---
title: "When I close my lid laptop goes on standby"
date: 2013-10-21
forum: Desktop Environments
---

### Post by linuxjozi2 on 2013-10-21
Hi

I have just upgraded to 13.10 Lubuntu.

Now every time I close my lid it goes on standy or hibernat im not sure.

I have set the xfce4 power settings when on power and on battery to "lock screen" tried closing the lid but still goes on standby. Set it to "do nothing" and still no change.

I have tried installing gnome-power-manager as well but that made no difference.

By the way when it comes back on line by powering it up again, the wireless doesnt work anymore and I need to reboot each time.

Any suggestions would be greatly appreciated.

Thanks.

---

### Post by slickymaster on 2013-10-21
Please disregard. Answering to the wrong thread.

---

### Post by itsacoaster on 2013-10-21
Just wanted to post something saying that I'm experiencing the same thing since installing Lubuntu 13.10 today, and that there appears to be a bug listed for it.

[https://bugs.launchpad.net/ubuntu/+source/xfce4-power-manager/+bug/1222021](https://bugs.launchpad.net/ubuntu/+source/xfce4-power-manager/+bug/1222021)

Hope it gets resolved soon.  It worked before... I guess 12.10 was the last version I used.

> **itsacoaster2 said:**
> Just wanted to post something saying that I'm experiencing the same thing since installing Lubuntu 13.10 today, and that there appears to be a bug listed for it.

[https://bugs.launchpad.net/ubuntu/+source/xfce4-power-manager/+bug/1222021](https://bugs.launchpad.net/ubuntu/+source/xfce4-power-manager/+bug/1222021)

Hope it gets resolved soon.  It worked before... I guess 12.10 was the last version I used.

I hate to double post but I had some self-inflicted account issues and I'd like to keep tabs on this thread with this account.

---

### Post by oldos2er on 2013-10-21
You don't need to post in a thread to keep track of it; that's what the 'Subscribe to this thread' option under Thread Tools is for.

---

### Post by linuxjozi2 on 2013-10-22
Hi, I used a workaround I found in the bug report ([https://bugs.launchpad.net/ubuntu/+source/xfce4-power-manager/+bug/1222021](https://bugs.launchpad.net/ubuntu/+source/xfce4-power-manager/+bug/1222021)). Not quite sure what it does but the laptop doesnt sleep when I shut my lid anymore.

"Temporary workaround is to set:

HandleLidSwitch=ignore

in /etc/systemd/logind.conf"

But the settings in my xfce4 power manager are still not applied....

I tried to lock the screen manually but found the xscreensaver daemon was not running for some reason....

Once it was running and I was able to lock my screen.

And when I close my lid the screen locks as per my xfce4 power manager settings + workaround mentioned in my last post....

---

