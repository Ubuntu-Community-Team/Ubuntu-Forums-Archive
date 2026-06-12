---
title: "System randomly TOTALLY crashes."
date: 2005-06-03
forum: Desktop Environments
---

### Post by simianMiscreant on 2005-06-03
Every so often my system just totally freezes - no mouse respose, no keyboard, the screen is frozen completely. I have to hold down the power button until it turns off. Output from /var/log/messages from when the system crashed yields nothing out of the ordinary.

I had my friend ssh in before and after it crashed, and the crash kills everything - no ping response, no ssh connection, nothing. My guess is an ATI/x.org problem at the driver level (but before i formatted i had no problems and hardware acceleration with fglrx!). Does anyone know what to do? I have a Radeon 9800 mobility with 256MB VRAM. Oh, and one more thing - I had to ship my system to Dell, and they replaced the vid card, mobo, and screen - but it's the same vid card as before, just a new one. Everything worked fine. Then i formatted my Ubuntu partition, and now I have the problem.

---

### Post by alastair on 2005-06-03
You could check whether it is an X driver issue (perhaps) by changing your X config file i.e.edit 

/etc/X11/xorg.conf

Change the driver to "ati" (or even "vesa")

Then restarting X (or CTRL+ALT+BACKSPACE) at the login screen/GDM.

If things stay more stable, it's an X driver issue.

---

### Post by simianMiscreant on 2005-06-03
ati is the driver I used before fglrx (also crashes) and vesa won't run any of my resolutions (it doesn't do 1920x1200, nor will it even do 1600x1200 for 4:3). This issue is really weirding me out, and I hope one among you has a fix - I loved Ubuntu so much before this happened and I hate having to boot Windows...please someone?

---

### Post by meteorain on 2005-06-04
I had a similar problem with my Radeon 9800 and I solved it by disabling AGP8x and AGP FastWrite. 

Try adding these lines in /etc/X11/xorg.conf  (just below Driver "fglrx"):
```

        Option          "AGPMask"  "0x00000218"
        Option          "AGPv3Mask"  "0x00000216"
        Option          "UseInternalAGPGART" "no"

```

Hope this helps.

---

### Post by simianMiscreant on 2005-06-04
Nope, sorry... :neutral: thanks for the effort, though.

---

### Post by simianMiscreant on 2005-06-05
*bump* this has completely immobilized my Linux experience...I haven't booted Ubuntu because this bug is so bad. It's affecting people all over the forum - I've seen three other topics on this crash. Someone please help us, or refer us to someone who can.

---

### Post by zAo on 2005-06-05
Do you use xcompmgr? My machine (Nvidia though) crashes randomly with xcompmgr enabled. Now I turned it off; everything goes fine.

---

### Post by railz68 on 2005-06-05
For the time being, I've given up trying to fix this problem. I don't think anyone really knows where the trouble lies. It seems it both ATI and nVidia cards, on different linux distro's as well.

Read a few posts in these links, and you'll find so many are having this problem.

[Trying to make headway into finding the Xid crashes source..](http://www.nvnews.net/vbulletin/showthread.php?t=49117) 

[""screen frozen, but mouse pointer moves" bug ](http://www.nvnews.net/vbulletin/showthread.php?t=31858) 

I really do hope you find a answer to your crashes. I've changed to "nv" driver and it doesn't freeze up. Soon as I try "nvidia" driver, system lockups all the time.
I've recompiled linux source, tried different drivers, nothing fixes it.
Before ubuntu, I was running Mandrake 9.2 for a long while, it never crashed. Now I'm "not" saying this issue is with ubuntu, but maybe linux 2.6 kernal (just guessing here).
good luck.

---

### Post by simianMiscreant on 2005-06-05
How do i disable xcompmgr?

---

### Post by Reb on 2005-06-05
apt-get remove xcompmgr. It doesn't "turn on" on it's own unless it is in your startup programs list.

---

### Post by simianMiscreant on 2005-06-05
Yeah it wasn't that.

---

### Post by simianMiscreant on 2005-06-06
My fix is here:
[http://ubuntuforums.org/showthread.php?p=201964](http://ubuntuforums.org/showthread.php?p=201964)

---

