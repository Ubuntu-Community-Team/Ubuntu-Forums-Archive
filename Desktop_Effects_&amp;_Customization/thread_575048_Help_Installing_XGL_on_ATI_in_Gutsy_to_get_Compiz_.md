---
title: "Help Installing XGL on ATI in Gutsy to get Compiz to work"
date: 2007-10-13
forum: Desktop Effects &amp; Customization
---

### Post by jmusso on 2007-10-13
Hi. Sorry this seems like it would be a common thread but I can't find anything relating.

I downloaded the RC for Gutsy, burned it to a disc, and fresh installed in on my hard drive. Now I've run into the small problem that I cannot enable the restricted drivers to work so I can turn the desktop effects on. I believe it has to do with the fact that I do not have XGL set up on this fresh install.

Here's what I tried, and what didn't work.
System > Restricted Drivers Manager > Click on "ATI accelerated graphics driver," to which I get the following response: 
The software source for the package

   xorg-driver-fglrx

 is not enabled.

I tried a sudo apt-get install for that package, but I get nothing. I'm not sure where to go? Is it some repository I have to add? Please help. Btw, I have an ATI Radeon Xpress 200m video card on my laptop (Compaq Presario V5000). Thanks.

---

### Post by jmusso on 2007-10-14
Bump. I was able to enable the restricted driver for my video card, however, when I try to enable desktop effects, I get an error message saying "The composite extension is not available." Help please?

---

### Post by ericdegen on 2007-10-14
I'm getting the same thing.. on an HP NC8430 - ATI Mobility X1600

Driver is on in restricted, but getting the "The Composite extension is not available" message in appearances.

Oh as usual, my Nvidia Desktop works flawlessly :S go figure.

---

### Post by ericdegen on 2007-10-14
Jmusso,

Try this man, found it in another thread worked on my x1600

sudo apt-get install xserver-xgl

Very nice, I just rebooted, non of the "session" config stuff I had to do under feisty.

Enjoy,

---

### Post by Hawk_AA on 2007-10-16
Got the same problem with my HP Compaq nc8430 and ATI Radeon Mobility X1600.

Installing xserver-xgl did not work, since i did not find the package.

---

### Post by xi3 on 2007-10-16
Ok, i had the same problem let me part with some knowledge since it was a headache to figure out. The Disappointing part of the whole exp. was i tried so many things initially that i had to reinstall and you might have to. (To get it to work correctly)

-***Clean install*** (7.10rc1) install all Compiz related updates[COLOR="DarkRed"] ( i just get all the updates plus or minus a few that i really dont need )[/COLOR]
[COLOR="SeaGreen"]-System will install updates could take as long as ~1hr for all, and as short as ~10 to 20mins for just Compiz[/COLOR]
-***Install and Enable*** ATI graphic driver in restricted driver management. [COLOR="DarkRed"](should allow you to do this as soon as you want to enable the restricted driver)[/COLOR]
[COLOR="SeaGreen"]-System will start to install 3 updates about ~8mbs[/COLOR]
-***Install*** CompizConfig Settings Manager from Add/Remove Applications[COLOR="DarkRed"] ( Easy thing to do was type in Compiz for all avaliable software and it pops ontop with a digital clock underneith it and the the one above it says something about advanced options, get that one.)[/COLOR]
[COLOR="SeaGreen"]-System will install this and it'll take about 5 minutes[/COLOR]
-***in terminal***:
**sudo dpkg install xserver-xgl** or **sudo apt-get install xserver-xgl** [COLOR="DarkRed"](forgot which on works but you have to get the ATI driver first i believe)[/COLOR]
[COLOR="SeaGreen"]-System will install this and it'll take about 2 to 5 minutes[/COLOR]
-Reboot system
[COLOR="SeaGreen"]-System reboot within 2 minutes[/COLOR]
-***Enable*** 3d Desktop's 4th option for custom effects and boom! it should work.

Tried it on several machines with ATI cards

works for 9800 , 9600 (mobile and not), and works well.

Sidenote(s): 
keep in mind too many graphics you can actually freeze your system and have to hardboot... Give it a shot and tell me what you think
Conky looks great with this :)

---

### Post by Hawk_AA on 2007-10-16
> **ericdegen said:**
> Jmusso,

Try this man, found it in another thread worked on my x1600

sudo apt-get install xserver-xgl

