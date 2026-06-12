---
title: "xfce4-notifyd - not starting after upgrade to 18.10"
date: 2018-10-30
forum: Desktop Environments
---

### Post by BloodyIron on 2018-10-30
I just upgraded 18.04 -> 18.10, and I use XFCE4 as my main desktop.

I use my mouse to (un)mute sound and change volume regularly, and part of that involves the xfce4-notifyd.

After upgrading I noticed the service was not starting, and I wasn't sure why.

After some digging, I located that the service exists at:

```
/usr/lib/x86_64-linux-gnu/xfce4/notifyd/xfce4-notifyd
```

Initially, I ran it as root, and it started throwing errors, so I thought something was wrong. I tried chmodding 0770 for .ICEauthority in my user's profile (/home/username/.ICEauthority), but that didn't resolve it.

Then I realised this probably should be running as my user, and so I ran it as my user, and it's "working".

But, in my travels, I also found another relevant post ( [https://forum.xfce.org/viewtopic.php?id=12213](https://forum.xfce.org/viewtopic.php?id=12213) )

It seemed relevant since it talks about dbus, and I was seeing dbus errors when I was running at root, and the file it talks about editing, did _not_ point to the xfce4-notifyd, it pointed to another one who's name escapes me (I've since removed it, lol)

File is at:

```
/usr/share/dbus-1/services/org.freedesktop.Notifications.service
```

And I change the "Exec=" line to point to the earlier xfce4 file ( /usr/lib/x86_64-linux-gnu/xfce4/notifyd/xfce4-notifyd )

Now, I'm getting the functionality I want... by manually running this file each time I login as my user. But I want to go back to the convenient way where the system runs it for me.

I know I could set it up as a startup process, but that seems hacky, and I suspect the dbus notification configuration thing is the better way to go about it, but I'm not sure what I'm doing wrong here.

Any of you able to point me in the right direction please? :)

---

### Post by BloodyIron on 2018-10-31
Bump

---

### Post by BloodyIron on 2018-11-07
Does anyone ever use these forums? Like really?

---

### Post by BloodyIron on 2018-11-11
Okay, so the solution was ludicrously simple

* systemctl disable bluetooth

Seriously, bluetooth was hanging at login and disabling the service fixed it. I don't have any bluetooth devices or radios, so it was probably searching and timing out.

I've already filed a bug report. Hope this helps someone, because these forums, nobody responds it seems :/

---

