---
title: "Help please!"
date: 2009-04-29
forum: General Help
---

### Post by Dbzdude707 on 2009-04-29
Basically, I just installed Ubuntu 9.04 Jaunty using partitions on a Compaq Presario C700 laptop, and all I've done is install updates (System -> Administration -> Update Manager). Once it finished installing and updating, everything seemed to work perfectly, except that when I went to System -> Preferences -> Appearance -> Visual Effects and it was set to None. I want Normal effects. So I clicked Normal and it did its thing for a second or two, and it told me shortly that it couldn't apply these effects. I did some research and it looks like the program that manages these effects is called Compiz, and it looks like there's some problem between it and Intel monitors that started back in 8.10 Intrepid or something. Well, I used to have 8.10 Intrepid and it gave me no problems with this (mind you, that old installation of 8.10 Intrepid is completely gone, the installation of 9.04 Jaunty was separate from that, I didn't use the Update Manager to get here). So this leads me to believe that I don't have this problem. However, I gathered some information and perhaps this will help: (some screenshots are scaled down to help keep this from becoming a massive post)

The problem:
[IMG]http://i5.photobucket.com/albums/y168/Dbzdude707/visualeffects.png[/IMG]

Installed drivers:
[IMG]http://i5.photobucket.com/albums/y168/Dbzdude707/drivers.png[/IMG]

Hardware information:
[IMG]http://i5.photobucket.com/albums/y168/Dbzdude707/lspci.png[/IMG]

PS. If you're going to suggest I install a driver, you'll need to tell me where to find it. I doubt I'll be able to find it on my own...

Also I'm really sorry about this, but when I last posted this here I got no response so I figured maybe I'd get more results if I try it here.

---

### Post by lisati on 2009-04-29
Did you notice on the message relating to the drivers a warning "Only activate this driver if you having trouble with your wireless LAN connection"? I think the drivers you installed could be unrelated to the trouble you had with the effects.

---

### Post by Dbzdude707 on 2009-04-29
> **lisati said:**
> Did you notice on the message relating to the drivers a warning "Only activate this driver if you having trouble with your wireless LAN connection"? I think the drivers you installed could be unrelated to the trouble you had with the effects.

Yeah, and that driver is not activated. I only posted an image of that window to show you guys what drivers I have installed. The only one I have that it shows is not activated.

---

### Post by Dbzdude707 on 2009-04-30
Hey, it's been longer than a full day so I just wanted to see if anyone will notice it this time... =/

---

### Post by Dbzdude707 on 2009-05-01
Well, it's that time again, it's been about a day.

---

### Post by Legace on 2009-05-01
> In the new Ubuntu 9.04 Jaunty Jackalope, Intel graphic (video) drivers 965 (x3000 or x3100) are blacklisted so you cannot run Compiz thus your desktop effects cannot be enabled. There is a way to enable desktop effects, though this is not recommended because the drivers were blacklisted due to an error in xserver-xorg-video-intel and they will be whitelisted when the bug fill be fixed.

To enable desktop effects anyway, type this in Terminal and reboot and try to enable the desktop effects again..

```
mkdir -p ~/.config/compiz/ && echo SKIP_CHECKS=yes >> ~/.config/compiz/compiz-manager
```

---

### Post by Dbzdude707 on 2009-05-01
> **Legace said:**
> To enable desktop effects anyway, type this in Terminal and reboot and try to enable the desktop effects again..

```
mkdir -p ~/.config/compiz/ && echo SKIP_CHECKS=yes >> ~/.config/compiz/compiz-manager
```

Wow, thanks! I'll try it. I don't see what harm could come of it, as 9.04 is not a huge change from 8.10, and these effects worked in 8.10.

---

