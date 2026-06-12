---
title: "Stumped on Dimension 2350 w/ 11.04 and Blank Additional Drivers"
date: 2011-06-19
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Scgn on 2011-06-19
I'm a veteran computer user but new to Ubuntu and a relative Linux newb.

I installed Ubuntu on a donated machine to set up a PoS for a local non-profit.  It doesn't need to do much, but it needs to have a display working at 1024x768, and I can't even get that far with it.

The computer has an Intel 845G video card, which as far as I can tell the system can't identify.  I tried to add resolution modes and change them manually as described in the wiki, but it fails with the error - Configure crtc 0 failed

I assume this is a driver related issue, but I got totally hung up here as well.  

I think the root of my problem comes from this fact I can't seem to solve at all - my Additional Drivers list in Ubuntu is TOTALLY blank, with no options to download or install any proprietary drivers.

After hitting that brick wall and following numerous threads I was able to get to a linux intel graphics website, but when I tried to download and compile the source code they provided it failed with even more errors and spitting out a list of additional software I needed to install.

I'll be honest that after many hours I'm rather frustrated and about ready to give up.  What's the easiest solution to what seems to me a straightforward problem that should be easy to solve?  Is there a driver I can at least download that will work that I don't have to compile myself?

Thanks for the help, guess maybe I'm just not hard core enough for this OS. :(

---

### Post by JRV on 2011-06-19
I will be back shortly, I need to look something up.

Sorry, I thought I had an answer, but I couldn't find it.

---

### Post by JRV on 2011-06-19
Try the vesa driver.
```

sudo gedit /etc/x11/xorg.conf

```

If the file is there add

```
Driver "vesa"
```

to the device section.

If the file is empty add this:

```

   Section "Device"
     Identifier    "Configured Video Device"
     Driver "vesa"
   EndSection

   Section "Monitor"
     Identifier    "Configured Monitor"
   EndSection

   Section "Screen"
     Identifier    "Default Screen"
     Monitor        "Configured Monitor"
     Device        "Configured Video Device"
   EndSection


```

I hope this helps, it's just a guess. But I have had luck getting some old video hardware working with the vesa driver.

---

### Post by Scgn on 2011-06-19
Thanks for the help, I've messed around with my xorg.conf file quite a bit today but sadly with little luck.

I first started with the settings you provided, but was not able to get the vesa driver to work. The boot would hang after the last step in my boot sequence (checking battery) and I've have to repair the file to boot back again.

I tried some other configurations that presented the same or similar problems.  I was finally able to get the computer to boot and recognise the monitor and change settings using "intel" as my driver type.  The bad news is that after about 30 min - 1 hr I get massive screen artifacts and have to reboot the system.

Might mess around with things a little more, but thinking this is a bit more trouble than it's worth.  Thanks for the help though!

---

