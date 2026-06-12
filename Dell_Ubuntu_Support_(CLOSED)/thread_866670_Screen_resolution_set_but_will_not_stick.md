---
title: "Screen resolution set but will not stick"
date: 2008-07-22
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Szyfrow on 2008-07-22
Hi, Not sure if this is a Dell problem actually, but you have to start somewhere. Running Ubuntu 8.04/Gnome on an Optiplex GX270. No extra graphics card, I use on-board video. I'm having this problem with my screen resolution. After start-up I get an 800x600 screen resolution without the option to change it via System --> Preferences. So, I gather Ubuntu is using some kind of generic driver instead of a specific driver for my mobo. Strange thing is that after logging of and then logging on again under the same user name, everything is suddenly OK: then I can choose from resolutions between 800x600 and 1280x1024. After either a cold or warm reboot however, I'm back to 800x600 only.:confused: Does somebody have any ideas?

---

### Post by falcon61102 on 2008-07-22
Based on your system, I'm guessing you have the integrated intel graphics chip in your system.  While those drivers are included with the kernel, I don't think that yours are loading properly.  When you first login, run:
```
sudo lshw -C display
```
And post the results here.  

Then log off and then back on as you described and run that command again and see if there is a difference.  If there is, post that here as well.

---

### Post by Szyfrow on 2008-07-23
Thanks for thinking along, falcon61102. Strange enough however, when I fired up my computer today, I immediately got 1280x1024 resolution. :confused: No reboot, neither warm nor cold, would replicate the situation I described in my post. Only after kicking the power switch, thus preventing a graceful close down, returned to 800x600 again. Here are the results:
```

~$ sudo lshw -C display
*-display UNCLAIMED     
       description: VGA compatible controller 
       product: 82865G Integrated Graphics Controller 
       vendor: Intel Corporation 
       physical id: 2 
       bus info: pci@0000:00:02.0 
       version: 02 
       width: 32 bits 
       clock: 33MHz 
       capabilities: pm vga_controller bus_master cap_list 
       configuration: latency=0 

```

After logging of and on again I got 1280x1024. The lsw results were the same as above.

Until now, on every reboot I get 1280x1024. So it seems the problem has sort of solved itself. Quite strange! If the problem arises again I'll let you guys know. 

**Just one more question:** where can I check (and change if necessary) the display driver that my configuration uses?

---

### Post by falcon61102 on 2008-07-23
You can view/edit your drivers and display settings using:
```
sudo displayconfig-gtk
```

---

### Post by Kylibar on 2008-07-23
I've just resolved a similar issue with my Dell GX260;

hardware - Using my onboard video
driver - (xserver-xorg-driver-i810)
issue - stuck on 640x480 (minimum resolution, and it sucked) to furthur my frustraition, the unit/computer is actually just one node attached to 7 other identical GX260s, as to form a cluster.

The other nodes worked fine, so naturally i was worried it was an actual hardware issue, maybe physcally broken or something. Im glad that wasn't the case!

resolution - I just got curious and checked the BIOS congifuration. I had recently taken out a secondary video card that came with the unit, I don't know if that was what cause my problem (i think it was), but I dont care :)

so check these settings, they may help;

1.)im sure you know this but you never know right?, but press F2 during BIOS splash screen (booting)

2.)you should be in the bios - 

[INDENT]Integrated Devices (press enter)
[INDENT]Primary Video Controller (Onboard)[/INDENT]
[INDENT]Video DAC Snoop (OFF)[/INDENT]
[INDENT]Onboard Video Buffer (8MB)[/INDENT]
[/INDENT]


hope this helps :D

---

### Post by Szyfrow on 2008-07-23
Hi falcon61102, thank you! video chip reference is OK (i810), so I gather I have the right driver installed. While at it I also changed the screen model from plug'n play into LCD Panel 1280x1024 and the screen looks very nice now!:-D Let's hope it'll stick 8-[

I consider my problem solved.

