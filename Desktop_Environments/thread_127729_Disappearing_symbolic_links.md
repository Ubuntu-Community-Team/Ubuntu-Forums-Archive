---
title: "Disappearing symbolic links"
date: 2006-02-09
forum: Desktop Environments
---

### Post by nrayever on 2006-02-09
hi everyone:

i manage to install and run 2 modems with chipset Intel537EP, one for each pc. but i got a problem and i don't know how to solve it. the problem is that i don't really know how to set a symlink or hardlink for the modem in /dev.

i used this documentation from wiki.ubuntu
[HTML]https://wiki.ubuntu.com/DialupModemHowto#head-068a426acfdc8518889ea095253c50b665bce5d4[/HTML]
to install the modem driver. i know that this documentaion is for Intel536EP, but making some deep thinking, i manage to install the driver. the driver for Intel537EP is avaliable here:

[HTML]http://downloadfinder.intel.com/scripts-df-external/Detail_Desc.aspx?agr=Y&ProductID=1230&DwnldID=9288&strOSs=39&OSFullName=Linux*&lang=eng[/HTML]
this driver is for suse, yes indeed. but work with ubuntu and the documentation from wiki.ubuntu.

when i was looking for the modem in /dev, i have found that a new device was created named as "Intel5370" ( so obvious!!). so i manage to make a connection with my isp but using System / Administration / Network tool to connect.

most of Xppp programs (Kppp, Gnome-ppp, etc.....) has on their devices list:

Example:

/dev/modem
/dev/tty
etc.... 

so i tried to make a symlink from /dev/Intel5370 to /dev/modem, so Xppp apps can use the Intel537EP modem as /dev/modem.

i used the command ```
sudo ln -s /dev/Intel5370 /dev/modem
```

and that worked pretty cool!, but when i rebooted the pc's the symlink was gone. my question is:

is there any way to make a symlink permanet?? or should i use a hardlink?? in any case, how should i do it?? i don't have a clue to do it, please any help would be appreciated!!!

sincerly nrayever

---

### Post by ddtmsa on 2006-02-09
I've been in contact with this person over on the Networking forum. 

Please be aware, they have been able to get their winmodem to work, so this is not a winmodem problem thread. Their problem is having to re-create the symbolic link after ever re-boot.

I do not know how to help with their symbolic link persistance problems, I suggested that they ask again over in this forum.

DDtMSA

---

### Post by cwaldbieser on 2006-02-09
[QUOTE=nrayever]hi everyone:

i manage to install and run 2 modems with chipset Intel537EP, one for each pc. but i got a problem and i don't know how to solve it. the problem is that i don't really know how to set a symlink or hardlink for the modem in /dev.

i used this documentation from wiki.ubuntu
[HTML]https://wiki.ubuntu.com/DialupModemHowto#head-068a426acfdc8518889ea095253c50b665bce5d4[/HTML]
to install the modem driver. i know that this documentaion is for Intel536EP, but making some deep thinking, i manage to install the driver. the driver for Intel537EP is avaliable here:

[HTML]http://downloadfinder.intel.com/scripts-df-external/Detail_Desc.aspx?agr=Y&ProductID=1230&DwnldID=9288&strOSs=39&OSFullName=Linux*&lang=eng[/HTML]
this driver is for suse, yes indeed. but work with ubuntu and the documentation from wiki.ubuntu.

when i was looking for the modem in /dev, i have found that a new device was created named as "Intel5370" ( so obvious!!). so i manage to make a connection with my isp but using System / Administration / Network tool to connect.

most of Xppp programs (Kppp, Gnome-ppp, etc.....) has on their devices list:

Example:

/dev/modem
/dev/tty
etc.... 

so i tried to make a symlink from /dev/Intel5370 to /dev/modem, so Xppp apps can use the Intel537EP modem as /dev/modem.

i used the command ```
sudo ln -s /dev/Intel5370 /dev/modem
```

and that worked pretty cool!, but when i rebooted the pc's the symlink was gone. my question is:

is there any way to make a symlink permanet?? or should i use a hardlink?? in any case, how should i do it?? i don't have a clue to do it, please any help would be appreciated!!!

sincerly nrayever[/QUOTE]

Well, the device you are linking is a "file", but not in the typical sense.  It is recreated each time the system boots, so the best thing to do would be to create a script that recreates the symlink at boot time.  i.e. put the link command in a script and use "update-rc.d" to add the command to the boot-up sequence.

---

