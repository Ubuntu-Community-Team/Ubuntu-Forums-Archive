---
title: "Help Me Understand Tracker?"
date: 2007-11-01
forum: Desktop Environments
---

### Post by flickerfly on 2007-11-01
I have a known file on my Desktop that I want tracker to find for me. I click the squiggly thing up by the clock and type the name of the file minus the extension (wiltres). It suggests "Search for wiltres with Tracker Search Tool" so I click on that. It pops up a window that I click "Find" on, but nothing happens. It simply says "Your search returned no results."

I tried putting by Desktop in the "Watching" area of the Tracker configuration tool, but that hasn't improved matters any.

I get the same results if I search for 'etc', 'doc' or 'src' or other things that should be littered around my file system. Why can't I find anything? :confused:

---

### Post by bingoUV on 2007-11-01
How long has it been since it started "tracking" ? In my experience it initially needs a lot of time (many hours for hundreds of MB) to really give a result. Then if you create a new file in the tracking area, it would immediately search by its contents too.

---

### Post by flickerfly on 2007-11-01
Is there something I have to do to start it tracking? I assumed it was on by default. Is there a place to check this sort of thing out?

---

### Post by bingoUV on 2007-11-02
does the following command list anything?
```

ps -aef | grep tracker

```

If tracker is running, 1 or 2 lines of "trackerd"  should come as a result.

---

### Post by DouglasCaixeta on 2007-11-03
Hi,

I don't know if my Tracker is running.

Here is the output of the command ps -aef | grep tracker.


```
douglas  10358     1  0 Nov03 ?        00:00:39 /usr/bin/trackerd
douglas  15034     1  0 00:39 ?        00:00:00 tracker-preferences
douglas  15313 15155  0 00:50 pts/1    00:00:00 grep tracker
```

Running?

I can't find any files!!

I change some settings in Preferences > Performance:

Maximum amount of text to index: 10000Kb
Maximum number of unique words to index: 20000 Kb

What's wrong?

---

### Post by bingoUV on 2007-11-04
It seems to be running.

Is the file you are trying to find in your home directory? I think by default tracker indexes only the home directory of the user.

---

### Post by DouglasCaixeta on 2007-11-04
Yes, it is in the home directory.

---

### Post by ayoli on 2007-11-04
I have the same issue, tracker deamon runs and had to index my home and other folders I've added, but the search tool can only find results in my evolution mails.

---

### Post by dabugas on 2007-11-04
Same problem here.

The following thread seems promising:
[http://ubuntuforums.org/showthread.php?t=583134&](http://ubuntuforums.org/showthread.php?t=583134&)

---

