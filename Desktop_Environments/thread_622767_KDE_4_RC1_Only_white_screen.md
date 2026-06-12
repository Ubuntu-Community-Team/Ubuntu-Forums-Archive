---
title: "KDE 4 RC1: Only white screen"
date: 2007-11-25
forum: Desktop Environments
---

### Post by jonnybecker on 2007-11-25
Hi,

I just installed KDE 4 RC1 (following the instruction rules on the Kubuntu homepage) on my Gutsy machine.

When I start a KDE 4 session I only get a white screen, the "Did you know"-window and a window to start programs by typing in their name. No panel. 
I was (kind of) able to launch Dolphin by typing in the name. The all the menue-entries say "No-text" and it crashed pretty soon.

The big question is: 
- Did I make errors installing this? I got KDE 4 Beta 3 running before.
- Where can I find the log-output for KDE 4 session?
- Has anyone else experienced this?
- How can I fix it myself?

Cheers
Jonny

---

### Post by Asraniel on 2007-11-25
i use kde4 from svn directly. i heard that the kubuntu team screwed up very much with packaging kde4 (since the first kde4 packages they made).

---

### Post by jonnybecker on 2007-11-25
Hi,

sounds great. Any HowTos available for this?

Cheers
Jonny

---

### Post by GeneralZod on 2007-11-25
> **jonnybecker said:**
> Hi,

sounds great. Any HowTos available for this?

Cheers
Jonny

Pretty long-winded, but once you've done it the first time, it becomes much easier :)

[http://techbase.kde.org/Getting_Started/Build/KDE4](http://techbase.kde.org/Getting_Started/Build/KDE4)

---

### Post by gamma on 2007-11-26
> **jonnybecker said:**
> Hi,

I just installed KDE 4 RC1 (following the instruction rules on the Kubuntu homepage) on my Gutsy machine.

When I start a KDE 4 session I only get a white screen, the "Did you know"-window and a window to start programs by typing in their name. No panel. 
I was (kind of) able to launch Dolphin by typing in the name. The all the menue-entries say "No-text" and it crashed pretty soon.

The big question is: 
- Did I make errors installing this? I got KDE 4 Beta 3 running before.
- Where can I find the log-output for KDE 4 session?
- Has anyone else experienced this?
- How can I fix it myself?

Cheers
Jonny
I've had this issue a few times. I've fixed it by removing my ~/.kde4 configuration directory. 
**WARNING**: I'd only do this if you don't mind losing data, I think anything related to KDE4 is stored in there so you could potentially lose a lot of stuff.

I believe this is a plasma related issue, so I'm guessing it could also be fixed by deleting the relevant plasma configs.

---

