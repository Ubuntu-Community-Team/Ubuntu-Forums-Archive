---
title: "Any reason not to use ext4?"
date: 2009-04-18
forum: General Help
---

### Post by MartyBuntu on 2009-04-18
Should I just stick with ext3 for an upcoming Jaunty install.
What are the benefits and is there any downside?

---

### Post by skymera on 2009-04-18
I've run Jaunty for a long time using EXT4.

I've noticed slightly more speed in general boot up and read/write speeds.
I've had to hard shut down many times for various reasons and EXT4 did not compalain. The filesystem check took seconds.

I haven't had any downsides.

---

### Post by chriskin on 2009-04-18
it feels way faster than ext3
i don't know if jaunty is so much faster than intrepid, but the filesystem must have helped somehow, the difference is easily understandable. 
the only downside i can think of is that a dual-booting with a previous version of ubuntu might have some problems, as the other version might not recognize the ext4 filesystem, not that i can think of any reason why you should have two versions either way, or why you would want the previous one to have access on jaunty's files

---

### Post by bumanie on 2009-04-18
I have used ext4 since jaunty alpha 2 and so far, there has been no problems. As stated above , read, write and boot are all quicker - booting being very noticeably so, although I haven't booted 9.04 with ext3 to do a direct comparison. fsck is much quicker.

---

### Post by zenithdave on 2009-04-18
I have jaunty on my EEE900 using ext4 no problems.

---

### Post by Klaz168 on 2009-04-18
ext4 is mature enough to be used. It provides better performance and features, like bigger subdir limit, supports larger volumes..

---

