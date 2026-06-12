---
title: "Hide specific paths/file types from Recent Documents"
date: 2009-02-07
forum: General Help
---

### Post by efjen on 2009-02-07
Hello.

I don't want certain documents to show up in the Recent Documents menu in Gnome. Is there any way to restrict the documents that are shown there by path and file type? For example I would like exclude documents in ~/Private from the menu. I'd like the same for certain file types, e.g. any *.mp3 file. Is this possible? Or something similar?

Thanks!

---

### Post by dowcet on 2010-07-17
Me too. I guess no solution has been found?

---

### Post by draki on 2010-08-09
I'd be interested in this as well... 

Anyone have any ideas how to blacklist certain folders or file types - I find my recent documents gets cluttered :(

---

### Post by SlugSlug on 2010-08-09
humm I dnt know how to black list certain files - but you can disable the whole think by deleting 
.recently-used.xbel in you home dir and then creating a folder called .recently-used.xbel

---

### Post by dino99 on 2010-08-09
use gconf-editor to disable it (no partial solution known)

---

### Post by cong06 on 2011-05-09
I feel like this is more important than ever with Unity...

---

### Post by stimpie on 2011-05-09
You could install gnome activity journal which contains an option to blacklist certain directories.

[http://www.andersaaberg.dk/?p=94](http://www.andersaaberg.dk/?p=94)

---

### Post by cong06 on 2011-05-09
I installed like the link said, but I'm getting this error:

```

isaac@bohr:~$ gnome-activity-journal 
Traceback (most recent call last):
  File "/usr/bin/gnome-activity-journal", line 94, in <module>
    from src.main import PortalWindow
  File "/usr/share/gnome-activity-journal/src/main.py", line 30, in <module>
    from activity_widgets import MultiViewContainer, TimelineViewContainer, ThumbViewContainer
  File "/usr/share/gnome-activity-journal/src/activity_widgets.py", line 35, in <module>
    from store import ContentStruct, CLIENT
  File "/usr/share/gnome-activity-journal/src/store.py", line 504, in <module>
    STORE = Store()
  File "/usr/share/gnome-activity-journal/src/store.py", line 367, in __init__
    days_population = ZeitgeistDBusInterface().get_extension("Log", "journal/activity").GetHistogramData()
  File "/usr/lib/pymodules/python2.7/zeitgeist/client.py", line 108, in __getattr__
    raise TypeError("Unknown method name: %s" % name)
TypeError: Unknown method name: GetHistogramData

```

---

### Post by andersaaberg on 2011-11-14
Sorry cong06 and others, the guide on my blog that was posted was for Ubuntu 11.04 (the blacklist option is now removed from gnome-activity-journal in 11.10 and the PPA that I referenced does not work for 11.10).

Good news is that I have made a new guide for Ubuntu 11.10, which should also make it much easier to fix the problem: [http://www.andersaaberg.dk/blog/blog/2011/unity-dash-privacy-at-ubuntu-11-10-oneiric-ocelot-hide-porn-folder/](http://www.andersaaberg.dk/blog/blog/2011/unity-dash-privacy-at-ubuntu-11-10-oneiric-ocelot-hide-porn-folder/)

Please give me a comment if something is wrong with my guide :)

---

