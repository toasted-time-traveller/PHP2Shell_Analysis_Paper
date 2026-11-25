# 🛡️ PHP2Shell
### Investigating Memory-Safety Failures and Remote Code Execution in PHP

<p align="center">
  <img src="https://img.shields.io/badge/Research-Cybersecurity-8A2BE2?style=for-the-badge" />
  <img src="https://img.shields.io/badge/Focus-PHP%20Internals-777BB4?style=for-the-badge" />
  <img src="https://img.shields.io/badge/Type-Technical%20Case%20Study-007ACC?style=for-the-badge" />
  <img src="https://img.shields.io/badge/Status-Research%20Project-orange?style=for-the-badge" />
</p>

---

## 🔍 About this project

What happens when something goes wrong inside the PHP runtime itself?

This project explores **PHP2Shell**, a pair of critical vulnerabilities affecting PHP that demonstrate how failures in memory management and exceptional control flow can potentially lead to remote code execution.

The research focuses on two vulnerabilities:

- **CVE-2026-109618** — An out-of-memory handling flaw involving exceptional control flow and partially initialised request state.
- **CVE-2026-109619** — A memory-lifetime issue involving stale worker-persistent state and references to freed request-owned memory.

Together, these vulnerabilities provide a fascinating case study in how seemingly separate implementation details can combine to undermine the security assumptions of a widely deployed runtime.

This repository contains a master's-level cybersecurity research paper examining the vulnerabilities, their underlying mechanisms, their potential impact, and the wider security implications.

**The aim isn't simply to document two vulnerabilities. It's to understand why they exist, how they can be exploited, and what they teach us about secure software design.**

---

## 🎯 Research objectives

The research investigates several key questions:

- How do the vulnerabilities arise within PHP's internal architecture?
- How can exceptional control flow leave request state partially initialised?
- What happens when memory allocated for one request is accessed after its lifetime has ended?
- How can worker persistence influence the security implications of memory-lifetime errors?
- What conditions affect exploitability across different PHP deployment architectures?
- How effective are the available patches and mitigations?
- What can these vulnerabilities teach us about memory safety, runtime security and secure software development?

---

## 🧠 What does the research cover?

| Area | Focus |
|---|---|
| 🔬 Root cause analysis | Internal PHP implementation flaws and their underlying causes |
| 🧩 Memory safety | Object lifetimes, dangling references and use-after-free conditions |
| ⚠️ Exception handling | Out-of-memory conditions and incomplete request initialisation |
| 🏗️ Runtime architecture | PHP workers, request lifecycles and persistent process state |
| 💥 Exploitability | Conditions, attack surfaces and potential remote code execution |
| 🛠️ Remediation | Upstream patches, fixed versions and defensive measures |
| 🔎 Detection | Indicators, monitoring opportunities and incident response |
| 📚 Secure development | Broader lessons for runtime and application security |

---

## 🧪 Research methodology

The paper uses a qualitative, documentary case-study approach, drawing on:

- Official PHP security advisories and release information.
- Vulnerability disclosures and technical analysis.
- Independent security research and reproduction reports.
- Government and national cybersecurity advisories.
- Established vulnerability classification frameworks.
- Secure software development guidance.

Evidence is assessed critically, with distinctions made between confirmed findings, reported observations, technical interpretation and proposed validation.

Where testing or reproduction has not been independently performed as part of this research, it is identified as such rather than presented as an experimental result.

---

## 📂 Repository contents

The repository is organised around the research paper and its supporting material.

```text
PHP2Shell-Research/
│
├── README.md
├── PHP2Shell_Masters_Cybersecurity_Paper_REVISED.docx
└── LICENSE
```

Additional supporting material may be added as the project develops.

---

## 📖 Inside the paper

The research examines:

