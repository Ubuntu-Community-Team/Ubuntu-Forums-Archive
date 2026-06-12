---
title: "Question installing WoW"
date: 2007-05-20
forum: Gaming &amp; Leisure
---

### Post by Elvish Legion on 2007-05-20
When I tried to install WoW I couldn't unmount the cd and I remember it being recommened to copy the contents  of the cds to a folder and install from there (I Assume two different folders with BC) But I Can't remember the command to rip the cds..

Any help or is it just copy and paste?

---

### Post by Cappy on 2007-05-20
[http://ubuntuforums.org/showthread.php?t=312482](http://ubuntuforums.org/showthread.php?t=312482)

How to copy the cds isn't in there but this should do it:
```

mkdir ~/wowinstall
cp -r /media/cdrom/* ~/wowinstall
cd ~/wowinstall

```

---

