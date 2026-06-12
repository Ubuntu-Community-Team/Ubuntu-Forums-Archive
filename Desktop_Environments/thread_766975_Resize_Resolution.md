---
title: "Resize Resolution"
date: 2008-04-25
forum: Desktop Environments
---

### Post by GunBuntu on 2008-04-25
I've installed ubuntu 8.04 64bit. I have an nvidia 8800gt card and THANKFULLY, it was recognized and it looks like the drivers are working without me having to manually install the drivers from the nvidia site.

My problem is, the desktop is extending past the monitor edges about half an inch. I can't see the toolbars!! This did also happen on my windows xp pro install, but I was able to constrain it to the right size.

How can I do this in ubuntu??

---

### Post by procreative on 2008-05-02
Hi,

I have a similar issue with ubuntu 8.04 64bit and nvidia 8800gt.
I'm not able to change the refresh rate (60Hz). Then I installed 
the paket NVIDIA-GLX new 169.12+2.6.24.12-16.34. The result was much worse,
lower resolution. :( 
Then I was try to uninstall this packet, but unfortunatelly this was also not succesfull. I got an error message, that during unistallation of the paket an error occurs. 
.
Do some body experience with 8800 GT and 64bit Ubuntu 8.04?:confused:
Shall I use i386 coding? or the graphics card is to new?

Thanks a lot and best regards.

---

### Post by Zorael on 2008-05-02
Fresh install or upgrade?

Also, please post the terminal output of the following command.
```
$ grep -i virtual /etc/X11/xorg.conf
```

---

### Post by asphaltninja on 2008-08-17
I'm bumping this thread because I'm having the same problem. I just installed Ubuntu and I can't see my toolbars. The desktop extends past the edged of my monitor (which is an HDTV). Ihad this problem with windwos and was able to resize my desktop using the Nvidia Control Panel. How would I do this in Ubuntu?

---

### Post by jualin on 2008-08-17
Install the nvidia control panel for Linux, called nvidia-settings in Synaptic Package Manager or via terminal > sudo apt-get install nvidia-settings. Then open the nvidia settings using the terminal > sudo nvidia-settings Change your resolution and save to your Xorg file. Hope this helps!

---

### Post by jualin on 2008-08-17
This will only work if you are using the propietary Ndivia driver, which should be enabled using System, Administration, Hardware Drivers (in Hardy Heron),  or using Envyng-gtk in Synaptic Package Manager. Hope this helps!

---

### Post by asphaltninja on 2008-08-17
I installed the nvidia-settings panel, and it allows me to change the resolution, but this doesn't correct the problem. When I change the resolution I still cannot see the top or bottom toolbars. The option to "resize HDTV Desktop" that was in the nvidia control panel in windows was how I was able to resize the desktop so that the toolbars are visible. I appreciate your help, though.

---

### Post by jualin on 2008-08-17
I know that the Nvidia Control in Windows is not the same than the Ndivia Settings Utility in Linux but at least it lets you choose better resolutions sometimes. Can you try a higher resolution, maybe with a higher resolution the problem could be fixed.

---

### Post by asphaltninja on 2008-08-17
I tried higher resolution, but the effect is relative. It adjusts the resolution, but the toolbars still aren't visible.

---

### Post by jualin on 2008-08-18
Can you upload a picture to see what you are talking about better? ;)

---

### Post by MrMarc on 2008-08-18
I'm not sure if this might be similar to what I've experienced from time to time. Sometimes when I've installed Ubuntu (it's very strange in that it occasionally does this, other times it doesn't), it seems to think my monitors resolution is 1440x1000 (or there abouts) when it should be 1440x900. Strangely the monitor displays it but I have to push my mouse cursor at the screen edges to show the toolbars.

I can't really suggest a fix because it was quite a random problem that seemed to solve itself once adjusting the resolution myself, but you're not alone at least heh.

By the way, this was with a 7600GT.

---

### Post by keinea on 2008-08-18
I encountered a resolution//refresh issue when installing Hardy Heron 8.04 on some classroom PC's at work (Intel Corporation 82865G Motherboard, ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE] Video Card).

The initial install went okay, but the default resolution was too high for the type of LCD monitors being used.  So lowering the resolution to 1024x768 initially looked okay, and applications opened without any issues.   

It was after re-booting the system, that the Desktop resolution // refresh broke.  Opening any application would only display portions of the app when clicking the mouse on the Desktop (see attached screen-shot).

It turned out that the 'Visual Effects' setting had been reset from NONE (initial install configuration) too NORMAL.   Evidently Compiz does not support this particular ATI Video card well.   Once I changed the visual effects setting back to NONE, all worked okay. 
It only broke the one time, following the reboot after changing the initial settings.

As a test, I did go back and install Gutsy Gibbons 7.10, and this version had no isssues at all.  But I did discover that the X11 config seems to be handled differently between the two versions.   Gutsy's xorg.conf file had a more detailed definition of parameters,
whereas, Hardy's xorg.conf is a very trimmed down generic file.

Anyway, I now have the systems running Hardy Heron, with the visual effects set to NONE, and all is running okay.

Sincerely,
Keith
:cool:

---

### Post by paulvanleest on 2011-03-02
A late reply, but I was searching for the option a long time but it is there. So for those who want to find it, go to:

System (in the bar at the top you don see ;-))
Nvidia X server settings
DFP-1 (your-monitor) (usually cab be found _underneath_ "PowerMizer"
Slide the "Overscan Compensation" bar to the right

Voila! Problem solved

---

