---
title: "Widescreen Notebook"
date: 2005-11-06
forum: Desktop Environments
---

### Post by LeeHambley on 2005-11-06
Hi,

While new to ubuntu, i'm fairly seasoned with linux, mainly oweing to using it for LAMP for my career...

</background>

I just invested in a lovely new notebook, with a 12.4" widescreen diplay - the problem is that gnome/xorg will only run it at 1024x768 - while it's `best` resolution is a sexy 1280x800.

Having googled just about everything i can think of, i've decided i need to edit the xorg config wo include the h and v sync ranges, the problem is i cant find the sync ranges either online, or in the manuals that came with my computer.

I dont want to go spamming the forum with yet more pleas for help, but is there any way to probe for the sync ranges without blowing a hole in my desk? 

I can ofcourse post my xorg config files if it would help you help me - the link below refers to the  manufacturers site for the notebook - it's a custom build machine - you buy the chassis from aopen, and fit the optical, disks, ram and cpu yourself.

[Link ]("http://solution.aopen.com.tw/products/nb/1551-AW1AG1.htm")

Thanks in advance

Lee

---

### Post by mlomker on 2005-11-06
You could try one of the online modeline generators.  [Referenced here.]("http://ubuntuforums.org/showthread.php?p=417734&posted=1#post417734")

---

### Post by LeeHambley on 2005-11-06
Awesome, thanks - 

# 1280x800 @ 70.00 Hz (GTF) hsync: 58.31 kHz; pclk: 98.89 MHz
  Modeline "1280x800_70.00"  98.89  1280 1352 1488 1696  800 801 804 833  -HSync +Vsync

is what it came up with, for clarity - which section of xorg.conf shoudl this be in, display, or one of the subsecst of screen?

---

### Post by LeeHambley on 2005-11-06
Hi,

Correctlky inserted in xorg.conf but it's still not an avalible option in the screen resolution dialog... still playing with it...

Did my modeline look OK ?

---

### Post by mlomker on 2005-11-06
You need a corresponding section with that resolution under "Screen."  Post your xorg.conf if you need to.

---

### Post by LeeHambley on 2005-11-06
Hi, 

Here's my xorg.conf file as it stands now, i re-did the modeline at 60hz jsut to check ti wasnt that...

Please find attached the xorg config file.

Thanks again

---

### Post by kverde on 2005-11-06
What kind of laptop do you have?  I got that resolution working using the **855resolution** program.  I would give you more details, but I'm not sure what exactly I did, but now it works.  Search for **855resolution** in this forum.  Also, apt-get install that package before you start.

---

### Post by mlomker on 2005-11-06
The xorg looks good to me.  Look in the /var/log/Xorg.0.log for errors.

---

### Post by LeeHambley on 2005-11-06
Like i mentionedin my first post, it's an A-Open BareBook - basically you buy the chassis, it's the logic board and screen
......and add you arr cpu ram disks, etc - it's usually sold to companies to brand them, then distrobute them

---

### Post by mlomker on 2005-11-06
[QUOTE=LeeHambley]Like i mentionedin my first post, it's an A-Open BareBook [/QUOTE]

Yes, but the specs don't mention what chipset your video adaptor is.  If you have one of the 845G/855GM/865G chips then that package may be what you need.

Try **lspci | grep VGA**

---

### Post by LeeHambley on 2005-11-06
Hi Fellas,

Just tried 855resolution, just got the following output:

```

lee@ubuntuhambo:~$ sudo 855resolution
Password:
855resolution version 0.4, by Alain Poirier

Chipset: 855GM (id=0x35808086)
VBIOS type: 1
VBIOS Version: 30

```

doesnt seem terribly helpful, but i'm probably misusing the program, need to google it some more, 

The Xorg.0.log doenst seem to contain anything great - it's mainly key bindings, and nothing hugely errornous looking.

Is this even an xOrg problem?

I'm almost at the stage that i go back to Xp as this is driving me nuts!

Continued thanks, lee

---

### Post by mlomker on 2005-11-06
**man 855resolution** should give you the options.  Plenty of [references]("http://www.bram.be/travelmate_4651lci.html") on Google.  Basically you'd just put the command at the end of your /etc/init.d/bootmisc.sh file once you figure out the right command line options.

---

### Post by LeeHambley on 2005-11-06
Hi,

Well thanks to both of you guys, basically to give you the lowdown on where i am with this now, i have my desktop running at 1280x800@60Hz - the 60Hz is from my modeline, which i can change - i just need to follow the last bit of the guide you referenced earlier to make the changes permanant on boot - 

And with that all done and dusted, it just remains to once again thank you both for helping me out before i gave in and followed Emporer Bill to the dark side.

Much regards, and to the Ubunto maintainers, much respect - easily the best windows replacement desktop for the new to Linux

(beats the hell out of Gentoo anyway)

---

