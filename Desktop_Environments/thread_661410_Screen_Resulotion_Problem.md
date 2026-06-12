---
title: "Screen Resulotion Problem"
date: 2008-01-07
forum: Desktop Environments
---

### Post by Welskyy on 2008-01-07
I have an onboard VGA ATI Xpress 200 but my screen resulotion is only 800x600...Help me to change it to higher resolution

---

### Post by skyjacker on 2008-01-09
> **Welskyy said:**
> I have an onboard VGA ATI Xpress 200 but my screen resulotion is only 800x600...Help me to change it to higher resolution 
Try this:Back up the present xorg.conf
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf-backup
```

Stop gdm or kdm
```
sudo /etc/init.d/gdm stop
``` or kdm for kde

Edit xorg.conf
```
sudo dpkg-reconfigure xserver-xorg
```
Select the resolutions you want available by arrowing down to each desired line and pressing the &#8220;space bar&#8221;
Validate your choices with &#8220;enter&#8221;
restart X with Control+Alt+Backspace
	Choose the desired resolution under the &#8220;Systems/Preferences/Screen Resolutions drop down 	list

---

### Post by Welskyy on 2008-01-09
I tried this code
sudo dpkg-reconfigure xserver-xorg  , then i set the resolution to 1024x768. but when i restart the pc. when its start to load linuz system files the monitor has no display and the lead indicator of the monitor will just blinking..hope you can help me..thanks

---

### Post by Fleece Flamingo on 2008-01-09
This happened to me a while back and I had to completely reinstall ubuntu, Hopefully it's not the case for you but I'm just putting it out there so you don't get disappointed.
And also are you in recovery mode?

---

### Post by espo111 on 2008-01-09
the SAME exact thing happened to me today (i posted right before you)

tried all the common fixes nothing worked. I dont want to reinstall again, i just got it setup nice.

help!

---

### Post by Welskyy on 2008-01-09
I tried to reconfigure the xorg.conf. by using this code: sudo dpkg-reconfigure xserver-oxrg
i finished it and set the resolution to 1024x768, but wheh i press the Ctrl Alt Backspace the monitor has no display anymore and the lead indicator keeps on bliking...whats the problem of this...

---

