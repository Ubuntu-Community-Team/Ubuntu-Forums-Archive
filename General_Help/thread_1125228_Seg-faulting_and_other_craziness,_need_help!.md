---
title: "Seg-faulting and other craziness, need help!"
date: 2009-04-14
forum: General Help
---

### Post by firefox05 on 2009-04-14
Well, for some reason Linux hates me, especially ubuntu.  I can't get any visual effects to work for the life of me, it's being difficult with power settings, torrents, pretty much anything outside the basic package I try to do....  But enough of my bellyaching.  On to the issue at hand.

I randomly got a seg-fault with Thunderbird yesterday, and since then things have gone to hell in a handbasket.  I couldn't replace the program because I got an error (don't have that one saved, but I remember it having to do with a character not allowed somewhere.)  But today the system has been randomly locking up and I keep getting this error when I try to launch synaptic:
"E:Malformed 3rd word in the Status line
E:Error occurred while processing x11proto     composite-dev (UsePackage1)
E:Problem with MergeList /var/lib/dpkg/status
E:The package lists or status file could not be parsed or opened."

Please help guys, this is my second go of Ubunutu 8.10 and I really would like to not have to reload the OS again!

Details: IBM T30 hardware, Ubuntu 8.10, no real serious mods done other than some stuff trying to get visual effects to work.

PS:  Oh yeah, and FireFox is crapping bricks over something or other, keeps showing me background code for Java and HTML stuff.

---

### Post by Denestria on 2009-04-14
The /var/lib/dpkg/status file was probably corrupted during an update.  You can try to back it up and then replace it with /var/lib/dpkg/status-old.  Or open /var/lib/dpkg/status with a text editor, search for the broken package (x11proto) and correct the entry.  If you post the /var/lib/dpkg/status file we can have a look at it and see what the problem is exactly.

---

### Post by firefox05 on 2009-04-15
> **Denestria said:**
> The /var/lib/dpkg/status file was probably corrupted during an update.  You can try to back it up and then replace it with /var/lib/dpkg/status-old.  Or open /var/lib/dpkg/status with a text editor, search for the broken package (x11proto) and correct the entry.  If you post the /var/lib/dpkg/status file we can have a look at it and see what the problem is exactly.



Alright, well that sheds some light on things.  When I open the status file, it looks as though the characters are in chinese.... odd, I thought.  And when it gets done fully loading the file, the text editor crashes.  However, status-old seems to be just fine.  What is the best means to go about replacing status with status-old (as I can't modify them by browsing to them since I'm not root and all that.) and what will that do to my system???

For the record, opening status with sudo gedit in terminal yields just a blank document, but it doesn't crash. status-old ALSO shows up blank when opened this way, even though I can see the text fine when browsing to it through the file tree.

Tried to upload both files, but got 'invalid' errors. I can e-mail them however, if someone thinks that would be beneficial.

Thanks so far guys!

---

### Post by Denestria on 2009-04-15
I can't promise it will fix things but we can try to replace it with the old one unless someone else has a better idea.

```

sudo cp /var/lib/dpkg/status /var/lib/dpkg/status.backup
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status

```

Then you can update or remove the packages giving you trouble.

---

### Post by firefox05 on 2009-04-18
It worked, thank you!

---

