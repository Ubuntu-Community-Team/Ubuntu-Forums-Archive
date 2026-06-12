---
title: "internet problem, somebody please help, about to give up on linux"
date: 2005-08-05
forum: Desktop Environments
---

### Post by nocloud on 2005-08-05
okay, i recently installed kubuntu for my first try with linux.

after hours and hours of work trying to get the internet to work, i am on the verge of giving up on linux.

my computer is a dell inspiron 6000 with a intel 2200b/g wireless card and broadcom 4400x 10/100 network card.  i do not use wireless so i do not know if the wireless works or not, but no matter what i try, i cannot get the wired network card to work.

when i try to access the network settings, i am unable to make changes or enter administrator mode.

when i use "sudo kcontrol" in konsole, i can get into administrator mode and go to make changes.  my network cards are both disabled and when i try to enable them, they will enable for like one second and then automatically go back to the disabled state.

for this reason, i cannot get the network card to enable and as a result, i have no internet.  without internet, any computer is useless and i will be unable to keep using linux unless i can get this internet problem fixed.

can somebody please help me?

---

### Post by elsewhere on 2005-08-05
AFAIK, that Broadcom interface should be supported out of the box.
As much as I love KDE, I find kcontrol pretty weak for configuring network settings.

I would suggest:

a) Using *sudo ifup eth0* from a shell prompt to see if you can bring the interface up manually

If that doesn't work,

b) Check your **/etc/network/interfaces** to make sure you have a reference to eth0

In mine, I have a line "*iface eth0 inet dhcp*" that designates eth0 as being an external network interface (inet) that obtains it's ip address vi dhcp.

If that still doesn't work, then you'll probably have to check to make sure the kernel module for the broadcom is being loaded.  You can list the kernel modules with lsmod but I'm not sure of the name for the broadcom driver.

Perhaps someone else can offer some more detailed advice?

Hope this helps...

Cheers,
KV

---

