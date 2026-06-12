---
title: "Each program's list of recently opened files"
date: 2012-01-29
forum: Desktop Environments
---

### Post by rage_311 on 2012-01-29
I've only had Kubuntu 11.10 (64-bit) installed as my primary OS on my machine for a few months, so I'm still trying to figure out a few things on it.  I've noticed that each program keeps a list of the files that you've opened recently with it.  I'm not talking about the "Recently Used" section of the application launcher.  If you open any given program (VLC, for instance) and launch the "Open File" dialog (in VLC, Media > Open File...), and click on the down arrow in the "Name:" text box, it displays a list of your recently opened files for that program.

My question is, where are those entries stored in the file system?  I'd imagine that it would be on a per-user basis, but I just can't seem to find it.  I've done a lot of googling, trying to figure it out, but I've been unable to find the answer to this.  I'd like to be able to flush the history -- either entirely or selectively would work.

Thanks for any help or direction.

---

### Post by inobe on 2012-01-29
anything done like settings and config files are hidden via dolphin.

show hidden files in dolphin, most files will look like for example

```
.kide4
```

or 

```
.vlc
```

within these folders are txt or conf files that can be edited or reset by renaming them.

i don't have vlc, so i can't verify this for that app, i like smplayer for various reasons.

most have their own config files.

---

### Post by rage_311 on 2012-01-31
I assume you're talking about files that would be in each user's home directory?  I have several of the ".programname" folders in my home directory, but VLC is not one of them, unfortunately.  I did poke around in the .config/vlc folder to no avail.  It seems like it might be a KDE-wide mechanism, since the "Open File" dialog/interface is the same regardless of the specific program that you're using.  Do you think that's a possibility?  (That it's stored somewhere in a KDE config/history file?)  I know that's how Windows handles this data -- via registry keys beneath Windows groups.

Thanks for the help in trying to figure this out so far.  It is definitely appreciated.

---

### Post by rage_311 on 2012-02-02
Still no luck... I've exhausted all of my resources.

Anybody have any insight?

---

### Post by inobe on 2012-02-02
i can look, though i can't stand vlc, it can be easily removed later on:P

side note, not home, you may want to check back later.

---

### Post by rage_311 on 2012-02-03
Lol.  To each their own.  Thanks for doing that.

---

### Post by inobe on 2012-02-05
i'm able to clear recent stuff within the apps, in kickoff menu, right click and you can rid of docs and apps, in vlc, tools> preference, uncheck "save recently played"

to go deeper, google "reset kde app history"

---

### Post by rage_311 on 2012-02-09
Thanks for the suggestion.

I had already unchecked the "save recently played" option in VLC -- unfortunately, this only affects the recent files that are displayed in VLC's built in Media > Recent Media sub-menu and doesn't apply to the "Open File" dialog.

I also did go deeper by googling your suggested search.  I found lots of things, but unfortunately I still couldn't find any relevant info about where this file history is stored.  I even ran kscrubber... no such luck. Kscrubber is even designed specifically to wipe every trace of your activity on an Ubuntu/KDE4 system.

I dug all around on the HDD and couldn't find a THING...  I'm not sure if KDE is the subsystem that would be in charge of keeping track of things like this, but I've poked around in every KDE related folder (yes, I made sure to check hidden files) and found nothing.

Any other suggestions?  Forums that would be better suited to a question that's this specific?  If so, which?

Thank you for your help so far!  The search continues...

---

### Post by rage_311 on 2012-02-13
Any more thoughts on the matter?

---

### Post by rage_311 on 2012-02-15
Found it!

In case anybody else is wondering... the history for recent files for VLC (and Google Chrome, and probably others) is stored in a plain text file that is located at: 

```
/home/username/.kde/share/config/kfilemodulerc
```

Also, for KDE-native applications that use the KDialog "Open File Dialog" (I noticed Amarok, specifically), the historic info is in: ```
/home/username/.kde/share/config/kdialogrc
```

A couple of notes:

1. The ".kde" folder is hidden.
2. You can just delete these files and they will be recreated the next time a program that uses them needs them.

Thanks for your help, inobe.  You were right from the beginning... I just wasn't looking hard enough.

---

### Post by inobe on 2012-02-15
> **rage_311 said:**
> 

Thanks for your help, inobe.

your welcome, you did great, not many folks have the patience to understand the very system they use, they often become intimidated by it, some just give up and come here to troll due to their inability to take the time learning, you are one of the majority that took the time to learn.

the operating system is powerful to do whatever and well worth the time taken to figure it out:D

please mark your thread solved.


'Solved' is under the drop-down menu Thread Tools.

---

### Post by oldos2er on 2012-02-16
Thank you for posting the solution. I've been wondering about this myself.

---

