---
title: "knoppix works with my sound but ubuntu dont, help plz"
date: 2006-06-04
forum: Desktop Environments
---

### Post by nic886 on 2006-06-04
I have installed Ubuntu Dapper Drake 6.06 and ive got to say its the best desktop linux distro ever! only one problem: knoppix detects my sound device and uses driver "i810_audio" but my sound does not work in ubuntu. how do i load this driver into ubuntu and get my sound? plz any suggestions as i am currently having to use windows :(

---

### Post by ktulu1115 on 2006-06-04
Yeah, I had a similar problem.  I was trying to play movies but totem-gstreamer didn't work, so I installed totem-xine, and now I have no sound whatsoever.  The volume control is disabled with a "no volume control GStreamer plugins and/or devices found".  Removing totem-gstreamer hosed my entire system, and I've already re-installed 3 timex to fix this stupid problem.

---

### Post by JoWilly on 2006-06-04
[QUOTE=nic886]I have installed Ubuntu Dapper Drake 6.06 and ive got to say its the best desktop linux distro ever! only one problem: knoppix detects my sound device and uses driver "i810_audio" but my sound does not work in ubuntu. how do i load this driver into ubuntu and get my sound? plz any suggestions as i am currently having to use windows :([/QUOTE]

check it this module is loaded with "lsmod |grep -i i810_audio"

if it is not, load it with "sudo modprobe i810_audio".

Don't forget to submit a bug report on launchpad to inform the developers (search the bugs first).

EDIT: and add the module to /etc/modules

---

### Post by JoWilly on 2006-06-04
removed double post sorry

---

