---
title: "Gnome Bug? .thumbnails folder too sensitive?"
date: 2008-03-07
forum: Desktop Environments
---

### Post by ibuclaw on 2008-03-07
Hi, small question, but has anyone noticed how sensitive the .thumbnails folder in your home drive can be?

I stumbled across it by accident the other week, I've used gutsy since it first came out, I was cleaning up some unwanted files, and found that the folder had some 150,000 files which added up to around 1.2GB in size.

I removed it, as posts up on the forums say that it is not harmful too, but its been less than a week, and already its back up to 300MB in size.

Now a small peek round and it's practically full of junk that I can't think of a reason for it's caching.
Such as program icons, banners, what appear to be internet items from webpages and file icons.
[EDIT]
Not to forget the many thousands of "blank" 234 byte sized png's. entitled "c6d52e5afca892506cd7881adb618bbd" or something or another...
[END]

Now file icons I understand why caching them to a folder for quick load COULD be efficient (though considering Linux's reputation for "hard-to-frag" surely whichever file you go for, it'll take the exact same time to get...just hypothesizing), but apart from previews of visual files (bitmaps, videos, vectors). Why would it be an apparent necessity to store everything else? and why has it an aggressive algorithm to store everything that apparently is loaded in anything?

Replies or thoughts would be appreciated.

Iain.

---

### Post by spin2cool on 2008-03-07
Nautilus is one of the programs that aggressively caches thumbnails, and there is a way to disable it, IIRC.  Some google searches should turn up that method (probably using gconf-editor).  Other programs, like GQview, for example, have a preferences dialog that lets you turn caching of thumbnails off.

You're right that it's a trade off. Disk space is cheap, and processor speeds are more limited., so right now, the default is to cache everything. 

One more idea - you could set up a cron job to remove all thumbnails older than a certain date, if disk space is a problem for you.

---

### Post by ibuclaw on 2008-03-07
> **spin2cool said:**
> you could set up a cron job to remove all thumbnails older than a certain date, if disk space is a problem for you.

wrote a code that would do just that...

```
0 20 * * * root find /home/*/.thumbnails -type f -atime +6 -exec rm '{}' \;
```


Basically everyday at 2000hours (8pm) it checks for files that haven't been used for seven days (+6).

I've stored it in /etc/cron.d as "thumbnails"

In theory it should work, right?

---

