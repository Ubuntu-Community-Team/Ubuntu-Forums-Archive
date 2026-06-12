---
title: "Problems running steam?"
date: 2013-04-11
forum: Gaming &amp; Leisure
---

### Post by heWhoWearsAshes on 2013-04-11
Is anyone else having problems with steam; particularly after it's installed, on the second run?

I installed it and downloaded tf2, and in the middle of that, it told me that I needed to install some graphic driver. Then it restarted the steam client, and kaput. It says that I need to enable direct rendering, which I'm working on at the moment. I think I'm running it on 64 bit pangolin (I'm not at home today, I can't check).

Anyone else have this problem?

---

### Post by Scrimshander on 2013-04-11
I did a clean install yesterday to play tf2. Make sure you installed linux-headers-generic , it's listed as a dependency for the experimental drivers (310) but for some reason did not install. Fall back onto the nouveau drivers before installing that and then install the nvidia-experimental-310 drivers. That worked for me O_o

---

### Post by heWhoWearsAshes on 2013-04-11
Right, I'm sure I installed linux-headers-generic right before installing steam. I'll try that tomorrow when I'm back home, but what do you mean the nouveau drivers?

---

### Post by Bölvaður on 2013-04-11
Nouveau is an open source implementation of a driver for Nvidia graphic units. It lacks features the official Nvidia drivers have, which is specially true for performance in 3d rendering.
You are required by Steam to have a "recent" official Nvidia graphic drivers installed in order to play any game (properly). I think there are some guides released by Valve, and more, for how to do just that.

---

### Post by heWhoWearsAshes on 2013-04-11
But I have a radeon card. Is there anything for that?

---

### Post by myromance123 on 2013-04-13
Radeon cards have their open source drivers as well, nicely called Radeon. Or you could use the proprietary drivers from AMD which are the fglrx drivers.

Open Ubuntu's dash, and type in Software Sources. Open that, and head on over to the Additional Drivers tab. Now you should be presented with a list of graphics drivers. Since I don't know what graphics card model you have (whether new or old), I'm not sure what you'll see.

Just take note that if it has X.Org early in the name, then it's the open source driver. If it has fglrx at the end, then it's the AMD Official proprietary driver. To install either one, just select it and click Apply changes. Now restart, and you should be fine.

P.S: To avoid any problems, just make sure to do this in a new Terminal BEFORE installing the drivers:
```
sudo apt-get install linux-headers-generic
```

---

### Post by heWhoWearsAshes on 2013-04-13
I find the "ATI Binary X.Org driver", but the license is proprietary. Is there somewhere else I can get the driver that isn't the software center?

And I'm using the radeon hd 4350.

---

### Post by myromance123 on 2013-04-14
You do not want to use the proprietary driver? 

Then all you have left is the Open Source driver, which is installed and used by default in Ubuntu. What you have right now is the Open Source driver. The only other place you can get the driver is from AMD's website itself, and that is under a proprietary licence as well. Just note that your card is now under Legacy.

---

### Post by heWhoWearsAshes on 2013-04-15
Oh, that's disappointing. So I'm having these problems cause my card isn't supported anymore?

---

### Post by myromance123 on 2013-04-16
The last proprietary driver from AMD that works in Ubuntu 12.04 that should support your card is the AMD Catalyst 12.8 driver. Have you tried to give that a go?

Your problems with TF2 are probably from the fact that you're using the Open Source drivers ( I'm assuming you haven't installed the official drivers ).

---

### Post by snafu006 on 2013-04-16
> **heWhoWearsAshes said:**
> I find the "ATI Binary X.Org driver",  but the license is proprietary. Is there somewhere else I can get the  driver that isn't the software center?

And I'm using the radeon hd 4350.

_**you just need to get the ATi 13.1 drivers from the web  **_[http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)
 
The above post are making this hard for you to install the drivers it not hard at all

step 1 open terminal:

(past) 
sudo apt-get install libc6-dev-i386
-> hit enter 
->enter you login password


Step 2:
                 to make it work with the new 13.1 legacy drivers on a  radeon hd  4250 or 4350, i had to COMPLETELY UNINSTALL the old drivers first  (otherwise i  would get sRGB error):
 
sudo sh /usr/share/ati/fglrx-uninstall.sh --force
sudo apt-get remove --purge fglrx fglrx_* fglrx-amdcccle* fglrx-dev*
)
-> after reboot, installed the new ones:

sudo sh 'REPLACE-WITH-PATH-TO-amd-driver-installer-catalyst-13.1-legacy-linux-x86.x86_64.run' --force
Example sudo sh '/home/snafu/Downloads/amd-driver-installer-catalyst-13.1-legacy-linux-x86.x86_64.run' --force
-> then rebooted again.
-> (optional) made some performance adjustments in the catalyst control center panel

Good luck

---

### Post by heWhoWearsAshes on 2013-04-17
> **myromance123 said:**
> The last proprietary driver from AMD that works in Ubuntu 12.04 that should support your card is the AMD Catalyst 12.8 driver. Have you tried to give that a go?

Your problems with TF2 are probably from the fact that you're using the Open Source drivers ( I'm assuming you haven't installed the official drivers ).

You assume wrong. I've tried with both. I don't wanna use the proprietary driver because when I installed it, it caused the steam client to crash. Now with the legacy driver installed, I still can't enable direct rendering (which no one has helped me with yet). The client runs smoothly with the legacy driver, but I think it's keeping me from playing games. 

I'll try this in the morning:

> **snafu006 said:**
> _**you just need to get the ATi 13.1 drivers from the web  **_[http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)


---

### Post by snafu006 on 2013-04-17
make sure you to un install  the drivers first or you might break X.org follow my post to the tee lol your card should work, on this laptop that i am on has a ATI 4250 HD and i can play killing floor, CS gams what ever else that only need 128 to 256 video memory.

P.S next time i buy a computer ill try Nvidia. AMD ALWAYS drops support to soon and **** drivers.

---

### Post by myromance123 on 2013-04-18
> You assume wrong. I've tried with both.
My apologies then, it's hard to guess without prior information being given. All the best, I hope snafu006's method works for you :)

---

### Post by heWhoWearsAshes on 2013-04-20
I think it's working!!!

Just waiting for some updates to download before I can give it test drive.

---

