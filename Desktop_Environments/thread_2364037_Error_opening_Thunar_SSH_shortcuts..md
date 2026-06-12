---
title: "Error opening Thunar SSH shortcuts."
date: 2017-06-17
forum: Desktop Environments
---

### Post by Brandon_MacEachern on 2017-06-17
For some reason, if my laptop has been on long enough (like a couple of days), it's unable to follow one of the links in my Thunar sidebar, which simply goes to an SSH server.  The error it gives me however makes no real sense, and nothing shows up in the logs regarding this.

[http://i.imgur.com/Buu7pdh.png](http://i.imgur.com/Buu7pdh.png)

Thing is, if I reboot, it works fine.  In fact, it's only the top link that fails, all of the other SSH links work just fine..  The server works fine if I type the same exact shortcut manually into the location bar.  It's specifically only to do with the Thunar shortcut.

I also showed in the screenshot how the gtk bookmarks file is laid out.  Should be rather simple.  I don't know if logging out and logging back in solves it, but a reboot definitely does.

Xubuntu 17.04, 64-bit..  As of right now it's up to date.

---

### Post by Brandon_MacEachern on 2017-06-19
Just checked.  Logging out and back in does fix it also, until it happens again.

So I'm still not sure what's causing it, and why it's only one of the servers.

---

### Post by Brandon_MacEachern on 2017-06-21
Appears Nemo has the same exact issue from several years back too.

[https://github.com/linuxmint/nemo/issues/678](https://github.com/linuxmint/nemo/issues/678)

---

