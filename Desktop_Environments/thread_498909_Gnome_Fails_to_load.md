---
title: "Gnome Fails to load"
date: 2007-07-11
forum: Desktop Environments
---

### Post by Marchard on 2007-07-11
Hi,

When i boot/reboot my ubuntu fiesty fawn i am able to boot correctly into gnome.But when i logoff and login Gnome is not loading and i can see an empty screen with a dialog box not rendered correctly.(i can see just a white patch ).What can be the reason.

---

### Post by kfrance on 2007-07-12
If you wait about five minutes I think gnome will finally load with an error.  I still don't have a solution.  I let you know if I find one.

---

### Post by rrlane on 2007-07-12
I just loaded ubuntu for the first time, and I'm getting the exact same error message.  Any help resolving this would make this newbie grateful.

---

### Post by kfrance on 2007-07-13
I finally got mine working but I'm not sure exactly what I did.  I just waited for 5 minutes, got into gnome, and used it for an entire day and the next time  I booted it up it worked.  I deleted my .gnome, .gnome2 and .gnome_private folders and perhaps using the system for some time I set a setting that made it boot properly.  Others I have seen have had a messed up /etc/network/interfaces file.  See if that is your problem.  Here is what my file looks like.

```
iface lo inet loopback
auto lo

auto eth0

auto eth1

auto eth2

auto ath0

auto wlan0
```

I also reinstalled gdm and ubuntu-desktop.  Maybe something there will work for you.

---

### Post by tipiglen on 2007-09-13
Same sort of problem.  everything boots ok, nice ubuntu drumbeat and login.  user name ; password, 
screen clears to nice dark maroon and mouse pointer (moves around ok, no click-action), and nothing else - dead keyboard, ctrl/alt/del ineffective; ctrl/alt/backspace exits to tty, but with very limited capacities.  

Now trying the "wait five minutes or so"  tip.

Logged in fine on first boot-up after install from scratch (via hard disk, since cd very dodgy),  but every attempt since gets me the pleasant dark maroon......

waiting patiently
ed

---

### Post by tipiglen on 2007-09-13
Still waiting 30 minutes later.  Trying failsafe (ctrl/alt/backspace) and trying something to do with compiz.
salaam, etc
ed

---

