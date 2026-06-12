---
title: "[SOLVED] Help please with nvidia 5500 and compiz"
date: 2007-12-26
forum: Desktop Environments
---

### Post by AndreiMe on 2007-12-26
I don't know if this is the right place to write this but I'm just stuck at something. I have ubuntu for a couple of days, in dual boot with XP.
I like it a lot, i spend 80% of the tie in ubuntu rather then xp.
So one day i wanted to install beryl. It didn't work. I read then about compiz and installed it. It doesn't work. I have my video card (inno3d nvidia geforce fx 5500, 256 mega and 128 bit) installed in ubuntu and i though that it should work with compiz or beryl at acceptable level. And then i saw that i cannot add any workspace. This is strange. I followed every step shown in tutorials and etc, but somehow it doesn't work. Is there something I can do or should i just reinstall ubuntu(not what i would like to do :P)
please any help will be greatly appreciated.

---

### Post by Samhain13 on 2007-12-26
I have the same card. Have you installed the restricted drivers for Nvidia?

---

### Post by AndreiMe on 2007-12-26
yes i reinstalled it through envy, and enabled it again through restricted device manager.
i have installed the compiz settings manager, but it doesn't respond to whatever changes i make it doesn't respond.
+ i cannot add workspaces, it is very annoying.
i don't have a very good computer (amd sempron 2200+, 1 giga ram, that card shown there, asus a7n8x-deluxe, and 80 giga hdd) but it should work just fine i guess on it. still it doesn't.
any ideas?

---

### Post by Samhain13 on 2007-12-28
We have more or less the same specs, I have a Sempron 2400+ and 1 GB of RAM too. Plus the same graphics card.

But I got my restricted drivers just by trying to enable visual effects after installing Ubuntu 7.10. When I selected normal, I got a warning that told me something to the effect that I needed to enable restricted drivers. Then there was a box telling me the specific one that I had to install. Checked it, installed it and restarted.

Anyway, searching Synaptic for the packages I got:
**nvidia-glx**
**nvidia-kernel-common**

It might also help making sure that the "Proprietary drivers for devices (restricted)" option in the Repositories menu in Synaptic is checked first because I think that's where those packages will come from.

[edit]

About the additional workspaces.

What I did was just right-click on the Workspace Switcher in the panel (mine's at the bottom), then preferences and set Columns to 4. I didn't have to go to CCSM.

[edit 2]

I just saw this:

> So one day i wanted to install beryl. It didn't work. I read then about compiz and installed it.

Did you uninstall the Beryl you installed before you installed Compiz? And I don't think you should have installed Compiz because it already comes with 7.10; you just needed to enable it.

Unless, of course, you're in a different version. I was under the impression that we're both using 7.10. If you have both Beryl and Compiz in your computer then that could be it.

---

### Post by AndreiMe on 2007-12-28
so, i managed to make it run.
i purged all compiz following another post in this forum, and then reinstalled it. 
but firstly i removed all my repos, i guess one wasn't very indicated to be placed there, it had some issues, and then installed the manager. and it works.
now the final biggest problem in ubuntu will be making opera(the greatest browser) to work. this two were the only problems that took more than 2 hours to fix. thanx though for the prompt help.

---

### Post by turtlepaul on 2008-01-13
I have a similar problem, but when I try to enable the restricted nvidia drivers it comes up with this error message:

E: /var/cache/apt/archives/nvidia-glx-new_100.14.19+2.6.22.4-14.10_i386.deb: subprocess pre-installation script returned error exit status 2

I'm running 7.10 btw.

---

### Post by cory_k on 2008-01-14
I get the exact same message as turtlepaul.

Running Gutsy, Just changed cards from ATI 2600 HT to geforce 8600 gts.

Tried envy, but it caused x to crash "Fatal Error - no screens found"

Uninstalled envy and x works fine, but can not enable the restricted driver.  

Any help would be greatly appreciated.

---

### Post by AndreiMe on 2008-01-14
i had something like this when i wanted to install something and it didn't work.
from what i understand, of course, you can install something by so many means but from experience it's not the best way to try to install them over and over again.
I had problems, big one, that i only fixed by removing all the repos and purge the application and try a clean install from an example that worked.
When i installed the video driver, it didn't quite work. I used envy first time and something like an erorr apear. I also couldn't use the restricted driver  at first but i went to google and tried this:
sudo apt-get update
sudo apt-get install nvidia-glx
sudo apt-get upgrade
sudo dpkg-reconfigure xserver-xorg

    * Select the nvidia driver from the X server driver list and follow the on-screen steps to complete the configuration

Once finished with the configuration, hold down Ctrl+Alt+Backspace to restart X server. You should be presented with a nice NVIDIA splash screen signaling that the driver is installed and working
I hope this helps you in a way. Maybe even try reinstalling envy?

---

### Post by cory_k on 2008-01-14
Thanks for your help AndreiMe, but even doing it your way I get the same error:

> /var/cache/apt/archives/nvidia-glx-new_100.14.19+2.6.22.4-14.10_i386.deb: subprocess pre-installation script returned error exit status 2

Maybe my old ati driver is somehow getting in the way.  Perhaps I should try from a fresh install.  That's just such a pain in the **** tho...

Thanks again.

---

### Post by AndreiMe on 2008-01-15
hmm that could be the problem.
new drivers are always good, and most people recomend installing them, but some may have crashes and so one. so maybe a newer version of your driver, maybe a month ago.
just be sure to remove all of your old driver cause you will get crashes if not, trust me :P

---

