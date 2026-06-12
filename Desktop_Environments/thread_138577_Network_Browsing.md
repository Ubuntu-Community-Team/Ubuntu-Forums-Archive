---
title: "Network Browsing"
date: 2006-03-02
forum: Desktop Environments
---

### Post by Stealth on 2006-03-02
Whenever I browse the network in Ubuntu, I get a dialog requesting a password from another Ubuntu box running Samba. This gets annoying as I'm only BROWSING the WORKGROUP. I understand if I want to access the PC, I'd have to type it in but it gets annoying having to type in the password everytime. Is there a way to set up Samba with relatively good security to be accessible to the computers in my network WITHOUT any passwords?

---

### Post by Ramses de Norre on 2006-03-02
[http://www.ubuntuguide.org/]("http://www.ubuntuguide.org/") There is a lot about samba, maybe your problem is there too.

---

### Post by knalle on 2006-03-02
something like **map to guest = bad user**; or something in your **/etc/samba/smb.conf**

---

### Post by Stealth on 2006-03-02
Yea, I suppose it would be in the smb.conf, but ubuntuguide (which the IRC guys say is out-dated) doesn't have what I'm looking for. I want read/write on shares, probably only allowing certain MAC or IP addresses...

---

