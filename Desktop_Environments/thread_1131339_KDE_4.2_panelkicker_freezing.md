---
title: "KDE 4.2 panel/kicker freezing?"
date: 2009-04-20
forum: Desktop Environments
---

### Post by mma8x on 2009-04-20
i've had my kicker/panel/whatever it's now called start freezing up at random times.  weird, since i haven't upgraded/changed anything in a while, and it had been stable before this.  applets/clock/etc don't move, and clicking anywhere on it doesn't do anything.  the desktop (or whatever it's now called) is also frozen.  killing/restarting plasma gives this as the last few lines of output:

```
QCoreApplication::postEvent: Unexpected null receiver
plasma(8963): Communication problem with  "plasma" , it probably crashed.
Error message was:  "org.freedesktop.DBus.Error.NoReply" : " "Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken." "
```

killing the xserver and restarting doesn't help, nor does logging out of kde and logging back in.  any ideas? oh yeah, using hardy.

---

### Post by inobe on 2009-04-20
i really don't have a suggestion except i don't think it's a good idea upgrading kde to 4.2 with kubuntu 8.04.

the upgrade procedure doesn't mention 8.04 once !

[http://www.kubuntu.org/news/kde-4.2](http://www.kubuntu.org/news/kde-4.2)

---

### Post by gregor171 on 2009-04-20
My solution was no KDE 4, but still thinking of changing to Ubuntu (not Kubuntu). Freezing of Firefox, Eclipse and others. Becomes slow after a while.

---

### Post by inobe on 2009-04-20
using kubuntu 8.10 x86 64bit with kde 4.2.2 without any hiccups.

---

### Post by mma8x on 2009-04-21
> **inobe said:**
> using kubuntu 8.10 x86 64bit with kde 4.2.2 without any hiccups.

whoops.  i am using a 64 bit intrepid install.  they start to blend together after a while i guess...realized that jaunty is just 2 days away.  guess i might as well update then and see what happens (although i know it will further break my system, and i'll spend a few hours trying to get it back the way it was.  sigh.)

---

