---
title: "novice wireless problems"
date: 2005-12-19
forum: Desktop Environments
---

### Post by jtmedin on 2005-12-19
Read most of the faq for wireless & have this comment & question.
Driver seems to be loaded & active but i am unable to connect to our dsl. Several things bother me: we use shared-key for our type of wireless do not see how to enable that. The driver is 'experimental' ... . Help TIA:(

---

### Post by Lambert on 2005-12-19
Is it the madwifi driver (ath_pci)


rest of informatin given will be based on the assumption of yes, it is madwifi.

```
sudo iwpriv ath0 authmode 2
```

This will change the driver setting so it's set up as shared key setting

When you reboot it will reset to open setting so add this line to your /etc/network/interfaces file under the correct interface

pre-up iwpriv authmode 2

---

### Post by jtmedin on 2005-12-21
Ok 'authmode 2' fixed it Thanks.

---

