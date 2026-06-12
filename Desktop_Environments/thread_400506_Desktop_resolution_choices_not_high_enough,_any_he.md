---
title: "Desktop resolution choices not high enough, any help?"
date: 2007-04-03
forum: Desktop Environments
---

### Post by TheCleaner on 2007-04-03
I have an nvidia quadro FX 3500 and it seems to be running ok, however the maximum screen resolution I can change to is 1024x768 at 75hz in the Screen Resolution utility.

I have another computer running vista on the same KVM switch and the resolution on that box with the same monitor is 1280x1024.

The nvidia config settings show the correct graphics card and monitor model so I'm not sure where to go from here to see how to get the correct screen resolution.

---

### Post by pppetter on 2007-04-03
You could do it the manual way. First make a copy of the xorg.conf, so you have if you manage to do something wrong:
> sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
Then we'll open the file
> sudo gedit /etc/X11/xorg.conf
find SubSection "Display", and depth 24 (assuming that that's what you use), then just add "1280x1024" as the FIRST mode, before 1024x768 - this will make it the default resolution. Save the file and then hit CTRL+ALT+BACKSPACE, to restart the X-server (note, this will quit your open programs).

Done!


IF something goes wrong(which is highly unlikely) and you end up on command-line, use sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf to restore the file.

---

### Post by TheCleaner on 2007-04-04
Thank you, that worked perfectly...

---

### Post by SNYP40A1 on 2007-04-04
Thanks for the advice, but that trick did not work for me.  It just made my monitor go blank.  I had to shut off my PC and boot in restore mode to restore it.  Any other advice?  I have the same problem, I can only get 1024x768 even though I have a monitor capable of 1280x1024 as well as a video card capable of the same.  Although my video card is an Ati Radeon 9550.

---

### Post by TheCleaner on 2007-04-05
Hmm..what does your xorg.conf say?

---

### Post by aid on 2007-04-05
I have a:
01:00.0 VGA compatible controller: VIA Technologies, Inc. S3 Unichrome Pro VGA Adapter (rev 02)
and, with Feisty I can use only 800x600 and 640x480.
With Edgy, I had 1280x1024 and 1024x768 available.
I tried to change xorg.conf, as suggested, but had no effect.
Help?

---

### Post by pljwebb on 2007-04-05
I've been having the same problem and after trying to edit the xorg.conf manually and completely failing to make it work I've found that running the following command will run a setup that lets you choose what resolutions you want to use.

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by SNYP40A1 on 2007-04-10
> **pppetter said:**
> You could do it the manual way. First make a copy of the xorg.conf, so you have if you manage to do something wrong:

Then we'll open the file

find SubSection "Display", and depth 24 (assuming that that's what you use), then just add "1280x1024" as the FIRST mode, before 1024x768 - this will make it the default resolution. Save the file and then hit CTRL+ALT+BACKSPACE, to restart the X-server (note, this will quit your open programs).

Done!


IF something goes wrong(which is highly unlikely) and you end up on command-line, use sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf to restore the file.

Ok, it is not just as simple as changing Display to 1280x1024.  The reason my monitor went blank is because I had a generic monitor selected which did not have a mode supporting that resolution in the config file (even though my monitor supports that res).  Check the video card AND the monitor config and ensure that whatever you set in screen is supported by the rest of the config.

---

