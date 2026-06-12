---
title: "[SOLVED] Trouble with nvidia drivers"
date: 2009-01-03
forum: General Help
---

### Post by stretch427 on 2009-01-03
Hey all, I'm relatively new to linux, and I'm having some trouble with my nvidia 8800gt. I'm pretty sure its a problem with my xorg.conf settings, but not exactly sure. 
Every time I reboot, it tells me to reboot in low graphics mode. Also, when I look at my hardware drivers the nvidia module isn't enabled. Then When I try and enable and restart, it does it all over. It's weird because once I get back into Ubuntu, I have to go to Visual Effects and click either Extra or Normal before I can move any windows around. It always says "Desktop Effects could not be enabled." 
The end goal is dual monitor set up with desktop effects enable. 
P.S. I do have Compiz Fusion installed but it won't work without Desktop Effects being enabled. 
Any help  would be greatly appreciated.
~Stretch~

---

### Post by redneckProgrammer on 2009-01-03
stretch,
  Have you run the update manager and installed all updates before you try to enable the nvidia drivers?  If not, you might want to try that first.

---

### Post by redneckProgrammer on 2009-01-03
You might want to take a look at this posting.  Looks like there is some manual xorg config that might help.
[URL="http://ubuntuforums.org/showthread.php?t=965085&highlight=8800gt"]
http://ubuntuforums.org/showthread.php?t=965085&highlight=8800gt[/URL]

---

### Post by shashank.shekher.02 on 2009-01-03
i m a newbe in ubuntu....i installed envy...rebooted my comp....still m not able to activate desktop effects. plz help me.....m ready to give u content of xorg.conf if u ask...plzz help me....i m using ubuntu ultimate 1.8....1gb ram core 2 duo 1.8ghz, nvidia 6200 tc...thanx in advance!

---

### Post by hotweiss on 2009-01-03
Luckily I to have an 8800GT and have experienced this problem many times. First you have to remove all of the old Nvidia drivers:

sudo apt-get remove nvidia*

And then you have to reinstall the driver. 180.18 is a really good driver...

PS-you have to this in recovery mode

---

### Post by stretch427 on 2009-01-03
> **hotweiss said:**
> Luckily I to have an 8800GT and have experienced this problem many times. First you have to remove all of the old Nvidia drivers:

sudo apt-get remove nvidia*

And then you have to reinstall the driver. 180.18 is a really good driver...

PS-you have to this in recovery mode

Well I did something to it last night and I don't remember what, but now I get,

(EE) Problem parsing the config file
(EE) Error parsing the config file
 
at reboot. 

Now as far as un-installing the drivers and installing 180.18, would I do that with Synaptic Packet Manager? Or simply from the command line?  Because I looked in Synaptic and didn't see any 180.18. What am I looking for?

As to the other poster, I checked out that link you posted, and couldn't find a whole lot pertaining to my issue but thank you for the effort!

So the issue stands, I can't enable nvidia drivers and when I do, they don't stay enabled.

---

### Post by stretch427 on 2009-01-03
Yes I've run update manager many times, but that doesn't seem to help. It just says
"your system is up to date"

Just for clarification. Some system specs are listed below.

Dual Core E6750, 2.66GHZ @ 2.83GHZ (Just on stock cooling)
Mobo: Abit IP35-E
8 gigs Corsair Ram
Nvidia 8800gt
Dual Boot Ubuntu 8.10/Vista Home Premium

---

### Post by stretch427 on 2009-01-03
Bumpity bumb bumb.

---

### Post by hotweiss on 2009-01-03
What lead to the Nvidia driver being corrupted?

---

### Post by stretch427 on 2009-01-03
It was a kernel update, and they broke. I'm trying to simply reinstall, but i'm having trouble. I was reading some forums, and they said to install from the Ubuntu repositories so they won't break at each kernel update, but I can't find how to do that.
Help?

---

### Post by hotweiss on 2009-01-03
Oh I see. If it was a kernel update you have to rebuild the driver:

> sudo sh NVIDIA* -K

---

### Post by stretch427 on 2009-01-04
Ok I ran the command you gave and it spat out this,
ERROR: You appear to be running an X server, please exit X before installing.

And at the moment, when I go into my Hardware Drivers manager, all I see is my Linksys WMP300n wireless card drivers. 

Now It looks like the drivers aren't even installed

---

### Post by hotweiss on 2009-01-04
> **stretch427 said:**
> Ok I ran the command you gave and it spat out this,
ERROR: You appear to be running an X server, please exit X before installing.

