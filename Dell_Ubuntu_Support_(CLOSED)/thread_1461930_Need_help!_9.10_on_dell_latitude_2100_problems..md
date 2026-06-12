---
title: "Need help! 9.10 on dell latitude 2100 problems."
date: 2010-04-24
forum: Dell Ubuntu Support (CLOSED)
---

### Post by d3m2 on 2010-04-24
I have this notebook about a month or so, and a few days ago I updated it to ubuntu 9.10, and since then I'm faced with these problems. I've used ubuntu for a while, even before the notebook, but, as it turns out, I'm a noob.
My problems are:
#1 / When I turn it on, after 2-3 sec.s, a pop-up pops up :) and says: 

Warning: Screen isn't compsited. Pleace run compiz (-fusion) or another compositing menager.

Well, I have no idea how to run it. (this is apparently becuase avant-window-navigator, whitch I find very usefull)

#2 / There is no sound at all. The drivers 'seem' to be there but when I open System-Preferences-Sound, under the hardware tab, there is nothing listed. Again I have no idea how to fix this.

#3 / (I left the best for last) The touchpad isn't responding. Not even the slightest. I've read other posts about this problem and I can't seem to get over it. In xorg.conf the touchpad is not listed, and I tried to edit it, on account of what I read on those other posts, but it woudn't save itself. It says something like: 'You're not authorised to do so'. I'm the first owner and I have only one user account. Also I tried something witch involves creating an file with hal - I think, like some posts said. Not being able to use the touchpad, I have to find my way around using the keyboard, so it's not like I can do with my notebook much.

Pleace help! Every book that I need for studying is in there and I can't acces them properly. I've tried not to post something that has been already, but I can't fix it instrucioned by the other ones. 
That's about it. So again, pleace help.

---

### Post by marco.cervantes on 2010-04-25
i think you need to install Compiz with this code:

```
 sudo apt-get install compiz compizconfig-settings-manager 
```that shuld fix it i hope.

and for sound i need to know what hardware you run. Use this:

```
 sudo lshw -html > hardwareprofile.html 
```There look for you audio hardware and mouse. post the results here.

---

### Post by d3m2 on 2010-04-25
I says:

compiz is already the newest version.
E: Couldn't find package compizconfig-settings-menager

And in hardwareprofile.html:

id: multimedia
description: Audio device
product: 82801G (ICH7 Family) High Definition Audio Controller
vendor: Intel Corporation
physical id: 1b
bus info: pci@0000:00:1b.0
version: 01
width: 64 bits 
clock: 33MHz
capabilities: pm msi pciexpress bus_master cap_list
configuration: driver  = HDA Intel
                         latency = 0
resources: irq      : 21
                   memory : f6ebc000-f6ebffff

And i can't locate the mouse part, but 3 parts a red: VGA compatible Controller and Display Controler abd SMBus.

---

### Post by d3m2 on 2010-04-25
Sorry for the type-os, I writing this from my phone.

---

### Post by d3m2 on 2010-04-29
Is there no one that could help me? I know that this will turn out to be simple but there is no way for me to work this out unless i have some help. I went through a lot of threads but none would work for me.

---

