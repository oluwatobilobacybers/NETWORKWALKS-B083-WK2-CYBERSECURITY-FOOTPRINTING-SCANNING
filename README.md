# NETWORKWALKS-B083-WK2-CYBERSECURITY-FOOTPRINTING-SCANNING

## Week 2 — Footprinting & Network Scanning

This repository documents my Week 2 cybersecurity internship work with **NetworkWalks**, covering authorized web footprinting/reconnaissance and local network discovery using Kali Linux and Zenmap/Nmap.

> **Ethical use:** All activities documented here were performed only against authorized training targets or my own lab/network. No exploitation was performed as part of this phase.

## Project Objectives

- Perform passive and low-impact web reconnaissance using multiple Kali Linux tools.
- Identify publicly observable domain, DNS, web-server, and technology information.
- Discover live hosts within an authorized local subnet using Zenmap/Nmap.
- Document findings, limitations, troubleshooting observations, and evidence professionally.
- Produce a final penetration-testing report covering the completed Week 2 modules.

## Lab Environment

| Component | Details |
|---|---|
| Operating System | Kali Linux 2026.2 |
| Web Reconnaissance Target | `networkwalks.com` — authorized NetworkWalks training target |
| Local Network | `172.20.10.0/28` |
| Network Scanner | Zenmap / Nmap |
| Reconnaissance Tools | WHOIS, WhatWeb, NSLookup, cURL, WAFW00F, DNSRecon |

## Modules Completed

| Module | Description | Status |
|---|---|---|
| W2-PM1 | Footprinting & Reconnaissance | ✅ Completed |
| W2-PM5 | Zenmap-Based Network Scanning | ✅ Completed |
| W2-PM-FINAL | Detailed Project Report | ✅ Completed |

## Activities Performed

### W2-PM1 — Footprinting & Reconnaissance

Six tools were used to collect different categories of publicly observable information from the authorized training target:

1. `whois` — domain registration information.
2. `whatweb` — web technology fingerprinting.
3. `nslookup` — DNS name-to-IP resolution.
4. `curl -I` — HTTP response-header review.
5. `wafw00f` — Web Application Firewall detection.
6. `dnsrecon` — DNS record enumeration.

### W2-PM5 — Zenmap-Based Network Scanning

A host-discovery scan was performed against the authorized subnet `172.20.10.0/28`.

```bash
nmap -sn 172.20.10.0/28
```

The scan covered **16 IP addresses** and identified **2 live hosts**:

| IP Address | MAC Address | Observation |
|---|---|---|
| `172.20.10.1` | `66:6D:2F:DC:B6:64` | MAC vendor not identified by Nmap |
| `172.20.10.3` | Not displayed | Host was reported as up; MAC was not shown in the captured output |

The unknown MAC vendor is not, by itself, evidence of a security issue. No MAC address was inferred or invented for `172.20.10.3`.

## Key Findings Summary

- Domain registration information and name-server details were obtained from WHOIS.
- WhatWeb identified Apache, WordPress, WordPress Download Manager, jQuery, Bootstrap, Google Tag Manager, and other web technologies.
- DNS resolution mapped `networkwalks.com` to `192.232.216.135` at the time of testing.
- HTTP response headers exposed several implementation-related headers and WordPress API references; session cookie values were intentionally excluded from public documentation.
- WAFW00F identified ModSecurity (SpiderLabs) protecting the target.
- DNSRecon identified SOA, NS, A, MX, TXT, and SRV records and reported an unsigned DNSSEC configuration.
- Zenmap/Nmap discovered two live hosts in the authorized `172.20.10.0/28` network.

> **Important:** Technology/version discovery and exposed metadata are reconnaissance observations, not confirmed vulnerabilities. This Week 2 phase did not include exploitation or proof-of-concept attacks.

## Evidence Structure

```text
W2-PM1-Footprinting/
├── README.md
└── screenshots/
    ├── 01-WHOIS.png
    ├── 02-WhatWeb.png
    ├── 03-NSLookup.png
    ├── 04-Curl-Headers.png
    ├── 05-WAFW00F.png
    └── 06-DNSRecon.png

W2-PM5-Zenmap-Scanning/
├── README.md
└── screenshots/
    ├── 01-Zenmap-Installation.png
    ├── w2-local-ip-address.png
    ├── W2-PM5-01-Host-Discovery.png
    └── w2-pm5-02-topology.png

W2-PM-FINAL/
└── W2-PM-FINAL-Oluwatobiloba-Banjo-NetworkWalks.docx
```

## Security & Privacy Notes

- Do not publish HTTP `Set-Cookie` values or other session tokens.
- Do not publish DNS verification tokens or other credentials/secrets.
- Do not treat a detected technology/version as proof of exploitable vulnerability without validation.
- Keep testing limited to systems and networks for which permission has been granted.

## Learning Outcomes

This project strengthened my practical understanding of:

- OSINT and web reconnaissance.
- DNS and domain infrastructure enumeration.
- Web technology fingerprinting.
- HTTP response-header analysis.
- WAF identification.
- Host discovery and subnet scanning.
- Evidence collection and technical documentation.
- Responsible and ethical cybersecurity testing.

## Final Report

The complete W2-PM-FINAL report is available in:

`W2-PM-FINAL/W2-PM-FINAL-Oluwatobiloba-Banjo-NetworkWalks.docx`

## Author

**Oluwatobiloba Banjo**  
Cybersecurity Analyst | Network Security Enthusiast

- GitHub: [@oluwatobilobacybers](https://github.com/oluwatobilobacybers)
- LinkedIn: [Oluwatobiloba Banjo](https://www.linkedin.com/in/oluwatobiloba-banjo-b2368819b/)

## Disclaimer

This repository is for educational, defensive, and portfolio purposes. The documented activities were performed within authorized training or personally controlled environments. Do not use these techniques against systems or networks without explicit permission.
