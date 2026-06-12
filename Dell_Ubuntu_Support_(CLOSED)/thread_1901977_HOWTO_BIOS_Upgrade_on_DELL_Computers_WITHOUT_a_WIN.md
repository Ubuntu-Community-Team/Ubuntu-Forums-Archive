---
title: "HOWTO: BIOS Upgrade on DELL Computers WITHOUT a WINDOWS Install"
date: 2011-12-29
forum: Dell Ubuntu Support (CLOSED)
---

### Post by frogotronic on 2011-12-29
Hello,

  Most DELL (or any other brand) of machines have BIOS updates/upgrades from time to time.  There have been several projects attempting to solve the issue that arises when attempting to upgrade the BIOS of a DELL computer with no MS Windows O/S on it.  However, most of them are defunct (not working anymore).  

  [COLOR="DarkSlateGray"]BTW:  You **[COLOR="Black"]CANNOT[/COLOR]** upgrade the BIOS from a VirtualBox or a VMWare install - Please [COLOR="Black"]**DO NOT**[/COLOR] try this - you need to be running an MS O/S or FreeDOS natively - *i.e.* on the bare metal.[/COLOR]

  Therefore, what is the solution?  Here's one that I came across that is very easy and straightforward and makes use of the native ***.exe** BIOS file from DELL.

  [COLOR="SlateGray"](This method will also work for any other brand of computer that provides it's BIOS files as ***.exe** format).[/COLOR]

[INDENT]1) Install [unetbootin]("http://unetbootin.sourceforge.net/") from Synaptic or CLI.[/INDENT]
[INDENT]2) Plug in a USB stick (it does not need to be erased, just to enough room for the FreeDOS and the bios (***.exe**) file).[/INDENT]
[INDENT]3) Create a FreeDOS bootable USB stick (on the USB stick you just plugged in).[/INDENT]
[INDENT]4) Download the latest and greatest **DELL_BIOS_MODEL.EXE** file for ***YOUR*** specific machine from the [DELL SUPPORT]("http://support.dell.com/") website from your Ubuntu install.[/INDENT]
[INDENT]5) Transfer the **DELL_BIOS_MODEL.EXE** file to your USB stick.[/INDENT]
[INDENT]6) REBOOT your computer and enter the BIOS options (F8 or F12 - usually).[/INDENT]
[INDENT]7) Select BOOT from USB *before* booting from anything else.  Hit <Enter>.[/INDENT]
[INDENT]8) Wait for the USB with the FreeDOS to boot.[/INDENT]
*****THIS NEXT STEP IS IMPORTANT*****
[INDENT]9) **[COLOR="Red"]DO NOT choose to _install_ the FreeDOS - this will erase your HDD and wipe-out your Ubuntu install[/COLOR]**.[/INDENT]
[INDENT][INDENT]   Also, do not choose any of the other special memory boot options.[/INDENT][/INDENT]
[INDENT][INDENT]   [COLOR="SeaGreen"]**Just choose boot FreeDOS with no extras**[/COLOR].[/INDENT][/INDENT]
*****Dangerous Step is Now Over*****
[INDENT]10) You will get a couple or warnings/errors - its okay to ignore them.  When presented with the **A:\** prompt, type **C:** and hit <Enter>.[/INDENT]
[INDENT]11) Type **dir** and you should get a list of all directories and files on your USB stick.[/INDENT]
[INDENT]12) Type **DELL_BIOS_MODEL.EXE** and hit <Enter> to execute the BIOS update/upgrade file.[/INDENT]
[INDENT]13) **DO NOT** touch the power (make sure your are plugged in with an A/C adapter if your are using a laptop); follow the on-screen instructions.[/INDENT]
[INDENT]14) If necessary after the update/upgrade, enter the BIOS (again, usually F8 or F12) and return the first boot device to what was before (usually the CDROM or HDD).[/INDENT]

Cheers,
CH

---

### Post by wgarider on 2012-01-01
Nicely done - I need to update the BIOS on my laptop and will give this a try!

---

### Post by critin on 2012-01-02
Dell support requires Internet Explorer.  What is the solution?

---

### Post by frogotronic on 2012-01-02
Hello,

  You have to manually navigate to the correct PC model.  You cannot use a windows-based "automagic" scan and auto-download option to find the correct files "For my PC" type programme. Just do it manually yourself in FireFox.

