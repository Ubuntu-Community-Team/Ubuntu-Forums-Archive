---
title: "The Gnome That Wouldn't Die"
date: 2007-01-23
forum: Desktop Environments
---

### Post by GedB on 2007-01-23
I've switched to Xubuntu, and everything went well apart from one problem: I have a Gnome   session that just won't die.

When I log on to my main user, it always picks up the old Gnome session, without the panel.

I can F2 and run gnome-panel, and everything works except the log of button.  When I click on this it kills the panel, but not the session.

I can ctrl-alt-bksp out of the session, but it always goes back in.

If I ctrl-alt-del and select new session I can start a second Xubuntu session, but I always have to have the Gnome session running first.

How can I kill the gnome?

I installed Edgy from the download and then installed xubuntu through apt.  I've installed all updates.

I'm running on an old x86.

I'd appreciate any help anyone can offer.



Ged.

---

### Post by forger on 2007-01-23
how about:
```

sudo /etc/init.d/gdm stop
sudo /etc/init.d/xdm restart

```

---

### Post by GedB on 2007-01-24
The one thing I've loved about switching to Ubuntu from Windows is that everything seems to be solved in two lines beginning with sudo.

In windows you always had to give long descriptions of go to this screen, now go to that screen.

Many thanks,

Ged.

---

