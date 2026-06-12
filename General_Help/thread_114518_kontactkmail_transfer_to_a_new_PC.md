---
title: "kontact/kmail transfer to a new PC"
date: 2006-01-08
forum: General Help
---

### Post by ger3d on 2006-01-08
Hi all
I just got a new laptop, installed kubuntu 5.10 upgraded kde to 3.5. How can I transfer all my mails contact from my old PC to the new one. The old one runs kubuntu with kde 3.5 beta.

Thanks gerhard

---

### Post by Divan Santana on 2006-01-09
[QUOTE=ger3d]Hi all
I just got a new laptop, installed kubuntu 5.10 upgraded kde to 3.5. How can I transfer all my mails contact from my old PC to the new one. The old one runs kubuntu with kde 3.5 beta.

Thanks gerhard[/QUOTE]
Install kmailcvt from universe respository.
Then open kmail, file => import messages => and select kmail mail dirs

Very simple.

---

### Post by Zerlinna on 2006-01-09
[QUOTE=ger3d]Hi all
I just got a new laptop, installed kubuntu 5.10 upgraded kde to 3.5. How can I transfer all my mails contact from my old PC to the new one. The old one runs kubuntu with kde 3.5 beta.
Thanks gerhard[/QUOTE]

If you want to keep all settings from your kde (including kmail) you could try that:

just replace the **/home/.kde/** on your new system with the one on your old system (copy and paste ;) ). 
If it's not working you can just remove /home/.kde/ - it will be recreated automatically. (But I think it should work - I even moved my .kde from a fedora system to kubuntu)

If you want to transfer only your emails and contacts from kmail just replace  
**/home/.kde/share/apps/kmail **on your new system with the old one, same for
**/home/.kde/share/apps/kabc/** (your addressbook)

Z.

---

