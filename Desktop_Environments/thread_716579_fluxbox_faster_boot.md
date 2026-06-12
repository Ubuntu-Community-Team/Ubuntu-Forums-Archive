---
title: "fluxbox faster boot"
date: 2008-03-06
forum: Desktop Environments
---

### Post by agim on 2008-03-06
I remember reading on the forums that there is a way to make fluxbox a lot faster on boot. Something along the lines of turning off a service. What I plan on doing is a server install, then adding fluxbox and the programs I use. But I want to make my machine as efficient as possible.

Any help would be great. Thanks.

---

### Post by kerry_s on 2008-03-06
huh? server/base install you only install what you want, wouldn't be no extra services to turn off.

---

### Post by kerry_s on 2008-03-06
i'm back :)
i been busy with a friends "kiosk" how to, he asked for my help to get started. i been testing things all day. trying to make it dead simple and putting what works into a doc.

anyways simple server/base install instructions.

install the base
sudo apt-get install xserver-xorg-video-vesa xorg synaptic fluxbox rox-filer leafpad
startx
open synaptic and install what ever else you want.

xserver-xorg-video-vesa  <-if you specify your vid driver before xorg, it will only install that driver.

to auto start X put this in your ~/.bash_profile

```
if [ `tty` = "/dev/tty1" ]; then
startx
fi

```


auto log in, is untested, i use debian, but i use to do it in the *ubuntu's. :)
sudo apt-get install rungetty

gksu leafpad /etc/event.d/tty1

comment out->
respawn /sbin/getty 38400 tty1

put->
respawn /sbin/rungetty tty1 --autologin user

"user" would be your log in name.

---

