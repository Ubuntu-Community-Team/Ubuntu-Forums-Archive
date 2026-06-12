---
title: "ETQW crashes when using voip"
date: 2009-11-20
forum: Gaming &amp; Leisure
---

### Post by lakersforce on 2009-11-20
Clean install of 9.10. (and updates applied.)

Newest driver from nvidia applied (because default was buggy)

Sound in etqw is "jumping." When ever I try to use voip the game instantly crashes. (No devices available in-game.) Can recieve voip though.

Followed the following thread to no avail: [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

output of lspci:
> 
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 10)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 10)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation GT200 [GeForce GTX 260] (rev a1)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)



---

### Post by Cresho on 2009-11-21
I had the same issue with this as well.  I have a solution to this problem too!

The problem here is pulseaudio.  you will need to uninstall it and use alsamixer.  I've solved this issue. but I went back to hardy heron because karmic koala isnt as stable as I would of liked it to be since I really push the hardware limit.  Stick with LTS releases since they are more stable and have longer time support.  ETQW needs a audio patch if you want the mic to work with pulseaudio and there is none.

I recommend you use a fresh install on a separate drive so you won't screw up your karmic koala.
```
#killall pulseaudio
#sudo apt-get remove pulseaudio
#sudo apt-get install esound
#sudo apt-get install gnome-alsamixer
#sudo apt-get install
these next two not needed but just incase
#install jaunty alsa-utils_1.0.18-1ubuntu11_amd64.deb
#sudo rm /etc/X11/Xsession.d/70pulseaudio (do not do this just incase)
#Reboot system
```

this particular alsa-utils_1.0.18-1ubuntu11_amd64.deb file you need to pay close attention.  if you dont have this, grab it off an intrepid release.
or
Just do a search for alsa utils in synaptic and after install, do a "alsamixer" in terminal and fix your  mic level in capture.  It worked for me when i used karmic koala but i also use a 24bit audigy gamer card that is very supported for mic and 5.1 audio.

---

### Post by lakersforce on 2009-11-23
It made ETQW work, but now I have all kinds of other sound problems (skipping and/or no sound) in rest of the Gnome applications.

I did not install the specific deb file, as a generic version was already installed in my system (or perhaps it got installed along the previous commands.)

Thanks anyway mate.

---

### Post by Cresho on 2009-11-30
well, open up a terminal and type "alsamixer" no quotes and fix your audio there.

my hardrive died and took hardy with it.  I installed karmic koala cuz of the gts250 support and it works.  audio works.

also depends on your soundcard.

---

### Post by lakersforce on 2010-03-15
> **Cresho said:**
> 
```
#killall pulseaudio
#sudo apt-get remove pulseaudio
#sudo apt-get install esound
#sudo apt-get install gnome-alsamixer
#sudo apt-get install
these next two not needed but just incase
#install jaunty alsa-utils_1.0.18-1ubuntu11_amd64.deb
#sudo rm /etc/X11/Xsession.d/70pulseaudio (do not do this just incase)
#Reboot system
```


I found a better option. Install the libsdl1.2debian-pulseaudio package.

EDIT: I tested it out and it worked. Could record my own audio and play it in-game. 5 mins later, with no changes it stopped working and I get the segfault again.

---

