---
title: "Screen doesn't turn off when I close the lid"
date: 2016-08-22
forum: Desktop Environments
---

### Post by intexdk on 2016-08-22
Hi

I just installed Ubuntu 16.04 on my Lenovo Ideapad s510p Touch. I've tried getting the computer to suspend when I close the lid but without success.
I've tried the normal System Settings, no good.
I've tried dconf-editor: org->gnome->settings-daemon->plugins->power: lid-close-ac-action(suspend), lid-close-battery-action(suspend), lid-close-suspend-with-external-monitor(true), no good.
I've tried manually editing /etc/systemd/logind.conf, un-commenting HandleLidSwitch=suspend and HandleLidSwitchDocked=suspend, no good.

Now, I've discovered that when I close down the lid, the screen doesn't even turn off. I can see the light through the crack. I think that's a bit odd. Maybe not?


I would like my laptop to suspend when I close the lid, or at the very least, to turn the monitor off. Anybody know about this or can help me solve it? =)
I'm grateful for whatever help you can give. Thanks!


Simon

---

### Post by oldrocker99 on 2016-08-23
I have a Toshiba cheapo laptop which won't suspend no way, no how. I ended up using this command for hibernation, which isn't suspend, but it does work:```
sudo pm-hibernate
```

---

### Post by intexdk on 2016-08-24
My hibernation doesn't work, at all, but it doesn't bother me too much. I just wanna know about the suspend/turn off screen. I just went back to Ubuntu after having used Windows for a couple of years, and even though I love the design and philosophy it's honestly a bit disappointing that these very, very basic things are still a problem for many users.

---

