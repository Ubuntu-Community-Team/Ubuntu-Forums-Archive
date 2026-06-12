---
title: "Azureus problem"
date: 2005-12-19
forum: Desktop Environments
---

### Post by vbmaster on 2005-12-19
Hey guys,

I'm having a little problem with azureus. I sucessfully installed java, and azureus 2.2.0.2 (i know it's not the newest version).

But when I try to download a torrent it simply says  that the tracker is turned off, and after: (ZipException:gzip header corrupted). This shows in the tracker tab of the torrent that i add. There's no need to say that I'm 100% sure that the tracker is not turned off.

Can you help me?

Errr....sorry my english... :P

---

### Post by Ocxic on 2005-12-19
try a torrent from a differnet tracker, or update to the newest version. see what you get

---

### Post by vbmaster on 2005-12-20
Well, I already tried the new version but the thing keeps still....

I'll search for another tracker to test....

---

### Post by vbmaster on 2005-12-20
Hi again...

it's just to say that I have my problem solved.....

I though that I had correctly installed j2re1.5 but I was still using j2re1.4.

Another thing: i din't knew if a close the console (where I typed (./azureus to open it), azureus closes too..is there a way to avoid this?

Thanks. ;)

---

### Post by Hallavej on 2005-12-20
[QUOTE=vbmaster]
Another thing: i din't knew if a close the console (where I typed (./azureus to open it), azureus closes too..is there a way to avoid this?

Thanks. ;)[/QUOTE]

Use screen:
you may need to install it: sudo apt-get install screen
and then:
screen ./azureus
press "ctrl a+d"

---

### Post by Hyun on 2005-12-20
```
sudo update-alternatives --config java
```
and select Sun Java.

Restart Azureus & Enjoy ! :p

---

### Post by vbmaster on 2005-12-20
Thanks, Hallavej for the tip.... ;)

Hyun, what does that code particullaly?

---

