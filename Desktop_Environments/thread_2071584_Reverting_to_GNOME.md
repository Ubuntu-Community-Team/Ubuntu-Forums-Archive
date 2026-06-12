---
title: "Reverting to GNOME"
date: 2012-10-15
forum: Desktop Environments
---

### Post by oxf on 2012-10-15
OK I installed 12:04 on my new laptop. 
Hmmm I can see why people don't like Unity. I don't either!

So... I followed insrtuctions and installed gnome-session-fallback via the software centre. Thats got me back to GNOME. So two questions:

How do I get the System>Preferences and >Administration menus back on the top panel? I cant seem to figure that out.

Can I now remove UNITY from my PC completely? If so how? 
I presume via Synaptic but what do I look for?

Thanks
Veronica

---

### Post by jerrrys on 2012-10-15
Check these out

[http://ubuntuforums.org/showthread.php?t=2033371](http://ubuntuforums.org/showthread.php?t=2033371)

[http://ubuntuforums.org/showthread.php?t=1962189](http://ubuntuforums.org/showthread.php?t=1962189)

[http://ubuntuforums.org/showthread.php?t=1966370](http://ubuntuforums.org/showthread.php?t=1966370)

---

### Post by vwbug on 2012-10-15
Try Linux Mint 13 with Mate. With a little tweaking, its just like 10.04. I don't like Unity either. I tried a lot of Distros looking for a replacement and settled on Mint. My second choice would be Xubuntu.

---

### Post by vwbug on 2012-10-15
Here is my Mint Desktop.  Look familiar? 

[ATTACH]225613[/ATTACH]

---

### Post by oxf on 2012-10-15
Well thanks. I see this is a little more cpmplicated than I first thought.
If GNOME 2 is going to cause problems for me I may have to look at the alternatives above.

Thanks.

---

### Post by james_mcl on 2012-10-16
Don't worry! It's not really that complicated, as long as you're willing to install from scratch. In a nutshell, install the OS from an Xubuntu CD, then install MATE.

> 
Can I now remove UNITY from my PC completely? If so how? 


I used an Xubuntu disc instead of an Ubuntu one to install Precise with XFCE. This means that almost none of Unity ever gets installed, and you can reduce the amount further by using Synaptic to uninstall Firefox/Thunderbird's "menu integration". If gedit is installed, uninstall that so you can get rid of a version of libzeitgeist it now requires as a dependency. (A gedit fork known as pluma will be installed to replace it at a later stage)

This leaves, AFAICT, only the following:

gir1.2-unity-5.0 (Removing this also causes you to lose usb-creator-gtk)
libunity9 (I would have lost Sound Juicer if I'd removed this)

Anyway, there's no visible or intrusive manifestation of Unity so far.

That brings us to Step 2 - getting Mate. The instructions are on [http://wiki.mate-desktop.org/download](http://wiki.mate-desktop.org/download) - check under the Ubuntu section, there are different sets of instructions for adding the repos depending on your Ubuntu version, and just below the Quantal-specific instructions you find the last step:

```

sudo apt-get update
sudo apt-get install mate-archive-keyring
sudo apt-get update
sudo apt-get install mate-core
sudo apt-get install mate-desktop-environment

```

(When it asks about that hddtemp thing, say yes. Accept defaults where offered)

When you boot into MATE, you'll now have a system near-identical to a Gnome 2 system, with the System - Preferences and System - Administration menus in their usual place. A few applications will look a bit rougher around the edges (I've only noticed this with Update Manager and Audacious so far), and you will find that both GNOME and MATE versions of some applications are installed. Plus, Pluma will now be installed, and it's almost identical to gedit.

It's working beautifully on my box.

---

### Post by oxf on 2012-10-26
Thanks James for that very detailed reply, sorry for the delay!
Veronica

---

### Post by cmcanulty on 2012-10-26
be aware that classic uses gnome 3 it just looks like gnome 2

---

### Post by mardybear on 2012-10-27
Howdy.

This is going to sound very old fashioned and a might get bashed. I understand that updates are occasionally required as security flaws are identified, but why do operating systems and desktop environments need to change so frequently. Choice is good but change for no other reason seems like busy work to me. I still use Ubuntu 8.04 and 10.04 on a daily basis, which includes running a business network, without problems or security breaches - hope that doesn't jinx me or motivate hackers.

I follow the forums closely and am reluctant to upgrade to the newer versions of Ubuntu due to the many complaints and problems encountered by other users following upgrades or new installs. I'm a fan of classic gnome and mostly openbox...'if it ain't broke, don't fix it'. Although i don't change systems often, my next install will likely be Arch Linux or Crunchbang (basically Ubuntu defaulted to Openbox).

So much effort seems to have been spent making upgrades and new installs look like the 'classic' version...why not just keep using the classic version? As i said 8.04 still runs flawless and 10.04 is still supported for a while longer...

Sorry for the rant ;)

mardybear

---

### Post by cmcanulty on 2012-10-28
+1!!!

---

