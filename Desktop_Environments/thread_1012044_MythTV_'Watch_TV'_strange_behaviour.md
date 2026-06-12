---
title: "MythTV 'Watch TV' strange behaviour"
date: 2008-12-15
forum: Desktop Environments
---

### Post by voteforpedro on 2008-12-15
Got some odd behaviour with MythTV when choosing 'Watch TV'. All is configured correctly. If I launch MythTv from the application menu and choose 'WatchTV', the screen goes blank for a few seconds then returns to the menu. If I launch mythfrontend from a shell I get:

```

2008-12-15 18:08:32.770 TV: Attempting to change from None to WatchingLiveTV
2008-12-15 18:08:32.770 Using protocol version 40
2008-12-15 18:08:33.831 GetEntryAt(-1) failed.
2008-12-15 18:08:33.832 EntryToProgram(0@Thu Jan 1 01:00:00 1970) failed to get pginfo
2008-12-15 18:08:33.833 TV Error: LiveTV not successfully started
2008-12-15 18:08:33.833 TV Error: LiveTV not successfully started
2008-12-15 18:08:33.874 TV: Deleting TV Chain in destructor

```

Now, if I then do:

```

$ sudo /etc/init.d/mythtv-backend stop
$ sudo /etc/init.d/mythtv-backend start

```

...I get the same problem. Now, if I do...

```

$ sudo /etc/init.d/mythtv-backend stop
$ mythbackend

```

...i.e. I launch the backend from a shell, it works fine and I can watch TV using my DVB-C card.

Why is this?

---

### Post by stevetree on 2009-01-24
This is almost certainly too late to help the original poster, but just in case someone else runs across it in a search as I did...

I had the same behavior when I suddenly couldn't watch or record.  It turns out I had just added another storage directory, but it was owned by my user rather than mythtv:mythtv.  This would cause the backend to work when it was running from the command line (presumably as the logged-in user), but not when it runs as a startup process, as user mythtv.  

When I changed the owner and group of the new storage directory to mythtv, it worked.

---

### Post by DemonSpectre on 2009-01-28
Stevetree-

Dude!  Thanks a million!  I couldn't for the life of me figure out why MythTV stopped working, but your fix worked perfectly.  Many thanks.

---

