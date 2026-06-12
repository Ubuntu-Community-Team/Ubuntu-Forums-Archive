---
title: "video card driver problem"
date: 2009-01-17
forum: General Help
---

### Post by spectre313 on 2009-01-17
Hi=)

I just installed ubuntu 8.10 (first time i ever tryed linux).

For my grapich card driver, i went to hardware support, then clicked to activate the recommended driver ubuntu found for me. Then i whas told to reboot (of course). I do so, but now when i log in i get a black screen with a gray box saying ''input not support''
Nvidia geforce 7600gs 256mb..

so my question, what to do?:S


My apologize for any bad english.

---

### Post by dcstar on 2009-01-17
> **spectre313 said:**
> Hi=)

I just installed ubuntu 8.10 (first time i ever tryed linux).

For my grapich card driver, i went to hardware support, then clicked to activate the recommended driver ubuntu found for me. Then i whas told to reboot (of course). I do so, but now when i log in i get a black screen with a gray box saying ''input not support''
Nvidia geforce 7600gs 256mb..

so my question, what to do?:S


My apologize for any bad english.

This is not that uncommon, do a forum search for nvidia drivers and you should get some posts that are useful to you.

I believe that you can also reboot into recovery mode and select the previous configuration to get back into your system.

---

### Post by Leo Dragonheart on 2009-01-17
Re: Nvidia Problem...I was having the same problem, I did what this guy said and it fixed my problem try it...


I've had the exact same problem with NVIDIA cards and the restricted driver. I searched for months to find an answer and I must tell you it was a painful runaround. The good news is I was able to fix it easily, simply by manually editing my xorg.conf file. In my case the problem was not with the NVIDIA driver at all. The problem was that my monitor was not correctly recognized by the X-server system. Once I identified my monitor specs in the xorg.conf file, everything worked perfectly. This is how I did it.

First you need to open your xorg.conf file in Gedit, like this:

Go to Main Menu and click on it, go up to Accessories, and then down to Terminal click on that and then enter the bold line below...

Code:

[B]sudo gedit /etc/X11/xorg.conf
[/B]
You'll have to enter your password to gain editing privileges.

Some say you should back up the file first, but I found gedit does this automaticaliy, and right now your original file isn't doing you much good anyway.

Next, you have to add a few lines to specific sections of your xorg.conf file. BUT DO NOT CHANGE ANYTHING ELSE!

In the Monitor section add the lines that appear in bold:
Code:

Section "Monitor"
    Identifier     "Configured Monitor"
   [B] HorizSync       31.0 - 65.0
    VertRefresh     51.0 - 90.0[/B]	
EndSection

Note that these are the specs that fit my particular monitor. They'll probably work for yours also - but if you want to you can replace the VertRefresh and HorizSync values with your monitor's actual data if you know what they are.

Next, in the Screen section add the lines that appear in bold, right before the EndSection line.

Code:

   [B] SubSection     "Display"
        Depth       24
        Modes      "1280x1024_60"
    EndSubSection[/B]

This set my monitor to my desired resolution which is 1280X1024. You can substitute the resolution data to suit your needs. Reboot your computer and you should have a high resolution display. Next, you should run the NVIDIA settings program to fine tune your system.

If this doesn't work, then you can boot in recovery mode and select the fix x-server option. This will give you a high resolution display but no special effects, etc.

I hope this helps.

---

### Post by spectre313 on 2009-01-18
Thanks, i wrote in what you posted in the xorg.conf file, but i couldent do it with any drivers installed.

I rebooted my computer, and i did get high resolution. Then i tried to install my grapich card driver and rebooted. After i log in, i get locked on the desctop for a couple of minutes, then i get an error ''The panel encountered a problem while loading. ''OAFIiD:GNOME_FastUserSwitchApplet''
And i get to choose if i want to delete it or not. 
Atleast im not stuck while having this error..

---

