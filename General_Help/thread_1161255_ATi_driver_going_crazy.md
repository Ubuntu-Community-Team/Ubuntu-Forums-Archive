---
title: "ATi driver going crazy?"
date: 2009-05-16
forum: General Help
---

### Post by Dinchamion on 2009-05-16
Hello,

I'm sorry if I'm posting in the wrong section, but I'm kinda clueless as where to ask this question.

I scrubbed my computer today, backed up data, formatted the hard drive and installed a fresh Jaunty. Everything went smooth, I set up wireless, upgrade everything, installed all the programs I needed, etc, then installed the proprietary ATI driver as I need it to use wine. And at this point my computer went crazy.

After the first reboot into the system with the new driver my screen was messed up, but that was to be expected. So I wanted to change resolution and refresh rate, only I couldn't and I still can't. I can do it with the Catalyst Control Center, but whenever I navigate to Preferences/Display, the computer kinda locks up. It's like when something cpu-heavy uses all resources and everything lags like hell. I can't even kill the applet, I have to log out and log back in to clear it.

I could live with this, though, since I could set my resolution and refresh rate via the Catalyst Control Center. But it affects everything! I can't use wine (even winecfg and regedit produces the same problem as above, except when it finishes loading it's usable, but it takes ages more than it should to get there) - I didn't even try installing WoW yet, which is painfully slow to begin with, I only attempted to install Splinter Cell... it's a disaster.

I checked my xorg.conf, disabled Compiz, no change. I'm totally lost about what should I do.

---

### Post by nolliecrooked on 2009-05-16
> **Dinchamion said:**
> Hello,

I'm sorry if I'm posting in the wrong section, but I'm kinda clueless as where to ask this question.

I scrubbed my computer today, backed up data, formatted the hard drive and installed a fresh Jaunty. Everything went smooth, I set up wireless, upgrade everything, installed all the programs I needed, etc, then installed the proprietary ATI driver as I need it to use wine. And at this point my computer went crazy.

After the first reboot into the system with the new driver my screen was messed up, but that was to be expected. So I wanted to change resolution and refresh rate, only I couldn't and I still can't. I can do it with the Catalyst Control Center, but whenever I navigate to Preferences/Display, the computer kinda locks up. It's like when something cpu-heavy uses all resources and everything lags like hell. I can't even kill the applet, I have to log out and log back in to clear it.

I could live with this, though, since I could set my resolution and refresh rate via the Catalyst Control Center. But it affects everything! I can't use wine (even winecfg and regedit produces the same problem as above, except when it finishes loading it's usable, but it takes ages more than it should to get there) - I didn't even try installing WoW yet, which is painfully slow to begin with, I only attempted to install Splinter Cell... it's a disaster.

I checked my xorg.conf, disabled Compiz, no change. I'm totally lost about what should I do.

whats your card?

---

### Post by Dinchamion on 2009-05-16
> **nolliecrooked said:**
> whats your card?

hd3850

---

### Post by nolliecrooked on 2009-05-16
uhuh, uhuh. ok, well ati is crap on linux. the resource thing sounds like almost deadly embrace...
buy a cheap nvidia card, believe me its worth it. I used to use ati, then switched to nvidia. the difference in quality/stability is hugeeeeeeee.

---

### Post by Legace on 2009-05-16
> **gocek said:**
> 
BTW: if you fail to boot up your Ubuntu, just reboot it, select "recovery mode" in boot-manager (GRUB) and then go for "root shell" option. 
After that just type:
```
sudo apt-get remove xorg-driver-fglrx
```

Now you will need to restore your original settings, so either restore any backed-up copy of file /etc/X11/xorg.conf or run something like:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

or another one (you will have to answer a few simple questions)
```
sudo dpkg-reconfigure xserver-xorg
```


then type
```
exit
```

and select "resume normal boot"

This should get you back to your Ubuntu desktop, but running on default drivers.

And this is how to install the drivers properly:
[http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide#Installing_the_restricted_drivers_manually](http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide#Installing_the_restricted_drivers_manually)

and do the "manual installation" STEP BY STEP.

---

### Post by Dinchamion on 2009-05-16
> **nolliecrooked said:**
> uhuh, uhuh. ok, well ati is crap on linux. the resource thing sounds like almost deadly embrace...
buy a cheap nvidia card, believe me its worth it. I used to use ati, then switched to nvidia. the difference in quality/stability is hugeeeeeeee.

Yeah, I know they're crap, but I'm stuck with it on my desktop. If I could buy an nVidia, I would, trust me. :)

Weird thing is, it did work just fine before... I used to use 8.04, upgrade to Jaunty, it was ok. Yeah, could've been better, but I'm waiting my laptop, which will have an nVidia card, so I don't want to spend on my desktop box any more if I can avoid it. Anyway, that's not the point. Point is that I did everything right (or I think I did - it worked before), so I don't know what happened.

What I'll try tomorrow, as a last chance, to install the driver by hand. But if anyone had this problem before and know a solution, it could really save me some time. ;)

---

### Post by Dinchamion on 2009-05-16
> **Legace said:**
> And this is how to install the drivers properly:
[http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide#Installing_the_restricted_drivers_manually](http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide#Installing_the_restricted_drivers_manually)

and do the "manual installation" STEP BY STEP.

Thanks, I'll do that tomorrow!

---

### Post by [S]Duke on 2009-05-16
I have the same problem with my HD2600.

Tho, for me, on first installation, drivers never work (default driver leads to a blank screen), so I have to go to recovery mode and set the Drivers to "vesa" so I can at least install fglrx.

It has worked to this point, but like you said, on 9.04, I get the weird screen flicker/everything freezes thing.

---

### Post by Dinchamion on 2009-05-17
> **Legace said:**
> And this is how to install the drivers properly:
[http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide#Installing_the_restricted_drivers_manually](http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide#Installing_the_restricted_drivers_manually)

and do the "manual installation" STEP BY STEP.

Works perfectly now, thanks for the help! :)

---

### Post by Legace on 2009-05-17
> **Dinchamion said:**
> Works perfectly now, thanks for the help! :)

Glad it worked out. Enjoy ;)

---

