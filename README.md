# Minor Project 01 – Networking, Linux & Reconnaissance

## 📌 Project Overview

This project is a practical reconnaissance and networking assessment completed as part of the Unlox Academy Minor Project.

The project focuses on:

- Networking fundamentals
- Linux commands and network configuration
- Web technology identification
- Directory and file enumeration
- Passive subdomain enumeration
- DNS resolution and analysis
- Reconnaissance documentation

All security testing was performed only against authorized targets and a deliberately vulnerable lab environment.

---

## 🎯 Objectives

The main objectives of this project were:

1. Understand basic networking concepts using Kali Linux.
2. Identify network interfaces, IP addresses, routes, and DNS configuration.
3. Perform technology discovery using Wappalyzer and Netcraft.
4. Understand the use of Shodan for internet-facing infrastructure research.
5. Perform directory enumeration using Gobuster on an authorized lab target.
6. Perform passive subdomain enumeration using Subfinder.
7. Validate discovered subdomains using DNSx.
8. Document reconnaissance findings with commands, screenshots, and analysis.

---

## 🛠️ Tools & Technologies

| Tool | Purpose |
|------|---------|
| Kali Linux | Security testing and reconnaissance environment |
| Wappalyzer | Web technology identification |
| Netcraft | Website infrastructure and technology information |
| Shodan | Internet-facing infrastructure research |
| Gobuster | Directory and file enumeration |
| Subfinder | Passive subdomain enumeration |
| DNSx | DNS resolution and validation |
| VirtualBox | Authorized lab environment |

---

## 🌐 Q1 – Networking & Linux

The networking configuration was analyzed using Kali Linux.

### Commands Used

```bash
ip addr
```

Used to identify network interfaces and IP addresses.

```bash
ip route
```

Used to identify the default gateway and routing information.

```bash
ping 10.0.2.2
```

Used to verify connectivity with the default gateway.

```bash
cat /etc/resolv.conf
```

Used to identify configured DNS servers.

### Network Information

- Interface IP: `10.0.2.15/24`
- Default Gateway: `10.0.2.2`
- DNS Server: `8.8.8.8`
- Additional DNS Server: `8.8.4.4`

The gateway connectivity test was successful with no packet loss.

---

## 🔎 Q2 – Web Technology & Infrastructure Reconnaissance

### Wappalyzer

Wappalyzer was used against the authorized target `example.com`.

The analysis identified **Cloudflare** as a CDN.

Wappalyzer is useful for identifying technologies and infrastructure components used by a website during authorized reconnaissance.

### Netcraft

Netcraft was used to examine `example.com`.

The observed information included:

- Hosting company: Cloudflare, Inc.
- Hosting country: United States
- IPv4 address: `172.66.147.243`
- Nameserver: Cloudflare
- Site technology: Cloudflare
- Gzip compression
- HTML5

Netcraft helps provide information about hosting, DNS, and website technology.

### Shodan

Shodan was investigated for `example.com`.

A target-specific Shodan result could not be verified without authentication, so no unverified Shodan result was included as a project finding.

---

## 🗂️ Q3 – Gobuster Directory Enumeration

An authorized deliberately vulnerable lab target was used for directory enumeration.

### Target

```text
http://172.28.128.3/
```

### Command

```bash
gobuster dir -u http://172.28.128.3/ -w /usr/share/wordlists/dirb/common.txt
```

### Interesting Results

| Path | HTTP Status | Observation |
|------|-------------|-------------|
| `/chat/` | 301 | Redirected directory |
| `/drupal/` | 301 | Drupal-related directory |
| `/phpmyadmin/` | 301 | phpMyAdmin-related directory |
| `/uploads/` | 301 | Upload-related directory |
| `.htpasswd` | 403 | Restricted resource |
| `.htaccess` | 403 | Restricted resource |
| `/cgi-bin/` | 403 | Restricted resource |

These results help understand the structure and accessible/restricted resources of the authorized lab web application.

---

## 🌍 Q4 – Subfinder & DNSx

Passive subdomain enumeration was performed against the authorized domain:

```text
example.com
```

### Subfinder

```bash
subfinder -d example.com -silent
```

Subfinder was used to collect subdomains using passive sources.

### DNSx

The discovered results were validated using DNSx:

```bash
subfinder -d example.com -silent | dnsx -silent
```

The validated output included:

```text
www.example.com
```

DNSx helped distinguish DNS-resolvable results from entries that could not be resolved.

---

## 📊 Q5 – Reconnaissance Analysis

The reconnaissance process followed these phases:

### Phase 1 – Network & Connectivity

Network interfaces, IP configuration, routing, DNS configuration, and gateway connectivity were examined.

### Phase 2 – Technology Discovery

Wappalyzer and Netcraft were used to identify web technologies and infrastructure information.

### Phase 3 – Web Enumeration

Gobuster was used against the authorized vulnerable lab target to identify directories and restricted resources.

### Phase 4 – Subdomain & DNS Analysis

Subfinder was used for passive subdomain enumeration and DNSx was used to validate DNS resolution.

### Phase 5 – Analysis

The collected information was organized and documented to understand the target's network and web infrastructure.

---

## 🔐 Authorization & Safety

All reconnaissance activities in this project were performed only against:

- Authorized targets
- `example.com` for permitted passive analysis
- A deliberately vulnerable local laboratory environment

No unauthorized exploitation or destructive activity was performed.

---

## 📄 Project Report

The complete assessment report, including commands, screenshots, findings, and analysis, is available in:

**`Minor_Project_01_Reconnaissance_Report.pdf`**

---

## 👨‍💻 Student

**Pratik Raviraj Deore**

**Sapkal Knowledge Hub, Nashik**

**Minor Project 01 – Networking, Linux & Reconnaissance**

---

## 📚 Key Learning Outcomes

Through this project, I learned:

- Basic Linux networking commands
- IP addressing and routing
- DNS configuration
- Web technology identification
- Passive reconnaissance
- Directory enumeration
- Subdomain enumeration
- DNS validation
- Security reconnaissance documentation
- Working with authorized cybersecurity lab environments
