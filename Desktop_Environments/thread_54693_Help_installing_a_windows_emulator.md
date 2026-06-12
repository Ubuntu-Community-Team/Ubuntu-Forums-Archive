---
title: "Help installing a windows emulator"
date: 2005-08-05
forum: Desktop Environments
---

### Post by rippon on 2005-08-05
I was wondering what windows emulator is best. I have heard of wine and qemu. 
Can anyone help me install either on kubuntu?
Thanks!

---

### Post by rippon on 2005-08-05
BTW, the goal is to run Microsoft Office Professional 2003 under kububtu using a windows emulation software. I have the install disk so it whoudlnt be a problem.

---

### Post by Ptero-4 on 2005-08-05
[QUOTE=rippon]I was wondering what windows emulator is best. I have heard of wine and qemu. 
Can anyone help me install either on kubuntu?
Thanks![/QUOTE]
 both are in the universe/multiverse repositories. You need to enable them, there's a wiki here at ubuntu on how to enable those repositories. Qemu is easier to install both you need the installation CDs for whatever OS you plan to use under Qemu. Wine run windows straight away and don't require a Windows install CD but it's trickier to install.

---

### Post by rippon on 2005-08-05
im confused

---

### Post by drizek on 2005-08-05
[QUOTE=rippon]im confused[/QUOTE]
 you cant run it under wine. you can either use office xp/2k in wine or run  2003 in an emulated windows xp with something like vmware.

---

### Post by Digitallysick on 2005-08-06
you could try win4lin pro, but be ready to have a pentium 4 computer, with lots of ram and a good graphics card, i tried it on my 900 mhz pentium 3 hahaha lets just say when it says minimum requirements 1.4 ghz or better, they mean it

---

### Post by varunus on 2005-08-06
Wine and Qemu do two different things.  Wine tries to get windows programs to run without having windows; they try to translate windows API calls into Linux ones.  Qemu tries to install windows inside of linux and run it natively on the processor.

Wine will be faster, and not require as much memory, but Qemu will have more compatibility.

For your purpose, you either need Crossover Office (wine derivative, costs money) or Qemu.  Here's a Qemu guide:
[http://www.ubuntuforums.org/showthread.php?t=39513](http://www.ubuntuforums.org/showthread.php?t=39513)

---

### Post by jeremy on 2005-08-06
There is a screensaver called BSOD ;-)

---

### Post by Mishura on 2005-08-06
MS Office 2003 is stated ***not to work*** in Codeweavers Crossover Office wine (The "supported" version of wine.)  So, the only route is probably qEmu.. meaning that you'll need a Windows install disc and some harddrive space.

Try this:
[http://www.ubuntuforums.org/showthread.php?t=39513&highlight=qemu](http://www.ubuntuforums.org/showthread.php?t=39513&highlight=qemu)

Disclaimer:  I cannot vouch for this, as I have not tried it.

---

