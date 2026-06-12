---
title: "Nautilus hangs on folders with active downloads"
date: 2007-04-08
forum: Desktop Environments
---

### Post by brsseb on 2007-04-08
Hi

Suddenly (perhaps after the latest xorg-updates?) Nautilus freezes (locks up, uses 100% of my CPU and I must kill it) when i enter a folder where a file is being downloaded. 

Basically, evertime I enter my BitTorrent download folder (where unfinished video files are being downloaded), nautilus freezes. 

Im running Ubuntu Dapper 6.06, kernel 2.6.15-28.686, on a Dell M1210 1,86GHz CoreDuo, 2GB.

Everything else seems to work ok. 

Does anyone have the same issue?

---

### Post by heimo on 2007-04-08
In Feisty with latest updates, no I don't. Maybe it's about preview feature? Have you tried turning off preview in [Nautilus->]Edit->Preferences->Preview?

---

### Post by brsseb on 2007-04-08
> **heimo said:**
> In Feisty with latest updates, no I don't. Maybe it's about preview feature? Have you tried turning off preview in [Nautilus->]Edit->Preferences->Preview?

Hi

I dont seem to be able to find out how to disable preview. On the preview tab in Edit-Preferences-Preview I can only choose between "Always" and "Local files only", there is no "Disable"-option for the thumbnail settings...

Remember Im still on Dapper LTS, so my Gnome version is probably considered Ancient by now :) (waiting for Feisty to be released before making the jump up).


**Edit:**

I tried starting Nautilus from the terminal, looking for any error messages when i navigate to a folder with active downloads. But there is sadly no output...

**Second Edit**

It only affects SOME files, not all of them. Some files i can look at in Nautilus while they are being written to, but some files i cant. Doesnt seem to affect a certain type of files ( it can be a video file, a compressed file, etc. ), its very strange. Is there some Gnome thumbnail cache or folders cache that might be outdated somehow, that I can flush in order to fix this problem?

---

### Post by lvanderree on 2007-04-08
I've got the same problem, but not only for folders with active downloads.

It keeps having a cpu usage of 100% when I've got previews turned on. When I click on view, it is game over, and it completely locks up.

---

### Post by brsseb on 2007-04-10
Hi again

Just wanna tell you that the problem went away when i deleted a video file from the folder generating the nautilus issue. My guess it was somehow corrupted, or contained an unsupported video codec (although no codec errors were reportet when launching nautilus from the terminal). 

Anyways, the file is gone and the problem is no more :popcorn:

---

