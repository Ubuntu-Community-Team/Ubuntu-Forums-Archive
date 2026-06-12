---
title: "Convert ext2 filesystem to ext3"
date: 2009-06-02
forum: General Help
---

### Post by merdok1981 on 2009-06-02
Hi Guys,

i've got a 1tb hard drive which used to reside inside a NAS, a few weeks ago the NAS broke down and I transferred the drive into my media server. 

Problem is, the file was formatted with the ext2 filesystem which means everytime I have a problem with my computer, which I do quite a bit (I'm one of the people who is being effected by the intermittent freezes in Jaunty) and have to do a hard reboot, I get the 'unclean' shutdown message followed by 15 mins of hard drive checking. 

Obviously with this being a media PC I don't want to wait 15 mins to watch my programs, nor do I want to risk data corruption every time my PC fails.

I've read bits and bobs on the internet that you can add the journaling system (essentially converting ext2 to ext3) using a single command line (tune2fs -j /dev/hda1), I really want to do this as its becoming an annoyance but I am worried about the possible risks.

I have over 750gb of data on here and no way to back it up (I know I should but hard drives are not free and I can't afford another big hard drive right now), I would be devastated if I lost all that data as its taken me years to amass all those files and at least 300gb of it is home movies which I really would not be able to stand losing.

Has anyone done this conversion? Is there any risk of data loss by doing it? Am I better off tolerating it for a few months whilst I save up for another hard drive?

---

### Post by perrti-y02 on 2009-06-02
The way I always do it is shrink the ext2 partition to as small as it will go. Then create a new ext3 partition in this space. Copy 250gb of files across. Shrink the ext2 partition again. Move files. Shrink. Move. until everything has gone.

Don't do this until you have had a reply from other people. I am not that experienced and this might give you some problems. It worked for me a few times but I can't promise it won't corrupt files.

---

### Post by merdok1981 on 2009-06-08
Just going to bump this topic, hope thats not against the rules here.

---