Start Here: [http://support.dell.com/support/topics/global.aspx/support/kcs/document?docid=427825#Issue3](http://support.dell.com/support/topics/global.aspx/support/kcs/document?docid=427825#Issue3) 

- CH

---

### Post by critin on 2012-01-08
Thanks!

---

### Post by Randymanme on 2012-01-19
> **cement_head said:**
> [INDENT]4) Download the latest and greatest **DELL_BIOS_MODEL.EXE** file for ***YOUR*** specific machine from the [DELL SUPPORT]("http://support.dell.com/") website from your Ubuntu install.[/INDENT]Just call me "Dumb."  I was having a whale of a time getting the bios update for my computer.  In retrospect, I can see that what was faking me out was the Dell site's advice to use IE.  I ended up using Firefox from Windows and flashing therein.  But it was your post that helped me to be able to do it. 

Thank you very much.

---

### Post by Randymanme on 2012-01-19
> **critin said:**
> Dell support requires Internet Explorer.  What is the solution?

Dell Support only requires Internet Explorer to scan your computer; but after you've done that (and that's assuming that you need for Dell support to scan your computer to get information that might be on the right hand side of the rear of your machine), you can download the bios update with Firefox and have Firefox put wherever you need it to be.

Cheers'

---

### Post by frogotronic on 2012-01-19
> **Randymanme said:**
> Just call me "Dumb."  I was having a whale of a time getting the bios update for my computer.  In retrospect, I can see that what was faking me out was the Dell site's advice to use IE.  I ended up using Firefox from Windows and flashing therein.  But it was your post that helped me to be able to do it. 

Thank you very much.

Awesome, yeah the "automagic" scan & download is a pain and only works in Windows systems.

Glad you solved the issue.

- CH  ;)

---

### Post by JC Cheloven on 2012-04-10
Unfortunately, after running the .exe I get (after saying that AC & battery is present etc):```
Memory error (2)
``` No instructions to follow or anything, it happens almost instantly.
Also, I see it creates another file, PHLASH16.EXE, with 0 bytes. To sum up, the process fails.

I'm on a dell mini9, with solid state disk.  

Not that I expect a fix for that (it would be welcome though ;) ). I'm simply posting for others to read.

Thanks for the tip anyway!
JC

---

### Post by mikewhatever on 2012-04-11
FreeDos didn't work for me, just got a message "this file can't be run" or something similar.

---

### Post by haqking on 2012-04-11
There are a few ways to do it

