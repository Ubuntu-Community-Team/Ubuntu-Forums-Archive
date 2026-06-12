---
title: "GStreamer plugin"
date: 2006-07-28
forum: Desktop Environments
---

### Post by Branta on 2006-07-28
How do I install the GStreamer LAME plugin?

I have done the preferences per  the manual but how do I **install the plugin so I can play MP3?**

TU,

Bob

---

### Post by Jagot on 2006-07-28
You don't need the LAME plugin to play MP3's - that is for encoding.

If you're using Dapper then it is gstreamer0.10-plugins-ugly, and Breezy it is gstreamer0.8-mad.

So, in Dapper, from the Terminal:

```
sudo aptitude update && sudo aptitude install gstreamer0.10-plugins-ugly
```

Or in Breezy:

```
sudo aptitude update && sudo aptitude install gstreamer0.8-mad
```

Both of those are in the universe repo so you will have to have that enabled - see here to do so:

[http://psychocats.net/ubuntu/sources.php](http://psychocats.net/ubuntu/sources.php)

---

### Post by Branta on 2006-07-29
Dapper did it.

Everything was set on ubuntu.  All I did was```
sudo aptitude update && sudo aptitude install gstreamer0.10-plugins-ugly
```

Thanks for correctly answering my query with the correct code!

--- Bob ---:p

---

