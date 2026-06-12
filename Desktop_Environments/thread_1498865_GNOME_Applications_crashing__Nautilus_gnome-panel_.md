---
title: "GNOME Applications crashing / Nautilus gnome-panel won't start at login"
date: 2010-06-01
forum: Desktop Environments
---

### Post by Ubu843 on 2010-06-01
Hello,

Ubuntu 8.04 up-to-date

The problem started at login with the following message :

"Nautilus can't be used now due to an unexpected error from Bonobo when attempting to register the file manager view server"

and from GNOME Panel :

"The panel could not register with the bonobo-activation server (error code : 3) and will exit. ..."

GNOME applications are randomly crashing, the only informations I have is in dmesg :

$ dmesg | grep segfault
[  126.190963] gnome-panel[7106]: segfault at 00001c4f eip b6d37543 esp bff7d758 error 4
[  128.006153] gnome-power-man[7147]: segfault at 00001c4f eip b68f2543 esp bf93abc8 error 4
[  130.421010] gnome-panel[7157]: segfault at 00001c4f eip b6d42543 esp bf8ef1b8 error 4
[  130.633636] gnome-panel[7205]: segfault at 00001c4f eip b6c6c543 esp bfe824f8 error 4
[  130.937856] gnome-panel[7208]: segfault at 00001c4f eip b6d40543 esp bfcea6f8 error 4
[  131.073401] gnome-panel[7209]: segfault at 00001c4f eip b6cd4543 esp bf847a58 error 4
[  131.239003] gnome-panel[7210]: segfault at 00001c4f eip b6ce6543 esp bf96f408 error 4
[  131.376041] gnome-panel[7211]: segfault at 00001c4f eip b6cbe543 esp bfcbd208 error 4
[  131.513612] gnome-panel[7216]: segfault at 00001c4f eip b6c8d543 esp bf95dbd8 error 4
[  132.019058] gnome-panel[7217]: segfault at 00001c4f eip b6d32543 esp bfa7e018 error 4
[  132.198280] gnome-panel[7219]: segfault at 00001c4f eip b6cac543 esp bf9721f8 error 4
[  186.744618] update-notifier[7120]: segfault at 00001c4f eip b6b92543 esp bfd10378 error 4
[  318.035433] nm-applet[7137]: segfault at 00001c4f eip b6c57543 esp bff3ffa8 error 4
[ 5947.951942] nautilus[7107]: segfault at 00001c4f eip b6a29543 esp bfa18fe8 error 4
[ 5954.903820] nautilus[11994]: segfault at 00001c4f eip b6a03543 esp bfdfb4d8 error 4
[11761.174161] gedit[11669]: segfault at 00001c4f eip b6bcb543 esp bf9717c8 error 4
[11847.977428] gedit[11722]: segfault at 00001c4f eip b6b7d543 esp bfc14778 error 4
[11883.513361] gedit[11742]: segfault at 00001c4f eip b6bef543 esp bf83c968 error 4
[12262.168856] gedit[11993]: segfault at 00001c4f eip b6b74543 esp bfe49bd8 error 4
[18197.638515] nautilus[12012]: segfault at 00001c4f eip b6abf543 esp bfaa4ba8 error 4
[18262.695768] nautilus[15678]: segfault at 00001c4f eip b6ab0543 esp bfcf4358 error 4


Memtest86+ didn't report any error.

How can I track the problem ?

---

### Post by Ubu843 on 2010-06-17
Up !

---

### Post by bhavya_g_mihira on 2011-07-12
Hi,
how did u solve this problem?I'm facing a similar one.

Regards
Bhavya

---