Kylibar, Thanks. I checked my BIOS:
[LIST]
[*] Primary video controller: auto (but don't believe this will make a difference because I only have onbord graphics - so i'll leave it as is for now).
[*] BIOS doesn't present any Video DAC options. Any ideas?:confused:
[*] On board video buffer was set to 1MB I changed it into 8MB. Do you expect me to see any differences?
[/LIST]

---

### Post by falcon61102 on 2008-07-23
I wouldn't worry about the Video DAC, if you don't have it then it can't be on.  As far as the changing from 1MB to 8MB, you may notice a slight increase in performance with desktop settings in such but I wouldn't expect to see a huge performance increase.  That chip isn't made for games and graphic heavy apps, it's mainly for your average desktop workstation.

---

### Post by Szyfrow on 2008-07-24
Strange though, that you need 'hard core'linux cl in order to  configure your machine - or is there lshw functionality hidden somewhere in the desktop menu structure?:confused:

---

### Post by falcon61102 on 2008-07-24
> **Szyfrow said:**
> Strange though, that you need 'hard core'linux cl in order to  configure your machine - or is there lshw functionality hidden somewhere in the desktop menu structure?:confused:

Could you explain what you mean by that statement/question?

---

### Post by Szyfrow on 2008-07-24
What mean is that I find it strange that in order to configure my monitor I need to invoke a program via the command line. The second part of my statement/question was meant to raise the question (yes it is a question)whether the Ubuntu GUI offers functions like Windows does: device managment via the tab 'Hardware' of (right click)'My computer'.

---

### Post by falcon61102 on 2008-07-24
They have something similar, but it's more to view than to edit your settings.  If you go to Applications>Add/Remove... and run a search for Device Manager or System Information, but are good tools to view information about your hardware and system overall.  

And it's not uncommon to use the command line to configure things, most often because it's the easiest/shortest way of accomplishing what you need to do.  And since people often have different desktop settings and programs installed, it is an easy way for nearly everyone to be able to perform the steps necessary.

---

### Post by arepaking on 2009-01-05
> **Szyfrow said:**
> Thanks for thinking along, falcon61102. Strange enough however, when I fired up my computer today, I immediately got 1280x1024 resolution. :confused: No reboot, neither warm nor cold, would replicate the situation I described in my post. Only after kicking the power switch, thus preventing a graceful close down, returned to 800x600 again. Here are the results:
```

~$ sudo lshw -C display
*-display UNCLAIMED     
       description: VGA compatible controller 
       product: 82865G Integrated Graphics Controller 
       vendor: Intel Corporation 
       physical id: 2 
       bus info: pci@0000:00:02.0 
       version: 02 
       width: 32 bits 
       clock: 33MHz 
       capabilities: pm vga_controller bus_master cap_list 
       configuration: latency=0 

```

After logging of and on again I got 1280x1024. The lsw results were the same as above.

Until now, on every reboot I get 1280x1024. So it seems the problem has sort of solved itself. Quite strange! If the problem arises again I'll let you guys know. 

**Just one more question:** where can I check (and change if necessary) the display driver that my configuration uses?

Hi,
I am not sure if you already resolved your issue but I wanted to tell you that I ran the command above and I got the same results as you. Now, I'm running Ubuntu 8.10 without any issues on the video display. If you still have 8.04 I would recommend you to upgrade to 8.10 and I very confident that you will not have these issues anymore.

Hope it helps,
AK

---

### Post by Szyfrow on 2009-01-10
> **arepaking said:**
> Hi,
I am not sure if you already resolved your issue but I wanted to tell you that I ran the command above and I got the same results as you. Now, I'm running Ubuntu 8.10 without any issues on the video display. If you still have 8.04 I would recommend you to upgrade to 8.10 and I very confident that you will not have these issues anymore.

Hi arepaking,

Returned from a short holiday and saw your reply only now.
I'm still on 8.04, but screen res still OK. Will upgrade to 8.10 soon anyway. I will post the effect of that in this thread.
Thanks for your response. Are you also running a Dell maybe?

Szyfrow

---

