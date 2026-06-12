---
title: "configure: error: Could not find OpenSSL and OpenSSL headers on your system"
date: 2005-12-22
forum: General Help
---

### Post by adroc on 2005-12-22
Hello Ubuntu crew, I am trying to install Nessus 3 on my Ubuntu box but am getting an error. I know I can get an older version of nessus with sudo adp-get install nessus but that is not what I want. I already have the nessus daemon installed but am getting the following error when I am trying to install the nessusClient-1.0
[B]
configure: error: Could not find OpenSSL and OpenSSL headers on your system[/B]

I already have OpenSSL installed so how do I tell the ./configure command where to look for it?

thanks in advance
adroc

---

### Post by Swab on 2005-12-22
maybe you need to apt-get libssl-dev ... just a guess.

---

### Post by adroc on 2005-12-22
You the man thanks!!!!!!

---

