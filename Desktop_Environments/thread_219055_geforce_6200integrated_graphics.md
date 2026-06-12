---
title: "geforce 6200/integrated graphics"
date: 2006-07-19
forum: Desktop Environments
---

### Post by jmhickman09 on 2006-07-19
I have a pci 6200 and I don't think its working because I was looking at xorg.conf, and in the device section it says Intel Corporation 82865G Integrated Graphics Controller for the identifier part. It says the same thing for the device part of the screen section. Also, I was looking in the device manager thing, and I found the integrated graphics controller but it said it was using PCI. It also says that the 6200 is using PCI. Earlier I tried running Cube and I got a horrible framerate and it was way too choppy to play. I remember playing it on Windows back when I only had integrated graphics, and I got a decent framerate. I think there is some kind of problem because my monitor is plugged into the 6200, but then it says it's using the integrated graphics. How can I uninstall the integrated graphics and make it use the graphics card and its drivers? Sorry for the noobdom last time I had ubuntu installed all I had was integrated graphics.

---

### Post by Dr. Nick on 2006-07-19
It would be best if you could disable the integrated gfx in your bios, but if you cant then look at your xorg.conf file and check the busid line, modifying that line will chose which video card xorg uses. Since your monitor is pluged into the 6200 I would think it is being used though, Have you installed the 3d accelerated nvidia drivers yet?

---

### Post by jmhickman09 on 2006-07-19
In the BIOS, the only options are to automatically detect, or use only integrated graphics. So I guess you can't disable it from the BIOS.

By 3d accelerated nvidia drivers, do you mean this:[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper) 

Edit: I followed Method 1 from that site, but xorg.conf still looks the same. Aargh.

---

### Post by jmhickman09 on 2006-07-19
Bumpity.

---

### Post by hajk on 2006-07-19
> **jmhickman09 said:**
> In the BIOS, the only options are to automatically detect, or use only integrated graphics. So I guess you can't disable it from the BIOS.

By 3d accelerated nvidia drivers, do you mean this:[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper) 

Edit: I followed Method 1 from that site, but xorg.conf still looks the same. Aargh.

Well, have you tried the "automatically detect" BIOS option?

---

### Post by jmhickman09 on 2006-07-19
> **hajk said:**
> Well, have you tried the "automatically detect" BIOS option?
Yeah, that's what it's set to by default. What can I do other than from the BIOS? Should I post my xorg.conf thing?

---

### Post by jmhickman09 on 2006-07-19
bump

---

### Post by Dr. Nick on 2006-07-19
yes, I would post your xorg.conf up here, If the driver section doesnt say nv, nvidia I would think it is using your onboard.

Is your 6200 a pci, or pci-e? I didnt know they had a regular pci ver until just now.

The BusId section is what really matters, but if they are both on the same bus (pci) i dont know how you would defrentiate the 2 :confused:

---

### Post by jmhickman09 on 2006-07-19
I managed to get glx installed, and it said x needed to be restarted, so I just rebooted the computer, and now it says the x server is not starting. Is there a command I should use? I have no graphical interface. Also, the 6200 is pci. I've been told the model I have is kind of hard to find. Its BFG and I paid about 120 for it. So anyways, how can I fix this?

---

### Post by jmhickman09 on 2006-07-19
Here's what it says for the X server not starting:

[B](WW) NVIDIA:No matching Device Section for isntance (BusID PCI:1:2:0) found

(EE) No devices detected.

Fatal server error:

no screens found[/B]

I assume that I need to edit the xorg.conf, but I don't think I can because I can't open gedit.

---

### Post by goobers on 2006-07-19
type **sudo pico /etc/X11/xorg.conf** and change the display driver back to whatever it was, or 'vesa' if you can't remember it.  Write the file (CTRL+O) then exit. Then type **startx** to start X back up again.

Edit:: Actually, sorry, it sounds like it can't find the card now... it seems to be trying to look for the card on the wrong bus

Try this:

```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
sudo dpkg-reconfigure xserver-xorg

```

it will take you through a load of stuff- enter as much information as you know, if you don't know something, press enter.

when thats done, try typing **startx**

---

### Post by goobers on 2006-07-19
Thinking about it, what might be easier to try first is to edit the xorg.conf like i said before, changing the driver to vesa, but also putting a **#** in front of the "BUSID" line in the graphics card part, then trying to start x.

Sorry about keep changing my advice, i don't always think of the easiest way first :p

---

### Post by jmhickman09 on 2006-07-19
No prob dude lol. Thanks a lot for your help. The 3rd edit of the first post was what worked (the reconfiguration one). This solved all of my problems from the original post too. Is there like a way to rep on this forum? Thanks a lot.

---

### Post by goobers on 2006-07-19
No worries :D posting on this forum is the only thing that keeps me sane in the gap between the end of uni and the start of the next semester :p

most people are glad to be on summer break, but its really boring here- i don't have a car or any money :p

---

### Post by Dr. Nick on 2006-07-19
Glad you got it.

---

### Post by fragos on 2006-07-20
Autodetect should work.  It does for an AGP slot on my Gigabyte mother board. Perhaps if we knew what mother board and BIOS you have we could be of more help.

---

