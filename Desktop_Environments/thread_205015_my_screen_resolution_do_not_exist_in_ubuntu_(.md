---
title: "my screen resolution do not exist in ubuntu :("
date: 2006-06-27
forum: Desktop Environments
---

### Post by soulwalker on 2006-06-27
i just installed ubuntu 6.06 but it only runs in 1024 * 768 :( I have a 32" lcd tv samsung monitor widescrren edition. In win xp i have the right resulotion which is 1360 * 768. But i can't choose that anyway in ubuntu and I have tried to search for a solution in the forums but can't find anything. Can u help me? I am using a nvidia card (7800 GT) if that helps u.

---

### Post by BigGrown on 2006-06-27
Reboot your system..............

---

### Post by jgcamp99 on 2006-06-27
I'm thinking:

System
Preferences
Screen Resolution

If there is a drop down to choose and select. Are you running Ubuntu video drivers  or the nvdia 3rd party drivers ?

I believe I may have had this same issue with an ATi Radeon 9600 XT & IBM G97 19 inch CRT, until I installed ATi's drivers.

---

### Post by dtfinch on 2006-06-27
I've always had to edit /etc/X11/xorg.conf to add resolutions. Otherwise, all I get are 4:3 ratio resolutions up to 1280x1024. My monitor supports up to 1920x1440.

---

### Post by soulwalker on 2006-06-27
[QUOTE=dtfinch]I've always had to edit /etc/X11/xorg.conf to add resolutions. Otherwise, all I get are 4:3 ratio resolutions up to 1280x1024. My monitor supports up to 1920x1440.[/QUOTE]
Sounds like something i'll try later. I just had to format the ubuntu installation though. i think it was because of grub and that ubuntu was on the secondary slave. Suddenly grub just restart everytime without me having time to press anything. So i had to fixboot and fixmbr with repair console on xp cd but that also deletes grub :( but i'll install it again later and then i'll try. 

#2 did that more times that once ;)

#3 i install nvidia drivers throught automatix and was in that menu. it only goes up to 1024*768. 

#4 like i said yours sound interessting. i'll give it a try later.

---

### Post by tseliot on 2006-06-28
Try point 5 of the Problems Section of my guide:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION)

If that doesn't work try point 10

---

### Post by soulwalker on 2006-06-28
[QUOTE=tseliot]Try point 5 of the Problems Section of my guide:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION)

If that doesn't work try point 10[/QUOTE]
point 10 sounds like the way to go like #4 says. i tried point 5 when i searched the forums before this thread and tried that command but the resolution i need is not a standard one. Not even out here in console to choose from. So if something works i should be point 10. Nice to send an examble so I'm not totally last when i try it ;)

---