1. **Introduction and background** — PHP architecture, security context and vulnerability discovery.
2. **Technical analysis** — Root causes, memory management and exceptional control flow.
3. **Threat model and exploitability** — Attack conditions, deployment considerations and potential impact.
4. **Patch analysis** — Remediation, fixed versions and effectiveness.
5. **Detection and incident response** — Defensive monitoring, containment and recovery.
6. **Critical discussion** — Broader implications for memory safety and secure software engineering.
7. **Conclusion** — Findings, limitations and recommendations.

### 📎 Supporting appendices

The paper also includes supporting material intended to make the research more useful beyond the immediate case study:

- **Appendix A:** Comparative vulnerability analysis.
- **Appendix B:** Evidence classification and assessment.
- **Appendix C:** Proposed technical validation programme.
- **Appendix D:** Operational security and remediation checklist.

---

## ⚠️ Important vulnerability distinction

Although both vulnerabilities are associated with PHP2Shell, they represent distinct technical failure modes.

| Identifier | Primary issue |
|---|---|
| CVE-2026-109618 | Out-of-memory handling and exceptional control flow |
| CVE-2026-109619 | Memory lifetime and stale references to freed request-owned memory |
| CVE-2026-115560 | A separate vulnerability discussed in the wider security context |

These identifiers should not be treated as interchangeable or assumed to describe one identical exploitation mechanism.

---

## 🛡️ Security and remediation

The research discusses the importance of:

- Applying the appropriate upstream PHP security updates.
- Checking vendor-specific backports where applicable.
- Restarting persistent PHP workers following remediation.
- Reviewing the PHP SAPI and deployment architecture.
- Monitoring suspicious process behaviour and unexpected execution.
- Investigating potential compromise rather than relying solely on patch status.
- Rotating potentially exposed credentials and secrets where compromise cannot be ruled out.

**Patching is essential, but understanding the affected runtime and deployment environment is equally important.**

---

## 📚 Selected references

The research draws on primary and secondary sources, including:

- [PHP Official Security Advisories](https://www.php.net/security)
- [PHP Source Repository](https://github.com/php/php-src)
- [Canadian Centre for Cyber Security](https://www.cyber.gc.ca/)
- [NCSC Netherlands](https://github.com/NCSC-NL/php2shell)
- [Elastic Security Labs](https://www.elastic.co/security-labs/)
- [Datadog Security Labs](https://securitylabs.datadoghq.com/)
- [MITRE CWE-416: Use After Free](https://cwe.mitre.org/data/definitions/416.html)
- [FIRST CVSS v4.0](https://www.first.org/cvss/v4.0/specification-document)
- [NIST Secure Software Development Framework](https://csrc.nist.gov/pubs/sp/800/218/final)

Full references and source-specific citations are provided within the research paper.

---

## ⚖️ Scope and limitations

This is an academic cybersecurity research project. Its conclusions are based on the sources, evidence and technical analysis available within the stated research period.

The paper distinguishes between:

- Documented vulnerability behaviour.
- Findings reported by independent researchers.
- Technical interpretation of the available evidence.
- Proposed testing and validation that has not necessarily been performed.

The research does not claim that every PHP deployment is equally vulnerable or that every reported exploitation technique applies across all PHP SAPIs and configurations.

---

## 👨‍💻 Intended audience

This research is aimed at:

- Cybersecurity professionals and security analysts.
- Penetration testers and vulnerability researchers.
- PHP developers and software engineers.
- Students studying application and runtime security.
- Anyone interested in memory safety and the internals of modern software.

A reasonable understanding of programming, web application architecture and cybersecurity concepts will help when reading the technical sections.

---

## 💬 Final thoughts

PHP is used across a huge portion of the web, which makes vulnerabilities within its underlying runtime particularly interesting.

PHP2Shell is a useful reminder that security problems don't always originate in application code. Sometimes the assumptions made by the runtime itself are where things start to unravel.

Understanding those failures is just as important as understanding how to patch them.

**Thanks for taking an interest in the research.** 🛡️

---

<sub>Research project · PHP2Shell · CVE-2026-109618 · CVE-2026-109619</sub>

<sub>Evidence cut-off: 24 November 2026</sub>
