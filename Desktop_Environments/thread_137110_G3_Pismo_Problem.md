---
title: "G3 Pismo Problem"
date: 2006-02-27
forum: Desktop Environments
---

### Post by Strag0 on 2006-02-27
Hello,

I just installed Ubuntu onto my Powerbook Pismo last night. Everything worked fine on it. However, now that I've rebooted it in the morning... Gnome refuses to show up. I get a log in screen... but once I log in the screen stays brown and the GUI doesn't show up.

Does anyone have an Idea what is causing this?

Thanks.

---

### Post by LordBug on 2006-02-27
Never tried Linux on a G3 (though this might change real soon), but I've had similar issues on x86 hardware.  It was caused by the video driver.  You might want to check this, maybe change to something more generic.

---

### Post by svref on 2006-02-27
I have a G3, and I had a similar problem, except that it didn't take FOREVER, just REALLY LONG (3-15 minutes) to log in, all the while stuck in the brown screen with a mobile white arrow cursor.

Did you perchance skip the "configure the network" phase of the install?

The first time you logged in did gnome kvetch that it couldn't lookup its own IP address?

If either of these are true, take a look at your /etc/hosts, and make it look a little sumpthin like this:
```
127.0.0.1 localhost.localdomain localhost umlaut
192.168.88.14 umlaut.mydomain.com umlaut

```
where you replace "umlaut" with your hostname, 192.168.88.14 with some IP address that makes sense (as much as static IP on a laptop makes sense at all...which is not much...ok just pick something in 192.168.?.?).

Note: this isn't the technique I used to actually fix our problem, instead I just reinstalled, but I'm curious if it would have fixed it, had I known what /etc/hosts should have looked like.

---

### Post by svref on 2006-02-27
PS: I'm not bothering with all the useless crap at the end of /etc/hosts, that stuff should not be disturbed.

---

### Post by Strag0 on 2006-02-27
It's the oddest thing, Ubuntu was 'hanging' while loading Gnome while I was at school. However, when I come home the system boots and Gnome shows flawlessly. So I'm thinking it might be a wireless network thing, thats the ONLY thing different. The machine is set up to connect to my home SSID(and with it's WEP), but not for my school's wireless network.

---