And at the moment, when I go into my Hardware Drivers manager, all I see is my Linksys WMP300n wireless card drivers. 

Now It looks like the drivers aren't even installed

Follow these steps:

1) Press Ctrl-Alt-F1
2) Type sudo /etc/init.d/gdm stop
3) Type sudo sh NVIDIA* -K
4) Reboot

---

### Post by stretch427 on 2009-01-04
That was Gold, Thank you, but one more question. What does the "-K" stand for?

---

### Post by hotweiss on 2009-01-04
> **stretch427 said:**
> That was Gold, Thank you, but one more question. What does the "-K" stand for?

I think kernel... It just tells the Nvidia drivers to rebuild themselves for the updated driver... I think. Glad you have it worked out now...

---

### Post by stretch427 on 2009-01-04
Well I guess it didn't quite work as well as we thought. When I rebooted this morning, It booted into low graphics mode, giving me a "type1" error or something. So I need to save the xorg.conf file? and back it up? i'm confused why does it keep rebooting into the low graphics mode?

and now it's saying that /etc/X11/xorg.conf does not exist.

---

### Post by stretch427 on 2009-01-04
Bump, 

sorry I thought the problem was fixed.

---

### Post by hotweiss on 2009-01-04
At this point you probably have to rebuild your xorg. So get back into recovery mode, and type this:

sudo dpkg-reconfigure xserver-xorg

---

### Post by stretch427 on 2009-01-04
Ok so I did that and it worked, but then what, I tried removing the nvidia drivers and reinstalling but when I try and open up: gedit /etc/X11/xorg.conf nothing shows up. I'm missing something.

When I try and remove the nvidia drivers it says it can't find them, and then when I try to install it says they're already there... i'll go get the actually error in a sec


The error is when I try to sudo sh NVIDIA* -K

I get this

ERROR the file '/lib/modules/2.6.27-9-generic/kernel/drivers/video/nvidia.ko' already exists as part of this driver installation.

---

### Post by hotweiss on 2009-01-04
> **stretch427 said:**
> Ok so I did that and it worked, but then what, I tried removing the nvidia drivers and reinstalling but when I try and open up: gedit /etc/X11/xorg.conf nothing shows up. I'm missing something.

When I try and remove the nvidia drivers it says it can't find them, and then when I try to install it says they're already there... i'll go get the actually error in a sec


The error is when I try to sudo sh NVIDIA* -K

I get this

ERROR the file '/lib/modules/2.6.27-9-generic/kernel/drivers/video/nvidia.ko' already exists as part of this driver installation.

So everything is fine now?

---

### Post by stretch427 on 2009-01-04
Alright here's what I did for those that may need it:

nvidia-installer --uninstall
sudo /etc/init.d/gdm stop
(press alt F4 to login, and make sure you cd into the directory where you want to install the file from. In my case the "NVIDIA-Linux-x86-177.82-pkg1.run" was in my "home" folder, so I typed:) 
cd /home
sudo sh NVIDIA*

and finally after the installation is complete 
sudo reboot

I'm still trying to figure out how to save my configuration though, because everytime I reboot it all goes to nothing, 
I've sudo'd into nvidia settings, and saved the X configuration but is there anything else I need to do. Like back it up?

---

### Post by hotweiss on 2009-01-04
> **stretch427 said:**
> Alright here's what I did for those that may need it:

nvidia-installer --uninstall
sudo /etc/init.d/gdm stop
(press alt F4 to login, and make sure you cd into the directory where you want to install the file from. In my case the "NVIDIA-Linux-x86-177.82-pkg1.run" was in my "home" folder, so I typed:) 
cd /home
sudo sh NVIDIA*

and finally after the installation is complete 
sudo reboot

I'm still trying to figure out how to save my configuration though, because everytime I reboot it all goes to nothing, 
I've sudo'd into nvidia settings, and saved the X configuration but is there anything else I need to do. Like back it up?

Hmmm, if you can get into Ubuntu without problems now, I'd install the drivers once in Ubuntu using Envy:

[http://www.albertomilone.com/envyngfaq.html#A](http://www.albertomilone.com/envyngfaq.html#A)

Envy almost always works...

---

### Post by stretch427 on 2009-01-05
Hey it works reboot and everything, at least in this kernel, we'll have to see if it sticks through the next kernel update. Hopefully! But thanks for your help!
Stretch

---

