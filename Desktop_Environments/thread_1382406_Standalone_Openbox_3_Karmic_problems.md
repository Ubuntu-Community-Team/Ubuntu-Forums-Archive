---
title: "Standalone Openbox: 3 Karmic problems"
date: 2010-01-15
forum: Desktop Environments
---

### Post by hhh on 2010-01-15
As the title says, I'm running Openbox sessions in Karmic with no desktop environment (meaning I'm NOT running a Gnome/Openbox session)...

1) Sound is muted after reboot. I have to go into Alsamixer and unmute the Master, Headphone and Front channels. If I do (as root) alsactl store and put alsactl restore in my autostart.sh file, sound will persist if I log out and back in but gets muted again after rebooting. ???

2) I cannot get the Num Lock key to persist after logout or reboot (I've tried the Ubuntu fixes). If I reboot it stays on through the Grub2 menu but goes off during usplash. ???
-edit- Fixed with numlockx, via here...
[http://crunchbanglinux.org/forums/topic/1803/starting-with-numlocks-resolved/](http://crunchbanglinux.org/forums/topic/1803/starting-with-numlocks-resolved/)

3) Logging in to the Openbox session takes a good 15 seconds longer than logging into Gnome. There is a bug reported for this but the workaround posted does not WFM...
[https://bugs.launchpad.net/ubuntu/+source/openbox/+bug/502481](https://bugs.launchpad.net/ubuntu/+source/openbox/+bug/502481)
???

-edit- Oh yeah, 4) I have no clue how to get my keyboard multimedia keys (volume up/down/mute) working in Openbox, they work fine in Gnome.
-edit- Strike 4), the solution is here...
[http://crunchbanglinux.org/forums/topic/5114/media-keys-in-openbox/](http://crunchbanglinux.org/forums/topic/5114/media-keys-in-openbox/)
I still have to unmute volume via alsamixer or gnome-volume-control-applet before the keys will work though.

Anyone else running Openbox alone in Karmic having these issues, or better yet, have any solutions?

Thanks. I'm loving Openbox.

-edit- 2 and 4 are done thanks to the crunchbang forums, but I've tried all sorts of configuration /startup entries/permissions for alsactl store/alsactl restore and it WILL NOT save those settings for openbox after a reboot.

-edit- 3 down, 1 to go, solution to 3) is here...
[http://ubuntuforums.org/showthread.php?t=1382348](http://ubuntuforums.org/showthread.php?t=1382348)
I don't know why alsactl store won't persist, I've tried adding 'alsactl restore' (no quotes) to /etc/rc.local and 'alsactl restore &' to autostart.sh, no joy.

---

### Post by hhh on 2010-01-16
The big finish, 1) solution. I should have mentioned that volume settings weren't persisting after reboot but weren't persisting between my Openbox sessions and my Gnome sessions either. The fix is in comments #38 and #39...
[https://bugs.launchpad.net/ubuntu/+source/alsa-utils/+bug/449783](https://bugs.launchpad.net/ubuntu/+source/alsa-utils/+bug/449783)
After that I had to add 'alsactl restore &' to ./config/openbox/autostart.sh for Openbox AND add 'alsactl restore' to /etc/rc.local for Gnome and now I have sound ready-to-go no matter which session I logout-login/reboot from. Joy!

---

### Post by Telecaster72 on 2010-01-16
Bad News - I cant help you with any of your problems.
Good News #1- I can confirm the slow log in (LXDE Session, but LX uses Openbox so i think it is the same issue) so you are not alone.
Good News #2 - I Bumped your post ;)
(Edit) Good News #3 - I cant read apparently, you already fixed your problems, congrats!

---

