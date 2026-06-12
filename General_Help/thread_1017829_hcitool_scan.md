---
title: "hcitool scan"
date: 2008-12-21
forum: General Help
---

### Post by axelsvag on 2008-12-21
I try to install the wammu. To be able to complete the installation I neen the mac adress for the phone and try the hcitool scan. All I get is maybe 10-15 s of scanning and the get back to the prompt without any information. How do I get the mac adress when this tool do not working. The phone is perfectly paired with the computer as I can get the files from the phone to the computer.

---

### Post by dcstar on 2008-12-22
> **axelsvag said:**
> I try to install the wammu. To be able to complete the installation I neen the mac adress for the phone and try the hcitool scan. All I get is maybe 10-15 s of scanning and the get back to the prompt without any information. How do I get the mac adress when this tool do not working. The phone is perfectly paired with the computer as I can get the files from the phone to the computer.

If the device responds to a ping then do that and then use:

```
arp
```

---

### Post by axelsvag on 2008-12-22
Thank you for your advice. I tried the ```
arp
``` command and the answer I get is the macadress for the eth0 adress. But when I uninstall the gnome-phone-manager and the wammu application the ```
hcitool scan
``` command works again.

---

