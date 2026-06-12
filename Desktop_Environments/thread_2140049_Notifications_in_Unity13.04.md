---
title: "Notifications in Unity/13.04"
date: 2013-04-28
forum: Desktop Environments
---

### Post by Cammy on 2013-04-28
After jumping between desktops in 12.x, I finally decided to give Unity a solid try, and it's kind of grown on me.  But in 13.04, we've lost the system tray, which is fine, except for one thing.  I use pidgin a lot, and before with the tray/whitelist, I had that icon that flashed when I had an IM.  Now, without the tray/whitelist, I have no way to know that I have an IM.  I've read something about "indicators" but I can't figure out whether that's something that's in the works, or something that's available.

Do I have any options for being notified of IMs, or other app activity?

---

### Post by kostkon on 2013-04-28
You should be getting a notification every time there is a new message.

Also, add your accounts in Online Accounts, even if Pidgin doesn't use them, not sure about that, and then the messaging indicator icon will appear in the tray, if you don't have it already.

The icon will turn blue every time there is a new message and the new messages will be listed there; you can click on them to bring up (even if you've closed it) the window that contains the new message.

---

### Post by Cammy on 2013-04-28
Well the thing is, there's no pidgin (or yahoo) option in Online Accounts.  Just Facebook, Flickr, Google, Windows Live, and identi.ca.

---

### Post by Frogs Hair on 2013-04-28
Strange , I installed pidgin after seeing your thread because hadn't done it yet in 13.04 . I see Yahoo in online accounts (scroll to bottom) and the message menu appears under envelope on the panel , but haven't received a notification yet. I can't seem to add to online accounts, but I may have to log-out and in or restart because I just installed.

---

### Post by Cammy on 2013-04-28
I did a "flying upgrade", so I think what I'll probably do is install 13.04 from scratch (which is a total bore!).  There are too many funkinesses that I think are a result of upgrading instead of doing a clean install.

---

### Post by Cammy on 2013-04-29
I finally did a 13.04 reformat/reinstall from USB, and for a few minutes, the envelope icon up on the taskbar (next to the battery icon) would turn blue on incoming IMs.  Then, it inexplicably stopped.  Any ideas on how to get it working again?  I think somewhere along the line I removed Empathy (I don't use it) but I've since put it back to no avail.

---

### Post by kostkon on 2013-04-29
> **Cammy said:**
> I finally did a 13.04 reformat/reinstall from USB, and for a few minutes, the envelope icon up on the taskbar (next to the battery icon) would turn blue on incoming IMs.  Then, it inexplicably stopped.  Any ideas on how to get it working again?  I think somewhere along the line I removed Empathy (I don't use it) but I've since put it back to no avail.
You could check what packages were removed when you uninstalled empathy.

The easiest way to do this is to open the software centre and press the History button. Another way is to use the System Log utility to open the */var/log/dpkg.log* log file; or by simply giving
```
gedit /var/log/dpkg.log
```
in the terminal.

---

### Post by Cammy on 2013-04-30
I ended up doing a fresh install, then adding my yahoo account under "Online Accounts".

In the end, I needed a Pidgin plugin called pidgin-libnotify.  It's not perfect (I don't really need the conversation text appearing in bubbles on my desktop) but it does turn that little envelope blue, and that's what I needed.

---

