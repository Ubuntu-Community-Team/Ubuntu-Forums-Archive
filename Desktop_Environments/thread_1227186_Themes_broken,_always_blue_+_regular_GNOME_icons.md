---
title: "Themes broken, always blue + regular GNOME icons"
date: 2009-07-30
forum: Desktop Environments
---

### Post by Aaron44126 on 2009-07-30
I'm having a problem where, no matter which theme I select in the "Appearance" control panel, I have blueish Window borders and the default GNOME icon set.  It looks pretty ugly to me.  Anyone have any ideas on how to fix this?

I rebooted yesterday after the kernel update, and this problem started.  However, I've tried booting with the old kernel (2.6.28-13) and the problem is still there, so I don't think the kernel update actually broke anything.

Thanks!

[IMG]http://aaron-kelley.net/wp-content/uploads/2009/08/broken-theme.png[/IMG]

---

### Post by Dullstar on 2009-07-30
I ran into a similar problem when I added KDE, but it was an easy fix.  Sounds like the method I used won't work for you.  Besides, my problem was getting the normal GNOME folders *back*.

Even if I put my theme up somewhere, it wouldn't help you, would it?  I could make a modification up and see if I could upload the theme somewhere.

---

### Post by Aaron44126 on 2009-07-30
Thanks for your reply, but I am also not sure if that would help.  My problem is, I can't get the icons or the "general look" (except window borders) to change at all, no matter which theme or icon set I choose.  So, I don't think installing another theme would help.

---

### Post by Dullstar on 2009-07-30
Well, do you want to try it?  Like I said, I'd make a modification to it to use the folder icons you want.

---

### Post by Aaron44126 on 2009-07-30
Well, sure.  I'll try anything, I suppose.  :-P

---

### Post by Dullstar on 2009-07-30
If I can figure out where the themes are stored. =P

---

### Post by tjok on 2009-08-01
> **Aaron44126 said:**
> I'm having a problem where, no matter which theme I select in the "Appearance" control panel, I have blueish Window borders and the default GNOME icon set.  It looks pretty ugly to me.  Anyone have any ideas on how to fix this?

I rebooted yesterday after the kernel update, and this problem started.  However, I've tried booting with the old kernel (2.6.28-13) and the problem is still there, so I don't think the kernel update actually broke anything.

Thanks!


I got this problem today as I did an update. The updates did not include kernel update (actually running older kernel due to wlan issues). My session worked ok even after the updates, but when my wife logged in her desktop looked just like yours (also tested another account). After logout and login I got the same problems (and also Gnome power manager complaining about missing schema).

I'm running 8.04 LTS, I quess you are running newer version based on kernel release. But the problem feels just the same!

My update included just these packages:
[LIST]
[*]libgvfscommon0
[*]gvfs-backends
[*]gvfs
[*]gvfs-fuse
[*]libnautilus-extension1
[*]nautilus-data
[*]nautilus
[/LIST]

   Toni

---

### Post by Aaron44126 on 2009-08-01
Thanks for your message!  I am glad that I am not the only one with the problem.

I think an update caused it too.  I have no idea which one.  I didn't notice until a kernel update came along and made me reboot (and thus log out and log back in).

I've tried creating a new account, and it had the problem too.  So, it's not an account-specific thing.

Since this is on a machine that I don't use for much anything except remote backup, I am quite sure that I didn't do anything to cause the problem.  Pretty much just an update left to blame... *anyway*, since this is a machine that I don't use much, I've kind of given up on the problem for now.  I don't know what to do, since I couldn't find any reference to a similar problem while Googling.  But please post back if you figure anything out, or have any leads...

Thanks again!

---

### Post by tjok on 2009-08-01
I found it!!! :D

After googling I run into this old thread: [http://ubuntuforums.org/showthread.php?t=810176](http://ubuntuforums.org/showthread.php?t=810176)

From there I tried this hack:
```

cd /usr/share/gconf/schemas/
sudo /usr/sbin/gconf-schemas --register *.schemas

```

After that reboot is needed (logout + login won't do it)

It looks like something in the update fried all the gnome schemas.

8.04 LTS is now back in business.

   Toni

---

### Post by Aaron44126 on 2009-08-01
No luck, still broken here.  :-(

---

### Post by Dullstar on 2009-08-01
There *was* a very recent update...

Does that one do anything?

---

### Post by Aaron44126 on 2009-08-01
I'm not sure what you mean.
I am fully up to date, and it is broken.

[Edit, Aug 4]
[Looks like this may be caused by FreeNX...](http://ubuntuforums.org/showthread.php?t=1231195)

---

### Post by Aaron44126 on 2009-08-04
Fixed.  gnome-settings-daemon was crashing, see [this bug](https://bugs.edge.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/199245).

Run gconf-editor.
Navigate to /apps/gnome_settings_daemon/plugins/keyboard.
Uncheck the "Active" box on the right.
Log out and log back in.

This disables the "keyboard" plug-in for gnome-settings-daemon.  I'm not exactly sure what this plug-in does at the moment, but my keyboard is still working fine.  :-P

---

