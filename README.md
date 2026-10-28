# Cognetix — Firewall Configuration & System Hardening

## Overview

This project was completed as part of my internship at **Cognetix Technology**. It focuses on improving the security of a Kali Linux system through firewall configuration, listening-port inspection, service review, system update assessment, and network testing.

## Objectives

- Review and verify UFW firewall settings.
- Identify listening ports and network services.
- Review running background services.
- Assess available system updates.
- Test network filtering behavior using Nmap.
- Document security findings and hardening recommendations.

## Tools Used

- **Kali Linux** — Testing environment
- **UFW** — Firewall management
- **Nmap** — Port scanning and firewall testing
- **ss** — Listening port inspection
- **systemctl** — Service management and review
- **APT** — Package management
- **Docker CLI** — Container status inspection

## Tasks Performed

1. Reviewed the UFW firewall status and rules.
2. Inspected listening TCP and UDP ports.
3. Reviewed running system services.
4. Checked Docker container status.
5. Reviewed the proposed system package upgrades.
6. Tested selected TCP ports using Nmap.
7. Documented observations, risk considerations, and recommendations.

## Key Findings

- UFW was active during the assessment.
- Explicit inbound deny rules were present for FTP port 21.
- SSH port 22 was reachable during the Nmap test.
- PostgreSQL was listening on localhost.
- KDE Connect was listening on TCP and UDP port 1716.
- No running Docker containers were listed by `docker ps`.
- Nmap reported ports 21, 80, and 443 as filtered in the tested scan.

These observations describe the outputs collected during testing. They do not independently prove that every filtering result was caused by UFW.

## Commands Used

### Check firewall status

```bash
sudo ufw status verbose
```

### Inspect listening ports

```bash
sudo ss -tulpen
```

### List running services

```bash
systemctl --type=service --state=running
```

### Check running Docker containers

```bash
docker ps
```

### Test selected ports

```bash
nmap -Pn -p 21,22,80,443 <AUTHORIZED_TARGET_IP>
```

Replace `<AUTHORIZED_TARGET_IP>` with the IP address of the system you are authorized to test.

## Security Recommendations

- Deny unnecessary incoming connections.
- Keep SSH protected and accessible only as required.
- Review services that are not needed.
- Keep software updated.
- Avoid exposing databases to untrusted networks.
- Verify firewall behavior with authorized testing.
- Maintain screenshots and logs as assessment evidence.

## Project Evidence

Add your screenshots to an `screenshots/` directory, for example:

- `screenshots/ufw-status.png`
- `screenshots/listening-ports.png`
- `screenshots/running-services.png`
- `screenshots/apt-upgrade.png`
- `screenshots/nmap-firewall-test.png`

Only include screenshots you have actually captured.

## Disclaimer

This project was performed for educational and defensive security purposes in a controlled environment. Scan only systems for which you have explicit authorization.

## Internship

**Organization:** Cognetix Technology  
**Project:** Firewall Configuration & System Hardening  
**Intern:** Odai Mohsen Wahib
