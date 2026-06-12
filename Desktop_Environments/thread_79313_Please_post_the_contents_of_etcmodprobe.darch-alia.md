---
title: "Please post the contents of /etc/modprobe.d/arch-aliases"
date: 2005-10-20
forum: Desktop Environments
---

### Post by Psquared on 2005-10-20
accidentally deleted the file and modprobe calls for the contents.

Thanks.

OBTW, using Breezy with Intel Pro Wireless BG ipw2200 ver 1.0.6

---

### Post by Marcos.Rufino on 2005-10-20
That's mine


alias parport_lowlevel parport_pc

alias binfmt-0064 binfmt_aout
alias binfmt-332 iBCS

---

### Post by matthew on 2005-10-20
For comparison, here's mine:
```
alias parport_lowlevel parport_pc

alias binfmt-0064 binfmt_aout
alias binfmt-332 iBCS
```
Looks the same as the other poster's

---

### Post by Psquared on 2005-10-20
[QUOTE=Marcos.Rufino]That's mine


alias parport_lowlevel parport_pc

alias binfmt-0064 binfmt_aout
alias binfmt-332 iBCS[/QUOTE]

Thanks. Are you using wireless? Are you using the 686 kernel in Breezy? I am thinking that ipw2200 for my Intel Pro Wireless BG (or maybe the firmware) needs to be in there too??

---

