---
title: "Oh, Yes !!!"
date: 2005-08-24
forum: Desktop Environments
---

### Post by Chareos on 2005-08-24
Moved a large file from /DOWNLOADS to /home (mounted from another disk),
konqueror crashes
**/ is now empty**

Kubuntu 5.0.4 with kde 3.4.2 (updated due 3.4 was terribly unstable)
/ was reiserfs3 as /home is



I just loved open source BEFORE this to happen...
M$ is evil, but doesn't delete your OS disk when moving an AVI file.


And now, I can't find any strenght to try kubuntu again.........

---

### Post by bored2k on 2005-08-24
[QUOTE=Chareos]Moved a large file from /DOWNLOADS to /home (mounted from another disk),
konqueror crashes
**/ is now empty**

Kubuntu 5.0.4 with kde 3.4.2 (updated due 3.4 was terribly unstable)
/ was reiserfs3 as /home is



I just loved open source BEFORE this to happen...
M$ is evil, but doesn't delete your OS disk when moving an AVI file.


And now, I can't find any strenght to try kubuntu again.........[/QUOTE]
 It's not Ubuntu's fault that you don't know the command line. Also, that's why its recommended to mount everything in /media or another exclusive directory. / is a sensitive place to put directories on.

If your / is empty, I can't imagine it booting..

Next time, name your threads in a manner that the member could know forehand what to expect. "Oh, yes" sounds like you love ubuntu and everything works.

---

### Post by Chareos on 2005-08-24
(from another pc of course)

I apologize, admin.

frustration just overwhelmed me.

Anyway that sounds me as a major filesystem breakage. Said that, I don't see any difference in using /media/downloads/... instead of /downloads/...

Not just the downloads directory have been deleted, but the whole filesystem.


I am thrilled that people even considers put reiser4 on next ubuntu... that may put your cat on fire !!

---

### Post by nocturn on 2005-08-24
I have never heard of any such thing and I doubt that moving the file is the cause.

If you reboot, does the system come up?
If you boot a liveCD, can you see your partitions?

The most common explanation is hardware problems, maybe your drive is failing?

---

### Post by bored2k on 2005-08-24
[QUOTE=nocturn]I have never heard of any such thing and I doubt that moving the file is the cause.

If you reboot, does the system come up?
If you boot a liveCD, can you see your partitions?

The most common explanation is hardware problems, maybe your drive is failing?[/QUOTE]
 I'm presuming he did simply issued a "mv" with the wrong directory output. That happens quite often.

> Anyway that sounds me as a major filesystem breakage. Said that, I don't see any difference in using /media/downloads/... instead of /downloads/...It's not breakage, it's simply protecting the user from himself.

---

### Post by nocturn on 2005-08-24
[QUOTE=Chareos]
Not just the downloads directory have been deleted, but the whole filesystem.

I am thrilled that people even considers put reiser4 on next ubuntu... that may put your cat on fire !![/QUOTE]

As I stated before, I think the probability of the move being the cause is quite low, especially with the reiserfs.  I have had reiserfs for about 4-5 years on all my machines (including production servers) and I have yet to loose a single file (even with power outages and damaged hard disks.

Did you do the move as root?  
Did you check the drive for media failures (SMART logs, manufacturer utils)?

It is quite possible that konq crashed because there was a hardware error which can be the cause for your lost data.

---

### Post by lerrup on 2005-08-24
if your system is working, have you tried a search of your file system?  I once thought I destroyed a Mac in a similar way, but the folder was just lost.

I don't think a different file name would have made any difference.

---

### Post by nocturn on 2005-08-24
[QUOTE=bored2k]I'm presuming he did simply issued a "mv" with the wrong directory output. That happens quite often.
[/QUOTE]

mv is dangerous to newbies, but from his description I think he used konqueror to move the file, not sure if he ran as root or not.

---

### Post by Chareos on 2005-08-24
No, bored2k. I'm on linux (and linux only) since 2 years. seasoned enough to know I should never launch a mv as root from / 

I simply used konqueror to move a file from a subdir.

Other partitions on disk still be there.
/ is completely empty.

Right now, I can't try with disk manufacturer's tests,
so I reinstall kubuntu on xfs then late in the morning I'll test the disk.


(NOW, consider that I was finishing to setup kubuntu and that / backup was sheduled for this afternoon !!!!)


Forgot to mention: "Oh, Yes !!!" I've been happy with kubuntu. Hope I'll be again with xfs, now.

---