Very nice, I just rebooted, non of the "session" config stuff I had to do under feisty.

Enjoy,

Ahh, sorry mate. I figured it was looking for files on the CD and not on the reposories (or however to write that extremely difficult word. I just installed the package, and are now updating the system. Can't wait to reboot and see if it works!

---

### Post by fettuohi on 2007-10-16
Has anybody been able to get this to work with the newer ATI cards, i.e. 2400, 2600 & 2900 HD?

Regards

André

---

### Post by depele on 2007-10-18
nope 
hp nx9420
ati x1600

==> not successfull
just got a sucky slow gnome

---

### Post by carli on 2007-10-22
I've tried this a dozen times now on my Acer TM8210.

Once I figured out how to enable the right repositories I installed fglrx to get right resolution (1680x1050) on my system. But then I tried to enable the visual effects. After installing xgl and the compiz advanced settings panel it still simply returns the good old "Can not enable visual effects" message.

Is there a log for compiz somewhere so I can see whats going on as it tries to start?

Oh yes, and I accidentally installed some official ATI drivers from their website... is this whats keeping me from succeeding and how can I eventually remove them?

---

### Post by michael37 on 2007-10-22
Recommending moving to [thread=569654]ATI dedicated thread[/thread].  The newer 2000 cards -- if you can get fglrx driver working with either out of box Restricted Manager driver or with Envy, good for you.  If not, then it's simply not supported (yet?) by ATI closed source driver.

---

### Post by vides2012 on 2007-10-23
> **xi3 said:**
> 

-***Clean install*** (7.10rc1) install all Compiz related updates[COLOR="DarkRed"] ( i just get all the updates plus or minus a few that i really dont need )[/COLOR]
[COLOR="SeaGreen"]-System will install updates could take as long as ~1hr for all, and as short as ~10 to 20mins for just Compiz[/COLOR]
-***Install and Enable*** ATI graphic driver in restricted driver management. [COLOR="DarkRed"](should allow you to do this as soon as you want to enable the restricted driver)[/COLOR]
[COLOR="SeaGreen"]-System will start to install 3 updates about ~8mbs[/COLOR]
-***Install*** CompizConfig Settings Manager from Add/Remove Applications[COLOR="DarkRed"] ( Easy thing to do was type in Compiz for all avaliable software and it pops ontop with a digital clock underneith it and the the one above it says something about advanced options, get that one.)[/COLOR]
[COLOR="SeaGreen"]-System will install this and it'll take about 5 minutes[/COLOR]
-***in terminal***:
**sudo dpkg install xserver-xgl** or **sudo apt-get install xserver-xgl** [COLOR="DarkRed"](forgot which on works but you have to get the ATI driver first i believe)[/COLOR]
[COLOR="SeaGreen"]-System will install this and it'll take about 2 to 5 minutes[/COLOR]
-Reboot system
[COLOR="SeaGreen"]-System reboot within 2 minutes[/COLOR]
-***Enable*** 3d Desktop's 4th option for custom effects and boom! it should work.

Tried it on several machines with ATI cards

works for 9800 , 9600 (mobile and not), and works well.



Hi!

Well I have a problem: after installing xserver-xgl, and rebooting, my gutsy becomes slow, icons don't appear normally.But the bigger problem is, that if I run compiz --replace, it gives an error message: Missing GLX_EXT_texture_from_pixmaps  then it crashes.I tried your method, but I can't get it to work.I've found that some libgl-dri package should be reinstalled,  but I don't even have that package, though I have mesa installed, and I can't find that pack.

Can anyone help me pls?

I have Radeon 9800, K-Ubuntu Gutsy 7.10

---

### Post by michael37 on 2007-10-24
> **vides2012 said:**
> Hi!

Well I have a problem: after installing xserver-xgl, and rebooting, my gutsy becomes slow, icons don't appear normally.But the bigger problem is, that if I run compiz --replace, it gives an error message: Missing GLX_EXT_texture_from_pixmaps  then it crashes.I tried your method, but I can't get it to work.I've found that some libgl-dri package should be reinstalled,  but I don't even have that package, though I have mesa installed, and I can't find that pack.

Can anyone help me pls?

I have Radeon 9800, K-Ubuntu Gutsy 7.10

Definitely go to [thread=569654]ATI thread[/thread].  You have supported hardware.

Sounds to me like 'Mesa issue'.

---

