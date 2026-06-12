---
title: "Secondary Disk Spins Up On Logout"
date: 2009-02-25
forum: General Help
---

### Post by LiquidRain on 2009-02-25
I'm running a HTPC with Xubuntu.  I am running a clean, no-programs-on-startup profile, but the problem occurs on any profile on the system.

I have 2 disk drives.  One is an 80gb laptop for the system, and the other is the 1TB media storage disk set to sleep after 10 minutes.  Whenever I log out of XFCE, the 1TB disk spins up after xfce4-session-logout.  The 1TB disk drive is mounted on /mnt/storage - an innocuous place, and only houses media.  Nothing else.  The disk does not spin up on login, only logout.

I have checked /etc/gdm/PostSession as well as /etc/xdg/xfce4/ for anything that might trigger a hit on the disk after a logout, and can't find anything.  It's extremely bizarre that it happens on all profiles.  Quite simply - this shouldn't be happening!  I don't think I have any indexing applications or any such thing on, though, as the disk doesn't spin up on login.  edit: worth noting this only happens in X11, does not happen when I log in via SSH or to a TTY.

Can anyone help me get to the bottom of this?

---

### Post by Yashiro on 2009-02-25
Happens to my external USB too. It's no real help I know, but just letting you know it's not specific to your drive/setup.

---

### Post by LiquidRain on 2009-02-25
Well, that's the strange thing - I'm on Xubuntu and I've removed a bunch of stuff from it too.  I don't *have* GNOME or GVFS installed.  XFCE's volume management is setup to handle removable USB drives and to automount DVDs, but I don't think that should cause it to hit /mnt/storage.  (or maybe it will?)

Glad to know I'm not the only one with this issue.

---

### Post by sdennie on 2009-02-25
You might be able to figure out what is causing the disk activity with:

```

sudo sh -c "echo 1 > /proc/sys/vm/block_dump"

```

Then log out check /var/log/syslog.  To turn off the log spam, use:

```

sudo sh -c "echo 0 > /proc/sys/vm/block_dump"

```

---

### Post by LiquidRain on 2009-02-25
Thanks for that.  It appears to be xfc4-session, as it's the only process accessing dm-4.

```
[whole lotta gibberish]
[259033.891363] xfce4-session(8077): WRITE block 0 on dm-4
[259033.893126] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[259033.893133] ata2.00: waking up from sleep
[whole lotta gibberish]
```

Now to figure out why xfce4-session is hitting that disk.

---

