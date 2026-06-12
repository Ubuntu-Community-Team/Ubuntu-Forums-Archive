---
title: "On shutdown, Xubuntu shows a corrupted splash screen and then hangs"
date: 2012-09-06
forum: Desktop Environments
---

### Post by peyre on 2012-09-06
My HP Pavilion ze4540us just died, but luckily I have a very similar model to replace it with, a ze4125 (AMD vs. Intel processor, but otherwise nearly identical AFAIK).  So I transplanted the hard drive into the ze4125, and it runs great, with a couple of exceptions.

1. Power management doesn't really seem to work all that well--it doesn't suspend when I close the lid (even on battery!), even though I've told it to do so both on battery and on AC.  I understand power management is an issue in Linux though, so this is probably irrelevant.  I'm just mentioning it in case it helps to know this.

2. When I tell it to shut down--or reboot--it shows the Xubuntu shutdown screen, with the bar going back and forth under "Xubuntu", then hangs and never shuts down.  Also the image appears corrupted (see attached).  Once, instead of the shutdown screen, I saw a bunch of text scroll down mentioning errors.  IIRC they seemed to point to the graphics card, but unfortunately I can't recall the details and I haven't been able to reproduce it.

I am open to the possibility of rebuilding Xubuntu from scratch, but I'm posting this in the hope that someone knows a fix so I don't have to go through all the after-installation configuration.

---

### Post by Merrattic on 2012-09-06
What's the graphics card on it? Nvidia?

Regardless, try uninstalling / reinstalling graphics drivers, may have needed a slightly different configuration for the other PC, and plymouth is bugging out because of this.

Or try reconfiguring the drivers (you'll need to come out of X to do this for nvidia)

```
sudo apt-get purge nvidia* 
sudo dpkg-reconfigure -phigh xserver-xorg
``` 
Have seen this before and believe it to be the graphics card / drivers having problems

---

### Post by peyre on 2012-09-06
It's an ATI; lspci shows: 
```

Advanced Micro Devices [AMD] nee ATI RS100 AGP Bridge [IGP 320M] (rev 13)
Advanced Micro Devices [AMD] nee ATI PCI Bridge [IGP 320M] (rev 01)
VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RS100 [Radeon IGP320M]

```

---

### Post by Epodx64 on 2012-09-07
Try going to TTY1 via ctrl+alt+F1 and try "sudo shutdown -h now" or for a reboot "sudo shutdown -r now" see if that hangs or gives you errors my guess is it's the graphics card I had similar problems on a Nvidia setup.

---

### Post by peyre on 2012-09-07
Thanks Merratic!  It's ATI of course, but I tried anyway since I'm not sure what the old one had, might have been nVidia.  I never installed a special driver, FWIW, just let Xubuntu use whatever it installed natively.  (The native driver gives me 1024x768, which is the max capability of this LCD anyway.)

So I tried running those commands and rebooted a couple times, but I'm still getting the same issue.

---

### Post by peyre on 2012-09-07
> **Epodx64 said:**
> Try going to TTY1 via ctrl+alt+F1 and try "sudo shutdown -h now" or for a reboot "sudo shutdown -r now" see if that hangs or gives you errors my guess is it's the graphics card I had similar problems on a Nvidia setup.

Yep, it hung as usual (I tried both options).  I'm not surprised it's a graphics card issue.  Barring suggestions from anyone else, I'll probably wipe the drive and install a fresh copy of Xubuntu on this machine next week.

---

### Post by Epodx64 on 2012-09-07
> **peyre said:**
> Yep, it hung as usual (I tried both options).  I'm not surprised it's a graphics card issue.  Barring suggestions from anyone else, I'll probably wipe the drive and install a fresh copy of Xubuntu on this machine next week.

My only suggestion would be to install the x-swat/x-update ppa and grab the current ATI drivers it use to work for me when I was using a Nvidia card worth a shot if your gonna wipe the drive anyway

---

