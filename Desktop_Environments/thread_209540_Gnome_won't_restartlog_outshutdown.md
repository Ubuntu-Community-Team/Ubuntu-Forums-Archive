---
title: "Gnome won't restart/log out/shutdown"
date: 2006-07-05
forum: Desktop Environments
---

### Post by Sciamano on 2006-07-05
Hi everybody.
I'm new to the forum, and fairly new to Ubuntu, which I've been using for a couple of weeks with much satisfaction.

I am now encountering the following problem (I have two actually, but since they seem unrelated, I'll post the other one in a different thread):
basically if I try to shutdown the computer, or even restart Gnome (either with the ctrl-alt-backspace combo or using the shutdown button and then "logout") the computer freezes.
If I try the shutdown, it will show the desktop background and it freezes.
If I try to restart Gnome or to logout, the screen will go black and nothing will happen.

What can I do?
Thanks in advance for any suggestion.

Luca

---

### Post by zhoux on 2006-07-05
you can try sudo reboot or sudo poweroff in terminal and see if it returns an error....though i don't know how to solve this prob.

---

### Post by Sciamano on 2006-07-05
sudo reboot works

---

### Post by wazoo on 2006-07-05
This seems to be a video driver conflict. You don't say if you're using ATI or nVidia. But in my case, using the "nvidia-legacy" driver took care of the problem. I found it in Synaptic.

---

### Post by jchavezb on 2006-12-24
Hi,

I'm using Edgy Eft on a HP Compaq nx6325 which has a ATI RS482 Radeon Xpress 200M integrated shared memory video adapter.

I also end up in a state where I can close all my applications but GNOME itself won't shutdown, either thru the shutdown button for Menu -> Quit.  One side effect of this is that, after hard shutdown, the system comes back up with auto fsck failed and forces me to run a full fsck.

Could this be video card related as well or what other aspects of the system should I look into.  

Thanks.

---

### Post by Sciamano on 2006-12-24
Can't say for sure, but after I switched from an ATI graphic card to an NVidia one, all these problems have disappeared.

---

### Post by unibok on 2007-06-03
Hi all,

I think this problem is related with ATI graphic cards, especially with Xpress 200M (which a lot of users seem to have) and is not specific only to GNOME but persist in KDE aswell.

Have not yet found a solution to it.

---

### Post by Sciamano on 2007-06-03
It's possible. As I stated earlier, I switched to NVidia cards and never had the problem again ever since.

---

