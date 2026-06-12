---
title: "Ubuntu Live CD: RythmBox not playing MP3"
date: 2005-12-31
forum: Desktop Environments
---

### Post by SupaShaD on 2005-12-31
I'm running Ubuntu (5.10) off a live CD and have mounted my fat32 drive to access my mp3s using RythmBox, however it declares that none of them are audio streams?

Also noteworthy, when trying to listen to internet radio using Rythmbox I continuously get a Stream Error: Unexpected End of Stream message.  Successfully preventing me from being able to access and listen to any internet radio stations.

Anybody know why I can't listen to any music using a liveCD?  Is this a specific thing that the liveCD doesn't support or is there a potential issue here?  ESD is loaded and what not so I can't imagine what's causing the problem.  I hear system sounds and various sounds from other programs so I know it's not my sound card.

Any help is greatly appreciated.

---

### Post by audax321 on 2005-12-31
Did you install all the codecs? If not see here: [http://ubuntuforums.org/showthread.php?t=110520](http://ubuntuforums.org/showthread.php?t=110520)

---

### Post by MetalMusicAddict on 2005-12-31
I dont think you can install anything with the "live" CD. If you decide to install search the fourm 1st for MP3.

---

### Post by SupaShaD on 2005-12-31
OK fellas, thanks for the reply, I thought it might be an issue with codecs I am just suprised that the LiveCD's didn't ship with them pre-installed.

Thanks again,
 SupaShaD

---

### Post by nami on 2005-12-31
GNU software e.g. ubuntu is totally free, but the mp3 coded has licensing issues.  This is why the mp3 codec is not included with any version of ubuntu!

However, read this [http://www.fluendo.com/press/releases/PR-2005-05.html](http://www.fluendo.com/press/releases/PR-2005-05.html)

---

### Post by SupaShaD on 2006-01-02
[QUOTE=nami]GNU software e.g. ubuntu is totally free, but the mp3 coded has licensing issues.  This is why the mp3 codec is not included with any version of ubuntu!

However, read this [http://www.fluendo.com/press/releases/PR-2005-05.html](http://www.fluendo.com/press/releases/PR-2005-05.html)[/QUOTE]


Yep, I'm all caught up on the issue, however it appears there's another one regarding the gstreamer plugin; one that prevents the inclusion of it with Ubuntu.  Under Ubuntu's ideology and manifesto all software included has to be completely free and open for release and modification.  However under the MIT structure it would require Ubuntu to sign into a contract (albeit free) in order to use the technology, and limiting the modification of the source code and redistrobution of the modified source.

This negates Ubuntu's core belief and practice that their software will always be free under all circumstances and fully modifiable.  And being that that's their belief, the inclusion of the GStreamer plugin is unlikely given that it's free in a limited form (modifiable, but not redistributable unless signed into contract with Fluendo and its affiliates).  It's unfortunate that software patents like this are being enforced in such a manner that's overall detrimental to the future of computing, but that's how it is!  In the meantime, the best bet would probably be to convert to or rip to OGG; which is an open source audio codec comparable to MP3.  Doing so will encourage the spread of an open source alternative to MP3.  Of course if you have a huge MP3 library you can always download the mad mp3 decoder for linux, or gstreamer as an end user.  Just don't expect them to come packed in any release from Ubuntu!

Thanks again for the information guys, I'll definitely be keeping an eye on the development of Ubuntu and may very well be installing it on my next format and leaving Windows on a partition designated for gaming.
 -SupaShaD

---

