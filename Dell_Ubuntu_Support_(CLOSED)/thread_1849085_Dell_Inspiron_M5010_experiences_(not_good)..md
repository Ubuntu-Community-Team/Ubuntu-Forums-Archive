---
title: "Dell Inspiron M5010 experiences (not good)."
date: 2011-09-23
forum: Dell Ubuntu Support (CLOSED)
---

### Post by aspidistra on 2011-09-23
Have had to abandon 11.04 because of this issue:

[http://ubuntuforums.org/showthread.php?p=11276022#post11276022](http://ubuntuforums.org/showthread.php?p=11276022#post11276022)

Dell Inspiron M5010 laptop Ubuntu 11.04 - cursor freezes after some use

went to 10.10 today to try it .. couldn't even install that (it doesn't initially without setting ACPI (power management) off in the grub settings.  

I noticed even on the install the same thing was happening which is giving me problems with 10.04 (mouse flicks around when you click on something - intolerable).  The mouse problem is not to do with "tap to click" it flicks away when you click on something

Now I am going to xubuntu 11.04 hoping that the cursor freezing issue isn't there on that.

I was going to try the 11.10 beta but there is no classic desktop - also really - a beta - uncharted territory.  Close to abandoning ubuntu totally at least on the M5010 because of this issue

can't believe 10.10 won't install at all on it ... set ACPI=off in the grub boot and it does install but further to that it won't boot ... I was told that pressing any key on a boot should give you the grub menu but that does't even work.  From what I know through investigating this the problem with the mouse is down to the synaptic driver

here the version numbers between 10.04 and 11.04

SYNAPTICS INSTALLLED 1.2.2-1ubuntu4  (10.04)
latest (11.04) = 1.3.99

mouse cursor jumping on click (always seems to be down and to the right) does not happen on 11.04 (because it is the later driver by some version numbers shown above).

So ... the mouse driver should be the later with xubuntu.  xubuntu is xfce window manager not gnome.  I have not been able to find out what cursor freezing problem is at all .. hopefully it's gnome/desktop effects issue.  xubuntu is a lot plainer.

Was trying to upgrade the synaptics driver on 10.04  earlier (would be nice - no freezing & touchpad issue resolved) but upon installing the .deb file from the repository

xserver-xorg-input-synaptics_1.3.99+git20110116.0e27ce3a-0ubuntu12.1_amd64.deb

I automatically got dependency errors (not straightforward) ... could state the error but the system is gone now -- was to do with C++ headers 

If anyone can tell me how to get the later synaptics driver onto ubuntu 10.04 it would help

all in all it's not been a good experience at all with this m5010 have tolerated the freezups so-far

summary - 10.04 incompatible with m5010 synaptic touchpad m5010 constantly locks up with 11.04 ... 10.10 same mouse problems I suspect (as far as I can tell the mouse driver is the same as 10.04) - but 10.10 doesn't even install

not good for such a common top line dell inspiron model ... can someone provide information?  can this be elevated?

---

### Post by aspidistra on 2011-09-24
found out about kernel upgrades 

will try upgrading 11.04 kernel to 3.0 soon & report (as I said -- cursor freeze failure after some use (can be days))

[http://techtimely.wordpress.com/2011/08/19/install-linux-kernel-3-0-on-ubuntu-11-04/](http://techtimely.wordpress.com/2011/08/19/install-linux-kernel-3-0-on-ubuntu-11-04/)

this is a big kernel upgrade I am hopeful

also I think ... there may be messages in /var/log if it does fail -- i'll install ssh server so I can get into the machine and look

I will solve this

---

### Post by mörgæs on 2011-09-25
I didn't completely understand... How did the computer work with Xubuntu 11.04?

---

### Post by aspidistra on 2011-09-26
M5010 is going on ebay (incompatible)

downgraded to 1525 (completly compatible)

---

### Post by aspidistra on 2011-10-22
UPDATE ---- 

have stuck with the M5010 -- installed xubuntu 11.10 --

touchpad driver is the later - problems gone

also ... hopefully!  I think the mouse freezing problem (which I could have looked into more) won't be present as it is XFCE 4.8 (latest version) - not gnome.  Couldn't confirm that that problem was due to gnome but ... what else GUI updates majorly between versions ... problem was not extant on 10.04

btw ... the frozen mouse unlocks when you connect using x2x (controlling mouse/keyboard on one pc from another) .. why is that  ... had tried for some time the machine (ubuntu 11.04) with desktop effects off (& classic desktop) .. still locked eventually .. couldn't see any system messages where I looked.

xubuntu 11.10 (XFCE 4.8 ) looks amazing -- very fast

Will report back on this thread if any more problems with ubuntu / Dell M5010

---

