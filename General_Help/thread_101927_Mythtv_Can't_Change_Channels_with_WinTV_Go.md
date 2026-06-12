---
title: "Mythtv: Can't Change Channels with WinTV Go"
date: 2005-12-10
forum: General Help
---

### Post by shewbox on 2005-12-10
I have an old Hauppage WinTV Go card I bought about 6 years ago.  I decided to give Mythtv a try with it, but I've hit a bit of a snag.  Following some guides found on this forum and elsewhere, I managed to get Mythtv installed, setup, and running.  However, when running mythfrontend, watching live TV is stuck on one channel, and this channel is always the one I was watching last in XawTV.  When trying to change the channel, I get this message in terminal:

```
QDateTime::fromString: Parameter out of range
```

And it stays on the current channel.  I believe I have the channels setup correctly and I have run mythfilldatabase, so if I look at the program guide, it looks correct.  If I schedule a recording using the program guide, it also does not work, although I'm not sure of the error message in this case.  I'm not sure what I'm doing wrong here.  Perhaps I didn't get the card setup exactly right?  Any suggestions?

---

### Post by GameGod on 2005-12-10
Try asking on the mythtv-users mailing list, or searching through the archive here:

[http://www.gossamer-threads.com/lists/mythtv/users/]("http://www.gossamer-threads.com/lists/mythtv/users/")

---

### Post by shewbox on 2005-12-11
It is fixed!  Sifting through the forum linked to above, I discovered several other people describing the same problem.  One suggestion was to clear out the channel settings, reget them, stop mythbackend, run mythfilldatabase again, then restart mythbackend.  After doing this, I now have no problems changing channels;  it all works smoothly.

---

