---
title: "MCE remote stopped working lirc"
date: 2009-02-11
forum: General Help
---

### Post by onesojourner on 2009-02-11
after the last round of upgrades my MCE remote has stopped working. irw gives me no response. I have tried uninstalling lirc. Can some one help me troubleshoot this?

---

### Post by kdog_1914 on 2009-03-28
I have the same problem.  This happened on both my 8.04 and 8.10 mythtv frontend.

I have also attempted it on a beta 9.04 with the same result.

hardware.conf shows:

#Chosen Remote Control
REMOTE="Windows Media Center Remotes (new version Philips et al.)"
REMOTE_MODULES="lirc_dev lirc_mceusb2"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_LIRCD_CONF="mceusb/lircd.conf.mceusb"
REMOTE_LIRCD_ARGS=""

which worked previously.  What puzzles me most is a clean install of mythbuntu 8.10 does not resolve it even before being updated.

Are these remotes prone to failure and I just happened to have two bad ones go out close to each other?

Is there a remote with equivalent functionality that I should be looking for?

---

### Post by jj_ffa on 2009-09-06
This should fix your problem:

sudo apt-get install lirc-modules-source

then:

sudo /etc/init.d/lirc restart

---

