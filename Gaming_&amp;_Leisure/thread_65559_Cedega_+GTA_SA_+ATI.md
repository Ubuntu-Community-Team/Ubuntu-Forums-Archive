---
title: "Cedega +GTA SA +ATI"
date: 2005-09-14
forum: Gaming &amp; Leisure
---

### Post by krak on 2005-09-14
Hello am using Linux for 1 moth so i am noob
i am trying to run gta sa but i get this error 
mmtime pid=15587 tid=15596
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  146 (ATIFGLRXDRI)
  Minor opcode of failed request:  1 ()
  Value in failed request:  0x4200005
  Serial number of failed request:  342
  Current serial number in output stream:  342
I have searched transgaming.org forum with no result
i have tested Painkiller and it works but GTA no

if u can help do so :) i use Ubuntu 5.04 kernel 2.6.13.1 and Radeon 9600PRO

---

### Post by leezer3 on 2005-09-14
I expect its probably because GTA: SA is too new to be properly supported in Cedega yet. If it's not on thier official compatibility list, then don't even bother trying to run it, unless you're prepared to play with debugging etc. (Which I'm not :) )

-Leezer-

---

### Post by krak on 2005-09-14
the thing is that on debian i have made it to run "till the menu" but on ubuntu not yet.

---

### Post by leezer3 on 2005-09-17
[QUOTE=krak]the thing is that on debian i have made it to run "till the menu" but on ubuntu not yet.[/QUOTE]
 Ok, then- Did you configure your FGLRX via running fglrxconfig?
You should have set it to the Wine/ Emulator compatible profile, as opposed to the default. While this may loose you some FPS in glxgears, it could be causing the errors. Try and see......

Cheers

-Leezer-

---

### Post by xbaez on 2005-09-18
[QUOTE=leezer3]Ok, then- Did you configure your FGLRX via running fglrxconfig?
You should have set it to the Wine/ Emulator compatible profile, as opposed to the default. While this may loose you some FPS in glxgears, it could be causing the errors. Try and see......

Cheers

-Leezer-[/QUOTE]
 Hello

I made a new poll called:

Point2play And Cedega Problems Go Here - [http://www.ubuntuforums.org/showthread.php?t=66348](http://www.ubuntuforums.org/showthread.php?t=66348)

Please visit it as I'm trying to install GTA as well
I have the latest version 4.4.1-1 and I'm installing it without Point2Play, setup fails, some times (1 in a 5) it works, just try to launch the installer 10 times or so

---

### Post by Mr_Grieves on 2006-01-11
I tried to run GTA SA on Ubuntu with Nvidia and Wine. I came to the meny system.. but when starting a new game it all crashed to desktop.

I guess you should look at this GTA III Howto for Wine.
[http://www.linux-gamers.net/modules/wfsection/article.php?articleid=11](http://www.linux-gamers.net/modules/wfsection/article.php?articleid=11)

---

