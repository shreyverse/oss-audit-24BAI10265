# OSS Audit Report – Git

> An open-source software audit covering origin, licensing, Linux footprint, ecosystem analysis, and practical shell scripting.

---

## Table of Contents

1. [Introduction](#1-introduction)
2. [Part A – Origin and Philosophy](#2-part-a--origin-and-philosophy)
   - [Origin of Git](#21-origin-of-git)
   - [License Analysis](#22-license-analysis)
   - [Ethics of Open Source](#23-ethics-of-open-source)
3. [Part B – Linux Footprint](#3-part-b--linux-footprint)
4. [Part C – FOSS Ecosystem](#4-part-c--foss-ecosystem)
5. [Part D – Open Source vs Proprietary](#5-part-d--open-source-vs-proprietary)
6. [Shell Scripts Explanation](#6-shell-scripts-explanation)
7. [Conclusion](#7-conclusion)

---

## 1. Introduction

Open source software plays a major role in modern computing. Many systems, applications, and tools that we use daily are built using open-source technologies. This project focuses on analyzing an open-source software — **Git** — and understanding its origin, license, and real-world impact.

The project also includes practical implementation using Linux shell scripts to demonstrate understanding of open-source tools and system-level operations. Through this project, both theoretical and practical aspects of open-source software are explored.

---

## 2. Part A – Origin and Philosophy

### 2.1 Origin of Git

Git is a **distributed version control system** created by **Linus Torvalds in 2005**. It was built out of necessity — the Linux kernel development community had been using a proprietary tool called **BitKeeper**, but licensing issues led to its access being revoked.

To solve this, Torvalds designed Git from scratch with the following goals:

- ⚡ **Speed and efficiency**
- 📦 **Support for large projects**
- 🌐 **Fully distributed architecture** — every developer holds a complete copy of the repository

Git quickly gained popularity and today forms the backbone of platforms like **GitHub**.

---

### 2.2 License Analysis

Git is released under the **GNU General Public License (GPL)**, which ensures the software remains free and open for everyone.

The GPL provides **four essential freedoms**:

| # | Freedom |
|---|---------|
| 1 | Run the program for any purpose |
| 2 | Study how the program works |
| 3 | Modify the program |
| 4 | Distribute copies |

> **Key requirement:** Any modified version must also be released under the GPL, keeping improvements accessible to the community.

#### GPL vs MIT

| Aspect | GPL | MIT |
|--------|-----|-----|
| Source code sharing | Required for modifications | Not required |
| Permissiveness | Copyleft (strong protection) | Permissive |
| Open-source protection | Strong | Weaker |

Git follows the philosophy of **"free as in freedom"** — not just free of cost, but free to use, modify, and share.

---

### 2.3 Ethics of Open Source

Open source represents a philosophy of **sharing knowledge and collaboration**, enabling developers worldwide to contribute, improve, and innovate together.

**Arguments in favor:**
- Promotes transparency, security, and innovation
- Anyone can review, identify bugs, and improve the code
- Accelerates technological growth — "standing on the shoulders of giants"

**Challenges:**
- Not all software can be open source (especially revenue-dependent proprietary systems)
- Maintaining OSS projects requires significant time and effort, often without financial reward
- Ethical tension: companies profiting from open-source tools without contributing back

---

## 3. Part B – Linux Footprint

Git can be easily installed and managed on Linux using the **Advanced Package Tool (APT)**:

```bash
sudo apt install git
```

### File Locations and Directories

After installation, Git files are distributed across the Linux file system:

| Path | Purpose |
|------|---------|
| `/usr/bin/git` | Main executable file |
| `/etc` | System configuration files |
| `/var/log` | Log files |
| `/home` | User-specific configurations |

**Useful commands:**

```bash
which git          # Locate the executable path
dpkg -L git        # List all installed Git files
```

### User and Permissions

Git runs under the currently logged-in user. File ownership can be verified with:

```bash
ls -l /usr/bin/git
# Output: -rwxr-xr-x 1 root root 4066232 Jul 2 2025 /usr/bin/git
```

The executable is **owned by root** but executable by all users, ensuring controlled yet accessible system-level operation.

### Process and Execution

Git does **not** run as a background service — it is executed manually via terminal commands:

```bash
git init
git clone <url>
git status
```

This makes Git lightweight and efficient compared to always-running services.

### Update Mechanism

Git is updated through the system package manager:

```bash
sudo apt update && sudo apt upgrade
```

Updates including bug fixes and security patches are distributed through Ubuntu repositories.

---

## 4. Part C – FOSS Ecosystem

Git is not just a standalone tool — it is a **central part of a large open-source ecosystem**.

### Dependencies and Supporting Tools

Git relies on:
- Standard C libraries used by Linux systems
- File system support for storing repositories
- Terminal / command-line interface

### Platforms Built on Git

| Platform | Additional Features |
|----------|-------------------|
| **GitHub** | Cloud hosting, pull requests, Actions CI/CD |
| **GitLab** | Self-hostable, integrated DevOps |
| **Bitbucket** | Atlassian integration, team workflows |

### Role in Software Development

Git enables:
- Multiple developers to work simultaneously without conflicts
- **Branching and merging** for parallel development workflows
- Use across web dev, mobile, ML, and enterprise systems

### Community and Contribution

Git has a large and active open-source community. Contributors report bugs, suggest features, and submit code. The project is maintained by experienced developers and supported worldwide through forums, documentation, and discussion platforms.

---

## 5. Part D – Open Source vs Proprietary

### Comparison Table

| Feature | Git (Open Source) | Proprietary Systems |
|---------|:-----------------:|:-------------------:|
| Cost | Free | Paid / Subscription |
| Source Code Access | ✅ Fully accessible | ❌ Not accessible |
| Security Auditing | ✅ Anyone can audit | ⚠️ Limited transparency |
| Flexibility | ✅ Highly customizable | ⚠️ Limited customization |
| Support | Community-driven | Official company support |
| Control | Full user control | Controlled by company |

### Analysis

**Open Source (Git):**
- Complete freedom to view, modify, and distribute
- Promotes transparency and continuous improvement
- Encourages innovation through experimentation

**Proprietary Systems:**
- Dedicated, structured support
- Easier for enterprise environments with specific compliance needs
- Restrict source code access and customization

### Final Verdict

> Git is **recommended for real-world deployment** due to its reliability, flexibility, and strong community support. Proprietary tools remain viable where dedicated enterprise support is required.

---

## 6. Shell Scripts Explanation

Five shell scripts were developed as part of this project:

### Script 1: System Identity Report (`script1.sh`)

Displays basic system information including kernel version, current user, uptime, date, and Linux distribution.

**Commands used:** `uname`, `whoami`, `uptime`, `date`, `lsb_release`

**Concepts demonstrated:** Variables, command substitution

**Sample output:**
```
Name: Akshat
Software: Git
Kernel: 6.6.87.2-microsoft-standard-WSL2
User: hp
Uptime: up 3 minutes
Date: Thu Mar 26 15:10:39 UTC 2026
Distro: Ubuntu 24.04.4 LTS
```

---

### Script 2: FOSS Package Inspector (`script2.sh`)

Checks whether Git is installed and retrieves package details such as version and description.

**Commands used:** `dpkg`, `grep`

**Concepts demonstrated:** `if-else` conditionals, `case` statements, pattern matching

**Sample output:**
```
git is installed
Version: 1:2.43.0-1ubuntu7.3
Description: fast, scalable, distributed revision control system
```

---

### Script 3: Disk and Permission Auditor (`script3.sh`)

Analyzes key system directories and reports their size and permissions.

**Directories audited:** `/etc`, `/var/log`, `/home`, `/usr/bin`, `/tmp`

**Commands used:** `du`, `ls -ld`, `awk`, `cut`

**Concepts demonstrated:** Loops, condition checking, text processing

**Sample output:**
```
/etc     => Permissions: drwxr-xr-x root root | Size: 4.3M
/var/log => Permissions: drwxrwxr-x root syslog | Size: 37M
/home    => Permissions: drwxr-xr-x root root | Size: 56K
/usr/bin => Permissions: drwxr-xr-x root root | Size: 95M
/tmp     => Permissions: drwxrwxrwt root root | Size: 28K
```

---

### Script 4: Log File Analyzer (`script4.sh`)

Reads a log file and counts occurrences of a specified keyword (default: `error`). Displays the last 5 matching lines.

**Commands used:** `grep`, `tail`, `while` loop

**Concepts demonstrated:** File handling, loops, conditionals, command-line arguments

**Usage:**
```bash
./script4.sh /var/log/syslog error
```

---

### Script 5: Open Source Manifesto Generator (`script5.sh`)

Interactively asks the user questions about their views on open source, then generates and saves a personalized manifesto.

**Commands used:** `read`, file redirection (`>`, `>>`)

**Concepts demonstrated:** User input, string manipulation, file handling

**Sample output (saved to `manifesto_hp.txt`):**
```
On 26 March 2026, I declare my belief in open source.
I use Git and believe in freedom.
I will contribute by building AI tools and sharing it freely.
Knowledge should be open, accessible, and collaborative.
```

---

## 7. Conclusion

This project provided a comprehensive understanding of open-source software and its importance in modern computing. By analyzing **Git**, the following areas were explored:

- 🔍 **Origin** — How and why Git was created
- 📜 **Licensing** — GPL and its implications for freedom and sharing
- 🐧 **Linux Integration** — Installation, file structure, permissions, and updates
- 🌍 **Ecosystem** — Git's role as the foundation of modern software collaboration
- ⚖️ **OSS vs Proprietary** — A structured comparison highlighting Git's advantages

The practical shell scripting component reinforced core Linux skills including system inspection, file handling, loops, conditionals, and user interaction.

> Open-source tools like Git promote **collaboration, transparency, and innovation** — making them a cornerstone of modern software development.

---

*Project by: Akshat | System: Ubuntu 24.04.4 LTS | Date: March 2026*
