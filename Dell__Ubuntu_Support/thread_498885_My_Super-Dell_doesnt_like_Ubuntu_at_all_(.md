---
title: "My Super-Dell doesnt like Ubuntu at all :("
date: 2007-07-11
forum: Dell  Ubuntu Support
---

### Post by metallicamaster3 on 2007-07-11
just bought myself a Dell XPS 720 H2C a few weeks back. 

specs:
	
Intel Core 2 Extreme QX6700
4GB RAM
Dual Video Cards, 2x 768MB Nvidia GeForce 8800 GTX
Dual Monitors; dual 30" Apple Cinema Displays (purchased seperatly of course)
1 1/2 TB Hard Drive Space,  RAID 0 (2 x 750GB)
Sound Blaster X-Fi "XtremeMusic" Sound Card
AGEIA PhysX physics accelerator 
ATI Theater 650 PRO Combo Analog/Digital TV Tuner with Remote Control

Windows Vista Ultimate
Windows XP Professional SP2
Windows XP Media Center 2005 SP2
Windows 2000 Professional SP4


I tried to Put Ubuntu 7.04 Fiesty Fawn on it...but it just hates my computer. First, no sound. Second, NO dual monitors. Ive tried every HOWTO to get that working....but no joy. The resolution could not get any higher than 800x600, which looked very terrible.

Also, some keyboard buttons do NOT work. (Apple Keyboard) Such as: Option, Command, Eject, Volume Keys, F14/15/16. This i just shrugged off, since its an Apple Keyboard and all.



suggestions? I miss my Ubuntu!

---

### Post by lproe on 2007-07-12
Did you try installing  915resolution package?

sudo apt-get install 915resolution.  

reboot and the resolution  should be fine.

---

### Post by MetalMusicAddict on 2007-07-12
> **lproe said:**
> Did you try installing  915resolution package?

sudo apt-get install 915resolution.  

reboot and the resolution  should be fine.
That is NOT going to work. He needs the nVidia drivers as well as configure xorg correctly.

The card is SO new you will need the nvidia-glx-new package (sudo apt-get install nvidia-glx-new) and set the driver in your xorg to nvidia. Reboot. I *think* the nVidia utility will set up your dual-monitors now. Its called: nvidia-settings.

---

### Post by MetalMusicAddict on 2007-07-12
> **metallicamaster3 said:**
> just bought myself a Dell XPS 720 H2C a few weeks back. 

specs:
	
Intel Core 2 Extreme QX6700
4GB RAM
Dual Video Cards, 2x 768MB Nvidia GeForce 8800 GTX
Dual Monitors; dual 30" Apple Cinema Displays (purchased seperatly of course)
1 1/2 TB Hard Drive Space,  RAID 0 (2 x 750GB)
Nice. ;) The displays should work fine once your sort out your xorg.
> Sound Blaster X-Fi "XtremeMusic" Sound Card
AGEIA PhysX physics accelerator 
ATI Theater 650 PRO Combo Analog/Digital TV Tuner with Remote Control
I have NO clue if those are gonna work. I know the physics accelerators sound cool but all signs look like they will start to be built onto GFX cards. So I'm waiting. :)
> Also, some keyboard buttons do NOT work. (Apple Keyboard) Such as: Option, Command, Eject, Volume Keys, F14/15/16. This i just shrugged off, since its an Apple Keyboard and all.

suggestions? I miss my Ubuntu!

---

### Post by metallicamaster3 on 2007-07-12
sudo apt-get install nvidia-glx-new

worked like a charm! i got every resolution from 640×480 to 7680×4800 :). they all work! (7680×4800 by the way.....the wallpaper was the size of a 32px icon! o.o) my personal favorite res for my monitor(s) (:D!!) are 1920×1200. 

dual monitors = HEAVEN! i love Beryl and Compiz fusion now ^_^ ^_^ ^_^

---

### Post by MetalMusicAddict on 2007-07-17
> **metallicamaster3 said:**
> sudo apt-get install nvidia-glx-new

worked like a charm! i got every resolution from 640×480 to 7680×4800 :). they all work! (7680×4800 by the way.....the wallpaper was the size of a 32px icon! o.o) my personal favorite res for my monitor(s) (:D!!) are 1920×1200. 

dual monitors = HEAVEN! i love Beryl and Compiz fusion now ^_^ ^_^ ^_^

Killer. Heres my 2 fav hi-res wallpaper sites. [HERE]("http://interfacelift.com/wallpaper/index.php?sort=date") and [HERE]("http://www.mandolux.com").

---

### Post by pikul on 2007-07-18
Its good that you managed to fixed at least your video card problems, and let me tell you, EXCELLENT MACHINE YOU HAVE :popcorn::o

---

### Post by strabes on 2007-07-18
That is a freaking awesome rig. Wow.

---

### Post by bimmerd00d on 2007-07-19
How about an external pic of your setup.

---

### Post by rscott5 on 2007-07-20
I second that request. Pics please! lol

---

### Post by gvoima on 2007-07-26
X-Fi cards are not supported in linux at all. Atleast not in ALSA.

From ALSA pages:
> Card delivered to developers. Completely new architecture. Creative actively preventing support due to no datasheets being released to ALSA developers. Reverse engineering work not started due to lack of time.

---

