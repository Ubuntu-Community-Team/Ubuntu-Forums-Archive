---
title: "Cinnamon continually freezes?"
date: 2014-01-17
forum: Desktop Environments
---

### Post by Richard Carlson on 2014-01-17
I've got KDE, Gnome, and Cinnamon installed on my machine. I believe all the files I need to installed to run it are all there. KDE and Gnome both work flawlessly. My machine is an 8350 8-core Amd, 16 gig-ram, 650 Nvidia video, and 3 terabyte drive. Evey time I boot up into the main menu that asks for a password and I select Cinnamon it starts but as soon as I click on anything on the screen (i.e. menu, for instance it pops up then the whole screen freezes. I'm running 319 nvidia driver and everything seems to function in the other two desktops without any hitches. Any idea's? Suggest? and or help would be appreciated. 

Richard :(

---

### Post by Richard Carlson on 2014-01-17
I guess a bigger question is to ask are all of the desktops supposed to work and interact  from the same start up menu and or are there  still glitches in each desktop that interferes  with this process? I've got xubuntu  and lxde installed also.  So where lies the problem with the freezeups? Xubuntu and Lxde appear to work but switching between desktops may be where the problem lies. Sometimes the machine doesn't want to do that it  and it too locks up until I press 'alt-control-F1'. 

Rich :)

---

### Post by VMC on 2014-01-17
> **Richard Carlson said:**
> ...I select Cinnamon it starts but as soon as I click on anything on the screen (i.e. menu, for instance it pops up then the whole screen freezes. I'm running 319 nvidia driver and everything seems to function in the other two desktops without any hitches...
I had the same issue using Mint and/or [X,U,G]buntu using the default *nouveau* driver. It works using nvidia driver.

---

### Post by Frogs Hair on 2014-01-17
I too run multiple window managers, but only three and I am running the sessions and not the full desktop installations. Cinnamon has been great for some users and a problem for others. Your posts suggest your running five or six desktops and there is no way to know if there are conflicts . With what the desktops  listed you have possibly four or more different file managers installed.

---

### Post by VMC on 2014-01-17
@Frogs Hair, I'm unsure who your referring your comment to. I'm guessing the OP, but I use separate partitions for each install, so that's not an issue for me.

---

### Post by Frogs Hair on 2014-01-17
The op from what I gather has a Lubuntu installation with multiple desktop environments . Cinnamon is installed as an extra desktop environment either via ppa or the repository . It is possible to install all of the environments from the repository on the same installation, but the waters can get muddy in terms of overlap of similar types of applications . This not the same as having different distributions on different partitions.

---

### Post by kellemes on 2014-01-22
Delete  ~/.cinnamon and try again.

---

### Post by Baldrick_NZ on 2014-01-22
I had the same issue when I installed Cinnamon on top of Gnome Shell earlier this week. I installed from the Ubuntu repos only to discover it's a really old version that basically just gets security updates now. This froze immediately when I clicked on anyting in the task bar. The only thing that would work was the mouse.

I found that by completely purging Cinnamon
```
sudo apt-get remove --purge cinnamon*
```
then doing a clean up to remove any unwanted files,
```
sudo apt-get autoremove; sudo apt-get clean
```
I added the official Cinnamon PPA and installing Cinnamon from that
```
sudo add-apt-repository ppa:gwendal-lebihan-dev/cinnamon-stable; sudo apt-get update; sudo apt-get install cinnamon
```
fixed the freezing problem for me.

Hope this helps.

Cheers.

---

