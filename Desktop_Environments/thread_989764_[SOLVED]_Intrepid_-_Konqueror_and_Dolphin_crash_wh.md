---
title: "[SOLVED] Intrepid - Konqueror and Dolphin crash when attempting to get folder propert"
date: 2008-11-21
forum: Desktop Environments
---

### Post by RogueLeader on 2008-11-21
Upgraded to 8.10 recently on my desktop machine, and I'm really enjoying it so far despite some of KDE4's growing pains.  There's one glaring problem I'm having so far, that I can't seem to find any information on elsewhere.

Right clicking and getting "Properties" (or hitting Alt+Enter while an entry is highlighted) crashes both Konqueror and Dolphin on my machine.  I also just went into Ark, clicked on new Archive to bring up a file dialog, and tried to get properties on one of the folders there.  This also crashed Ark.  So, I believe this is a problem with some underlying KDE4 code (or at least Kubuntu's packaging of it).  I searched KDE for a bug report on the issue and couldn't find anything. The crashes only happen with directories, regular files' properites are retrieved without issue.

Can anyone confirm this as a problem or even confirm the opposite, that this function works for them?  One interesting observation is that within Amarok's file browser, obtaining directory properties did not crash that program.  It's still Amarok 1.4 though, not Amarok 2.  So the problem might lie somewhere in Kubuntu's KDE4 code.

Any suggestions?  There's a slew of debugging output that pops up in the KDE crash handler after the crashes.  If nobody has any suggestions I'll file the bug with KDE.

---

### Post by RogueLeader on 2008-12-03
Bug filed [here]("https://bugs.kde.org/show_bug.cgi?id=175863").

Hasn't been any activity with the bug or on these forums.  I'm getting the feeling I'm the only one with this problem and it's something system-specific.  I've reinstalled the kde4 packages with no luck.  Looking forward to December 16 or so, whenever they package KDE 4.2 beta 2.

---

### Post by kernelhaxor on 2008-12-04
I've never heard of this problem before.  From what you say, the issue might not be a KDE issue at all (since reinstallation of KDE packages didnt help).  I think something at a lower level (possibly at the kernel level) went wrong during your upgrade.  Upgrades don't always go smooth.  They are known to create weird issues some times.  Its not worth your time to debug.  If its not too much trouble, I would suggest a fresh install of Kubuntu

---

### Post by RogueLeader on 2008-12-05
Thanks for your insights, I hadn't considered that.  I guess if the packages I mentioned I was waiting for don't fix the problem (and I'm willing to wait the couple weeks), I might fresh install.  The reason I want to leave this as a last resort is the year and a half I have invested into this system in terms of tweaking settings, installing programs, getting all hardware to play nice, etc.  

That said, this is a big enough problem to want to get it working.  I wouldn't mind spending some time to try to debug it, the problem is I don't have any Linux kernel or KDE development experience.   I'd like to get involved with OSS, so this might be a nice place to get my feet wet.

I might also branch out and try a new distro if I have to fresh install.  I love Kubuntu and also have it on my Laptop (sticking with Hardy there for now), but now that I'm much less of a beginner, I might like to try something different.

---

### Post by RogueLeader on 2009-01-05
Marked as solved, thanks to someone named Andreas Rjasanow who replied on KDE's own bug tracker.  Here is what he said:  
> 
After a "strace -f dolphin --nofork" I've seen this line: 

access("/etc/security/fileshare.conf", W_OK) = -1 EACCES (Permission denied) 

SHARINGMODE was set to "advanced", however "simple" seems to be required. After I've changed this line in fileshare.conf the properties dialog appears again. 

Editing this file fixed the issue for me.  I'm reporting this in case someone else searches these forums for this issue!

---

### Post by mayeulk on 2009-05-01
Thanks a lot, I had the same problem with "simple"/"advance".
So I think there is a bug somewhere in the (samba ?) sharing system, since  did not edited that file by hand  originally

---

