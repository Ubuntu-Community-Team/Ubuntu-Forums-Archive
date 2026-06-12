---
title: "Razer Nostromo"
date: 2011-10-27
forum: Gaming &amp; Leisure
---

### Post by dalamar666 on 2011-10-27
Hi,

I am having some issues getting the key bindings to work with my nostromo.  I have installed the driver and followed the instructions from [http://ubuntuforums.org/showthread.php?t=538319](http://ubuntuforums.org/showthread.php?t=538319) .

The issue I am having is that after I close the nostromo_config I get this line:  nostromo_daemon: no process found
then nothing.

I run the nostromo_daemon and nothing happens.  No icon on the taskbar nothing.  I did run the nostromo_config first and did run it under sudo.  I have also done the chmod 666 /event* thing.

I tried pystromo but I could not get the map file to work correctly.  The cursor went to the next line and hung.  I would rather use the nostromo config file.  

I am using nostromo driver version 1.4.1

---

### Post by dalamar666 on 2011-10-30
Bumpity bump bump

---

### Post by Sanaki on 2012-02-28
Is it a Belkin Nostromo n52, a Belkin n52te, or a Razer Nostromo? There are significant differences between them, and as far as I can see the (overall superior) Razer Nostromo has no way whatsoever to make it work in linux. If that's what you've got, I feel your pain.

---

### Post by xinel on 2012-04-10
followed the guide here:
[http://ubuntuforums.org/showthread.php?t=948833](http://ubuntuforums.org/showthread.php?t=948833)

and it worked for my razer nostromo

i just used the output of lsusb in my default.map as it states in the guide

changed some of the key bindings and it worked nicely

then made a little bash script to be run after kde logs in :)

all in kubuntu 11.10

---

