---
title: "Add/Remove problems, list of applications is not available"
date: 2008-12-05
forum: General Help
---

### Post by nicklikesfire on 2008-12-05
Hello,

So I'm trying to install gnome partition editor (I assume this is the gparted thing that everyone keeps telling me about). When I goto add/remove, and select it, I get the message:

> The list of applications is not availabe

Click on 'Reload' to load it. To reload the list you need a working internet connection. 

at which point I click "refresh" (there is no reload button). Enter my password, it does something and a progress bar flashes past. Then I click on gparted again, and the same thing happens?

Any ideas? How do I get started?

---

### Post by Nathan Sweeney on 2008-12-05
> **nicklikesfire said:**
> Hello,

So I'm trying to install gnome partition editor (I assume this is the gparted thing that everyone keeps telling me about). When I goto add/remove, and select it, I get the message:



at which point I click "refresh" (there is no reload button). Enter my password, it does something and a progress bar flashes past. Then I click on gparted again, and the same thing happens?

Any ideas? How do I get started?
What about trying Synaptic?  System -> Administration -> Synaptic Package Manager?

or

```
sudo apt-get update
sudo apt-get install gparted

```
from a terminal?

---

### Post by nicklikesfire on 2008-12-05
> **Nathan Sweeney said:**
> What about trying Synaptic?  System -> Administration -> Synaptic Package Manager?

or

```
sudo apt-get update
sudo apt-get install gparted

```
from a terminal?

I'm not sure exactly how to install from Synaptic (I tried searching gparted and partition, etc). Then I tried from the terminal and ended up with:

> nick@nick-desktop:~$ sudo apt-get update
[sudo] password for nick: 
Reading package lists... Done
nick@nick-desktop:~$ sudo apt-get install gparted
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package gparted is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package gparted has no installation candidate
nick@nick-desktop:~$ 


Maybe that helps with figuring out what's wrong?

Thanks again for the help!

---

### Post by Nathan Sweeney on 2008-12-05
That's weird.  What is selected when you open Synaptic and then choose Settings -> Repositories?  I thought gparted should be in official repositories.  If I type gparted in the search box from within Synaptic, it is the first (and only) result.

---

### Post by eternalnewbee on 2008-12-05
Maybe you should enable All Available Applications in Add/Remove...

---

### Post by plucky on 2008-12-05
> nick@nick-desktop:~$ sudo apt-get update
[sudo] password for nick:
Reading package lists... Done


That says your repositories are not enabled.

Open a terminal and post output of ```
cat /etc/apt/sources.list
```.

To enable the repositories open **System > Administration > Software Sources** and make sure the boxes are ticked.(See attachment).Also make sure the CD rom box is un-ticked.

Good Luck

---

### Post by nicklikesfire on 2008-12-05
OK,

So things just got way worse somehow.

I clicked off those four repositories, and then I thought things were going to get way better. Then I tried installing the 100 something updates that were recommended. Towards the end, my computer froze, and then I restarted. At this point things went bad.

Now my wireless doesn't work (I'm on a different pc), and all my video files come up as text files.

Any ideas? I'm totally stuck!

Thanks!

---

### Post by plucky on 2008-12-05
> Towards the end, my computer froze, and then I restarted. At this point things went bad.


What was it installing when it froze.

Were there any error messages?
Can you hook it up by ethernet cable?

If you can get the internet working again,open a terminal and ```
sudo dpkg --configure -a
``` to try and fix the packages that didn't install during the update.

What are your system specifications,and what version of Ubuntu are you using?

---

### Post by nicklikesfire on 2008-12-05
> **plucky said:**
> What was it installing when it froze.

Were there any error messages?
Can you hook it up by ethernet cable?

If you can get the internet working again,open a terminal and ```
sudo dpkg --configure -a
``` to try and fix the packages that didn't install during the update.

What are your system specifications,and what version of Ubuntu are you using?

OK. So I ran that code above without an internet connection (unfortunately I have no hope of hooking that machine up to a wired connection at any point in the near future). Anyways, I ran the command, and terminal started doing some stuff. (I wish I could just copy and paste). Anyways, it went through a few things, and then eventually froze on:

> Setting up linux-restricted-modules-2.6.24-22-generic (2.6.24.14-22.53) ...

I'm running hardy, and I built the system a year and a half ago, or so. I'm not sure of the specs right now, but If it's necessary, I'll do my best to get them. Any thing else I can be doing in the meantime?

Thanks again for the replies.

---

### Post by plucky on 2008-12-05
> Setting up linux-restricted-modules-2.6.24-22-generic (2.6.24.14-22.53) ... 


That is the latest version of that package according to my Hardy synaptic.

Can you boot into a previous kernel version in the grub menu and see if the wireless connection works with that.
Did you have to do anything special to get your wireless working? Sometimes kernel upgrades causes wireless problems if you have to install wireless drivers.

From a terminal ```
cat /boot/grub/menu.lst
``` and see if there is a previous kernel version that you can boot.Check if the wireless comes back when you boot the earlier version.

Good Luck

---

