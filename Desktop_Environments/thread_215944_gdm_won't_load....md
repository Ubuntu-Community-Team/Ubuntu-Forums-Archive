---
title: "gdm won't load..."
date: 2006-07-14
forum: Desktop Environments
---

### Post by royg1234 on 2006-07-14
Hey,

GDM won't load.  When I start up, it goes all the way to the part where it shows the cursor "spinner", then the screen goes black and then to a bash login (no blue screen about xorg being misconfigured).  Before it goes to the bash login, I very briefly see something in the top left about "dhcdbd", "dhcbdb" or something like that.

This started happening after the last round of dist-upgrades (~Wednesday).

I'm using a Gateway 3522GZ laptop with 915resolution installed (for widescreen), if that helps.

Can someone point me in the right direction?

Thanks.

---

### Post by Paerez on 2006-07-14
can you post your /var/log/Xorg.0.log and "dmesg | tail -n 50"?

---

### Post by royg1234 on 2006-07-15
> **Paerez said:**
> can you post your /var/log/Xorg.0.log and "dmesg | tail -n 50"?

I can't do the "dmesg | tail -n 50", because I'm in Windows right now (I'm not good with command line), but here's my /var/log/Xorg.0.log -- **[http://www.roygullem.com/misc/Xorg.0.log](http://www.roygullem.com/misc/Xorg.0.log)**

---

### Post by Paerez on 2006-07-15
hmm, there weren't any crazy errors, just some weird stuff about resolutions. What resolution can your monitor do? Also, please post your /etc/X11/xorg.conf. Thanks.

---

### Post by royg1234 on 2006-07-15
> **Paerez said:**
> hmm, there weren't any crazy errors, just some weird stuff about resolutions. What resolution can your monitor do? Also, please post your /etc/X11/xorg.conf. Thanks.

my /etc/X11/xorg.conf - [http://www.roygullem.com/misc/xorg.conf](http://www.roygullem.com/misc/xorg.conf)

My laptop monitor does up to 1280x768, which is what I have it set to by using 915resolution.

---

### Post by tzulberti on 2006-07-16
I think that it is trying to open at 1024x768. In a console write "sudo dpkg-reconfigure xserver-xorg". Press Enter until it ask you about the resoluciont. Reestart Gdm writin "sudo /etc/init.d/gdm stop; sudo /etc/init.d/gdm strart".

I hope that solves your problem.

---

### Post by Paerez on 2006-07-16
if you only want to change the resolution, use:
```
# sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by royg1234 on 2006-07-17
> **Paerez said:**
> if you only want to change the resolution, use:
```
# sudo dpkg-reconfigure -phigh xserver-xorg
```

Thanks for all the help, but this still doesn't work (I think the resolution's fine, because when the mouse spinner comes up, it looks like it's the right proportion).  I don't know what else to try.

---

### Post by royg1234 on 2006-07-23
anyone have the same problem?

---

### Post by royg1234 on 2006-07-23
I've reached a breakthrough, sort of.  When I go into terminal and type
```
gdmsetup
```
, it tells me
```

  Failed to connect to socket, sleep 1 second and retry
  Trying failed command again.  Try 2 of 5.
  Failed to connect to socket, sleep 1 second and retry
  Trying failed command again.  Try 3 of 5.
  Failed to connect to socket, sleep 1 second and retry
  Trying failed command again.  Try 4 of 5.
  Failed to connect to socket, sleep 1 second and retry
  Trying failed command again.  Try 5 of 5.
  Command failed 5 times, aborting.

```

Oh, and kdm works just fine.

---

