---
title: "Another two new problems"
date: 2006-09-23
forum: Desktop Environments
---

### Post by Rhapsody on 2006-09-23
I just recently tried to install Sound Converter (in order to convert some files over to FLAC) and although it seemed to install correctly through Adept, all I get when I try to start it (through a terminal command) is:

```
Traceback (most recent call last):
  File "/usr/bin/soundconverter", line 42, in ?
    import gtk.glade
ImportError: No module named glade
```

This is annoying, but not particularly worrying. What has me more worried is that at about the same time, my system began freezing at shutdown. It reaches the point where it tries to terminate the Common Unix Printing System, then it just stops. Cutting the power successfully shuts the system down and Kubuntu starts up next time like nothing ever happened, but this is clearly not how it's supposed to work.

Neither of these are particuarly urgent, but I'd like to nip them in the bud before either can become a serious problem for me.

---

### Post by ayoli on 2006-09-23
for your first problem you may need ```
sudo aptitude install python-glade2
```
dunno for second one.

---

### Post by Rhapsody on 2006-09-23
After tracing a whole string of problems (which all seemed to lead back to *flashplugin-nonfree*, which didn't want to update, so I ended up removing it) I eventually ran that and it seemed to do the job. All of these problems seemed to start around the time *flashplugin-nonfree* stopped wanting to update, so I'll see if it fixes the shutdown problem too.

---

