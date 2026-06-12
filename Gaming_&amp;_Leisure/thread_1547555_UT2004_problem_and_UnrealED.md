---
title: "UT2004 problem and UnrealED?"
date: 2010-08-06
forum: Gaming &amp; Leisure
---

### Post by Janitor-Blue on 2010-08-06
I have recently installed UT2004 on my computer (Ubunutu 10.04) and it runs like a charm, but I have encountered one small problem. UT2004 can only be launched if I go to a command line, find the folder on my computer and type 'sudo ./ut2004-bin.' Is there a way to change the permission on the file and possibly create a launcher for this? Bonus points if I can use the unreal logo for my launcher. I dislike having to enter my password every time I want to play UT2004.

This brings me to part 2. Under windows, one of my favorite thing to do with Unreal was create maps. UnrealED doesn't seem to support Linux natively. Does anyone have a solution for this? I've seen some suggestions to use Wine, but I'm not exactly sure on how to do this. Any help at all is appreciated.

---

### Post by Brebs on 2010-08-07
> **Janitor-Blue said:**
> Is there a way to change the permission on the file and possibly create a launcher for this?
Of course there is.

For permissions, look at the chown and chmod commands. E.g. "man chown".

You haven't explained how you managed to screw up your installation.

---

### Post by epitaph on 2010-08-08
Try launching the game using just "ut2004" rather than navigating to the actual binary. If installed properly, it should have added a link to this startup script in your /usr/local/bin directory.

To use UnrealED you will likely have to have access to an installation of Windows. I'm not sure how well it operates under WINE.

---