[https://wiki.ubuntu.com/DellBIOS](https://wiki.ubuntu.com/DellBIOS)

---

### Post by JC Cheloven on 2012-04-13
> **mikewhatever said:**
> FreeDos didn't work for me, just got a message "this file can't be run" or something similar.
Just a quick check: Have you tried the dos executable or tha windows one? There's both at dell's, only the 'dos' one is applicable here.

> **haqking said:**
> There are a few ways to do it

[https://wiki.ubuntu.com/DellBIOS](https://wiki.ubuntu.com/DellBIOS)
It seems I'm still out of luck: > The only BIOS recommended update for the Dell Mini 9 is version A01. There is no know mechanism for doing this update from Linux at this time. 
Thanks for the link anyway, perhaps I can work out some of the methods outlined there. I'll come back with my findings, if there is any at all useful ;)
JC

---

### Post by haqking on 2012-04-13
> **JC Cheloven said:**
> Just a quick check: Have you tried the dos executable or tha windows one? There's both at dell's, only the 'dos' one is applicable here.


It seems I'm still out of luck: 
Thanks for the link anyway, perhaps I can work out some of the methods outlined there. I'll come back with my findings, if there is any at all useful ;)
JC

here is someone using wine to do it with A01

[http://www.mydellmini.com/forum/ubuntu/246-bios-a01.html#post5298](http://www.mydellmini.com/forum/ubuntu/246-bios-a01.html#post5298)

And here is a launchpad discussion

[https://answers.launchpad.net/dell-mini/+question/60269](https://answers.launchpad.net/dell-mini/+question/60269)

---

### Post by rudy1094 on 2012-10-06
This was just what I needed to update my bios. Worked perfectly.

---

### Post by mikewhatever on 2012-10-06
> **JC Cheloven said:**
> Just a quick check: Have you tried the dos executable or tha windows one? There's both at dell's, only the 'dos' one is applicable here.


I've use the only one available, which mentioned nothing about being a DOS or Windows executable, same as the OP, by the way.

---

### Post by frogotronic on 2012-10-06
> **mikewhatever said:**
> I've use the only one available, which mentioned nothing about being a DOS or Windows executable, same as the OP, by the way.

Might try the post Hacking made - looks as though some of the newer machines are a bit tricky.

- CH

---

### Post by Lars Noodén on 2012-10-06
There's also a trick to boot FreeDOS from Grub without needing a floppy or USB stick.

[http://ubuntuforums.org/showpost.php?p=12167567&postcount=8](http://ubuntuforums.org/showpost.php?p=12167567&postcount=8)

---

### Post by blortuga on 2012-12-08
I've tried rufus, and the unetbootin FreeDos method.  

Both of these respond with "Program can not be run in DOS mode".  

This is with Bios A04 and A07 for a Dell Inspiron 7520 15 SE.

I think I need to boot to WinPE.

---

### Post by frogotronic on 2012-12-08
> **blortuga said:**
> I've tried rufus, and the unetbootin FreeDos method.  

Both of these respond with "Program can not be run in DOS mode".  

This is with Bios A04 and A07 for a Dell Inspiron 7520 15 SE.

I think I need to boot to WinPE.

I've run into this before.  Luckily, I was able to find a BIOS (for a supermicro) that wasn't WinPhlash.  Maybe try this: [https://wiki.ubuntu.com/DellBIOS](https://wiki.ubuntu.com/DellBIOS)

---

### Post by blortuga on 2012-12-19
I also tried WinPE.
Curse me for a fool, but I built a 64-bit WinPE image, and that didn't work. I'll get a chance later this week to try a 32-bit one.

I think I'll try the syslinux method - but if it's based on FreeDOS, I don't think its going to be any better than Rufus. . .

---

### Post by Andy Mackow on 2012-12-19
Hi, followed this and got to part 10, but when I searched A and B did not have my file with bios update WS380A09.EXE on it but if I look at the USB contents on windows its there, but not in the boot up at stage 10.  What am I doing wrong please. Andy

---

### Post by frogotronic on 2012-12-19
> **Andy Mackow said:**
> Hi, followed this and got to part 10, but when I searched A and B did not have my file with bios update WS380A09.EXE on it but if I look at the USB contents on windows its there, but not in the boot up at stage 10.  What am I doing wrong please. Andy


It's on C:

Type "C:\"

then "dir"

you should then see it.

---

### Post by blortuga on 2012-12-21
An x86 (32-bit) winpe boot *did* work, so I was able to successfully load the A07 bios.

The two features of this bios are supposed to be better (less overly aggressive) fan operation (I suppose that's going to depend on cpu scaling, and gpu driver/setup, as well), and better USB 3.0 performance.  I can't really comment on the latter - since I never benchmarked that. On the former: I don't notice much difference.

---

### Post by ksmigrod on 2013-02-01
I confirm that this solution works. Tested on Dell Vostro 3360, upgrade from A08 to A13.

Divergences from procedure:
- default unetbootin downloaded from sf does not work on amd64 system, I've built my own unetbootin from source.
- USB dongle with FreeDOS WON'T BOOT IN UEFI MODE, remember to switch to Legacy BIOS.
- I've run FreeDOS without HIMEM or other drivers, pendrive appeared as drive C:
- After executing 3360A13.exe computer works for over a minute, then reboots, re-flashes BIOS, and reboot once more.
- If you're using UEFI booting system, its a good opportunity to switch back to this mode.

---

### Post by mrainess on 2013-04-09
Using unetbootin with freedos to update a Dell Vostro to bios version 1.0.16 I got the message "Insufficient memory".
I found that if I boot freedos with himem, it works. The bios update utility ran without error and the bios was properly updated.
If I booted freedos with any other option or combination of options other than just himem, it did not work.

---

### Post by Hexxus on 2013-04-09
Thanks for the awesome sticky. This helped me a lot!

---

### Post by maxirodriguezsola on 2013-05-08
Hi friend,I need your help. I can do everything you post, but when the updating is starting it tells me that I need the battery charged. and i have no battery it is broken an I always use my laptop plugged in. how can I solve this problem???
thnaks!!

---

### Post by frogotronic on 2013-05-20
> **maxirodriguezsola said:**
> Hi friend,I need your help. I can do everything you post, but when the updating is starting it tells me that I need the battery charged. and i have no battery it is broken an I always use my laptop plugged in. how can I solve this problem???
thnaks!!

Can you borrow a battery?

---

