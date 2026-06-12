---
title: "Trackerd eating my processor time"
date: 2008-04-10
forum: Desktop Environments
---

### Post by josef.sabl on 2008-04-10
Hello,

everytime I boot to Ubuntu, there is trackerd process that starts to eat 100% of my processor time. It has nice priority, but it also never seems to finish what it is working on.

What it is? What can be the problem? And what to do about it?

Thanks for any advice.

---

### Post by kpkeerthi on 2008-04-10
Yeah.. that was annoying. Unfortunately, I couldn't do anything about it. Same was the case with beagle. Another annoyance was that the index file tracker/beagle created was about 300 MB.

So I uninstalled them both and switched to the standard gnome file search (Places -> Search). I'm happy with what it finds albeit somewhat slow in finding results. But that is OK for me.. most of time I know where my files are organized and there is also nifty **find** command that I always use wherenever I'm in a terminal.

---

### Post by Nameless_one on 2008-04-10
Trackerd is the daemon of MetaTracker, an indexing, tagging and searching program. It usually runs well, although having used it since 0.5.4 or somesuch, I think memory leaks and 100% processor usage aren't so rare. 

Now, there are two things you can do. If searching is not that important to you, as with kpkeerthi, you can uninstall it completely. Otherwise, you might want to remove it and install the latest version from source. 

On the other hand, if trackerd was installed recently, and you have a large storage with lots of files, it just might be indexing your stuff. You can check this by running the following command in a terminal:
```
$ tail -f ~/.local/share/tracker/tracker.log
```

This is tracker's log. If ever few seconds or so, a newline appears, which says "Indexing #13500" or something along those lines, then it's indexing. 

More information on the [official site](http://www.gnome.org/projects/tracker/).

---

