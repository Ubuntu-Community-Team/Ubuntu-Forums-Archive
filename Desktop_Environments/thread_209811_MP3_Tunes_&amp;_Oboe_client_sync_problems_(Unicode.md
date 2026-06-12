---
title: "MP3 Tunes &amp; Oboe client: sync problems (Unicode?)"
date: 2006-07-05
forum: Desktop Environments
---

### Post by bogl on 2006-07-05
I have an [MP3Tunes Locker]("http://www.mp3tunes.com").  A great way of storing your music & playing it anywhere, any platform.  You can also sync your music from your online locker to a local drive, and vice versa.  The Oboe sync client, written in Python for Windows and Linux, does all the hard work.  Superb idea!

...except for one problem.  I uploaded a stack of music which I ripped onto my /home, formatted ext3.  Since then, I saved it onto DVD and deleted it.  

I then bought a Seagate 160GB USB HDD (formatted FAT32).  Problem: a track in the Locker will not sync onto the Seagate drive.  It's David Bowie's Neuköln (note the umlaut) from the "Low" album.  Every time, it chokes on this track.

I know I could restore it from the DVD backup, but it's the principle.  The Locker is there to act as a way of accessing your music from anywhere and providing a backup, and I want to be sure it will be there if I need it.  Besides, I have a fair amount of "Krautrock", and could have this problem many times over.

MP3Tunes technical support have been looking at this for a couple of weeks now and seem no nearer a solution.

Tech support is beginning to wonder if there may be a Python bug.  Dapper has version 2.4.2-0ubuntu3 listed in Synaptic.  Any known problems?

Refresh my memory: will FAT32 support file names with umlauts in them?  I suspect not.  Could this be the problem?

Or any other suggestions?

Thanks in advance,

bogl

---

### Post by rykel on 2006-12-25
Hi,

I am running Edgy Eft, and am interested in getting Oboe 2.0 to run... however, so far I have no success with it... it is always some missing python stuff, and man, when I look into Synaptic, there are TONS of python files...

How did you get Oboe Sync to work, may I ask? Thanks!!

---

