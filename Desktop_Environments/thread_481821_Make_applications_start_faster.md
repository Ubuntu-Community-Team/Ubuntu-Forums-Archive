---
title: "Make applications start faster?"
date: 2007-06-22
forum: Desktop Environments
---

### Post by W3ird_N3rd on 2007-06-22
I'm running (well my mother is but I maintain the machine) Ubuntu 7.04 (with Gnome) 32bit x86. System specs: Athlon 64 3000+ S939, 1GB PC3200, 40GB Samsung 2,5" laptop drive with converter on desktop nForce4 SLI mainboard.

After a cold boot, it takes a while to start an application. Firefox about 6-7 seconds, Kaffeine (after making kdeinit load directly on startup, without kdeinit on boot it takes 20 secs!) takes 7 seconds, any application with wine 8 seconds. However, if I close the application after it was started once, and start it again, it will load in about 2 seconds. That's valid for Firefox, Kaffeine and Wine: 2 seconds the second time I run it.

Considering the harddrive (laptopdrives are always a bit slower) these speeds are mostly normal I think, but it would be nice if they were faster after the cold boot. Often my mother doubleclicks a program on the desktop, gets impatient after 5 seconds because there is no indication whatsoever that anything is actually loading, doubleclicks it again, and 3 seconds later Word (on Wine) is started twice and complaining normal.dot went bonkers.

Now I heard about readahead which should be able to solve this problem - but I don't get it! There's no man-page and I couldn't find much on this forum either. I found this: [http://ubuntuforums.org/showthread.php?t=49068](http://ubuntuforums.org/showthread.php?t=49068) but that's not very informative.

I tried adding /usr/share/firefox and /usr/lib/firefox to /etc/readahead/boot but that doesn't make any difference. I want to readahead Firefox, Wine and Kaffeine on boot. Who can tell me how?

---

### Post by tgm4883 on 2007-06-23
The reason it starts faster the second time is that it is already loaded in RAM.

---

### Post by jackmc on 2007-06-23
I did [this]("http://http://ubuntuforums.org/showthread.php?t=1971"), and openoffice now opens in 3 seconds from when I click the launcher, a fair bit quicker than it was...

---

### Post by vexorian on 2007-06-23
The aCtual URL : [http://www.ubuntuforums.org/showthread.php?t=1971](http://www.ubuntuforums.org/showthread.php?t=1971)

---

### Post by W3ird_N3rd on 2007-06-23
> **tgm4883 said:**
> The reason it starts faster the second time is that it is already loaded in RAM.
I know. That's why I want to load some applications in memory during boot with readahead.
> **jackmc said:**
> I did [this]("http://http://ubuntuforums.org/showthread.php?t=1971"), and openoffice now opens in 3 seconds from when I click the launcher, a fair bit quicker than it was...
I know about Prelink. But there are two problems: according to [http://ubuntuforums.org/showthread.php?t=74197](http://ubuntuforums.org/showthread.php?t=74197) it shouldn't be used for 7.04 ("UPDATE 1/2/07: Prelink is no longer necessary in Feisty. Feisty uses a new linking mechanism called DT_GNU_HASH which dramatically speeds up the linking process without the need for continuously running this prelink program. Again, prelink is NOT useful starting from Feisty") and I want to just "cache" the three most-often-used applications on startup. No others. These are also the only applications that I gave icons on the desktop, with programs started from the menu it's less likely my mother will try to start them twice because she gets the response of the menu disappearing after starting something there.

---

### Post by W3ird_N3rd on 2007-06-24
Okay, I'm a little further now.

In synaptic, when you right-click a package, you can get a list of installed files. I copied that list and tried to load it with readahead-list. That didn't work, because readahead-list stops when it finds a directory or other file it somehow doesn't like in the list, hence nothing is cached. After removing the directories from the list, it did work. Loading times now:

wine 6 secs
firefox 3 secs
kaffeine 5,5 secs

So Firefox gained a lot, kaffeine a little and wine very little. There is something else strange: the default "desktop" file in /etc/readahead doesn't fully load with readahead-list. There apparantly are some invalid entries in it. I removed those.

Shouldn't readahead-list just carry on with the rest of the file if it finds an invalid entry? The "boot" file also contained several invalid entries, I've removed them and I didn't time it, but for my feeling the computer boots up faster now!

I've attached my filelist to load firefox, kaffeine and wine. If you want to use it, you can either append it to /etc/readahead/boot or /etc/readahead/desktop or add "readahead-list /home/user/readahead-firefoxkaffeinewine.txt" (or whatever path you use) to the programs that have to be loaded at startup in preferences>sessions.

[edit]I got Kaffeine down to 4,5 seconds now. Instead I now attached the 3 filelists for firefox, kaffeine and wine. I'll just leave everything as it is now. Someone suggested the idea of adding an activity-meter to the panel, and I've done that. I'll teach my mother to look at it before doubleclicking something a second time.

---

