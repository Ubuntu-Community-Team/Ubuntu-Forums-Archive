---
title: "aptoncd &quot;No space available in the disk&quot;"
date: 2008-11-03
forum: Desktop Environments
---

### Post by klausner on 2008-11-03
Trying to burn a repair disk with aptoncd. The program tells me I need two CDs, or one DVD. OK. Not a problem. But when I go to burn the image (either to disk, or to my home dir), I get an error:
[INDENT]"No space available in the disk

Before continue, please make sure you have enough space on /tmp and /home/klausner" (sic)[/INDENT]

Since I have 25.9GB available in /home, I assume the problem is thay there is only 1.3GB free in /, which is the partition with /tmp. (Although 1.3GB ~= 2 CDs.)

Is there a workaround, or do I have to start scavenging bytes from / ? I already cleaned out /tmp.

---

### Post by klausner on 2008-11-09
Bump.

---

### Post by redradish on 2009-04-24
Hey, I just upgraded to the latest version now because of a bug in the previous one, and I get the same error too! It really doesnt seem to be a space issue because I have like 20GB free in home, and 4.3GB in / even though aptoncd only needs to make a 2GB file. Hmm, any ideas?

---

### Post by redradish on 2009-08-02
PS: If you still have this problem, try updating to the new version that's out now, they seem to have sorted everything out now, plus its way faster!

[http://aptoncd.sourceforge.net/download.html](http://aptoncd.sourceforge.net/download.html)

---

### Post by maubarra on 2009-11-13
Just in case anyone still has this problem I used a simple solution. I'm running Karmic Koala and when I tried to create an APTonCD disk on my laptop, I bumped with this issue. The total space required according to APTonCD was 1.3 GB and I had 1.6 on my /tmp dir and like 20 GB on my home dir. I think (I'm not sure though) that it also needed some extra space to create the ISO file, even if the destination folder was my home dir.

How to get around this? Actually all I did was running APTonCD with the -t parameter to specify the temporary dir to be used. So I created a tmp dir on my home dir and used that one. Went something like this:

aptoncd -t /home/<myname>/tmp

And voila! It worked!

Hope this helps anyone!

---

