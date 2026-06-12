---
title: "How do I get into root mode to edit xorg.conf? Note: Xubuntu not Ubuntu"
date: 2009-02-03
forum: Desktop Environments
---

### Post by frankwakeman on 2009-02-03
I stress that 'not Ubuntu' there because I've tried gksudo gedit... and so on but nothing happens, literaly nothing happens though I hear the hard drive having a bit of a turn.

How do I get to the point of being root and editing xorg.conf so that I can save it properly?  It would be a lot easier if I could just log on as root... sigh....

I am trying to paste someone's successful xorg.conf regarding the dreaded GeForce fx5200 card in a last ditch attempt to avoid having to buy something else or use a different OS.

If someone could - with no jargon or assumptions whatsoever - walk me through this editing process, I'd appreciate it.  Once I'd applied the restricted driver the display went from a useless 800x600 to a dire 640x480.

I'll give this 10 pm tonight (three hours) after a month of messing about, trying around 25 distros, returning to the Ubuntu family periodically - after which the card goes in the sea....:p  Then I'll get an fx6200, which apparently works.  If it doesn't, it's Bowling For Columbine time.;)

Thanks.

---

### Post by toopi on 2009-02-03
Xubuntu does not contain Gedit, instead it has a very lightweight text editor, mousepad.  Try this:  ```
 gksu mousepad 
```

---

### Post by frankwakeman on 2009-02-03
Ha ha, yes, I found this out about three seconds before you posted that.  Thanks anyway.  Any further tips appreciated.  

Right, here goes... this is war.

---

### Post by snowpine on 2009-02-03
And of course, you can install gedit too if you want:

```
sudo apt-get install gedit
```

---

### Post by frankwakeman on 2009-02-04
A big breakthrough, and one that may be of use to some using the forum. My monitor's native 1078x768 is finally working.

I pasted bits of my xorg.conf that worked for Ubuntu 6.06 into the 8.10 xorg.conf, replacing its one.  These sections were concerning the monitor, screen and device.

I think the problem all along has been that Ubuntu, Xubuntu and Linux Mint haven't recognised my monitor, not the graphics card, though that may have played a part in flummoxing the installation.  The xorg.conf with 8.10 as made originally described the monitor as 'unknown' and 'crt', maybe because I have a quite old 15 inch TFT monitor connected with a normal crt monitor-type cable?  I'm not technical enough to know if this makes sense, but I've got a hunch.  It might explain why some people with a GeForce FX5200 aren't having trouble.

I've not installed the 173 driver, but with this old machine I don't think I'd get good 3D anyway (without things getting laggy when online) and the display is very good, it's the first I've seen of this in a month or longer of messing about.  I'm really pleased; with some adaptation this must be of use to others too.  If someone's pc was faster, I would think they could install 173 and then splice the extra monitor detail into the new xorg.conf.

---

### Post by bagy on 2009-10-06
Type in terminal:
```
sudo mousepad /etc/X11/xorg.conf
```

---

