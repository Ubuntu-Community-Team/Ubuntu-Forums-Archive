---
title: "ext4"
date: 2009-04-29
forum: General Help
---

### Post by krishna1650 on 2009-04-29
i have upgraded my system from 8.10 to 9.04. my root partition is ext3 format. is there any way to convert root partition to ext4 without installing 9.04 by just upgrading?

thanks for help.

---

### Post by jigglywiggly on 2009-04-29
Sorry, have to reformat. I have ext4 on this laptop I'm typing on, it's worth the format, I'll tell you that.

---

### Post by cariboo on 2009-04-29
Have a look at this [page]("http://webupd8.blogspot.com/2009/04/convert-your-ext3-file-system-to-ext4.html") to convert without having to reformat.

---

### Post by krishna1650 on 2009-04-29
> **jigglywiggly said:**
> Sorry, have to reformat. I have ext4 on this laptop I'm typing on, it's worth the format, I'll tell you that.

is ext4 faster than ext3? is it reliable?
thanks for the reply.

---

### Post by halovivek on 2009-04-29
you can read more about this from [here]("http://en.wikipedia.org/wiki/Ext4")

---

### Post by whoop on 2009-04-29
Or take a look at the ext3 to ext4 conversion howto on this forum:
[http://ubuntuforums.org/showthread.php?t=1118295](http://ubuntuforums.org/showthread.php?t=1118295)

---

### Post by buchan on 2009-04-29
Some users are experiencing problems with EXT4
[http://ubuntuforums.org/showthread.php?t=1135055](http://ubuntuforums.org/showthread.php?t=1135055)


Make sure you back up before making the switch.  
Was causing all kinds of issues for me but as soon as I re-installed with EXT3 my problems stopped.

---

### Post by whoop on 2009-04-29
> **buchan said:**
> Some users are experiencing problems with EXT4
[http://ubuntuforums.org/showthread.php?t=1135055](http://ubuntuforums.org/showthread.php?t=1135055)


Make sure you back up before making the switch.  
Was causing all kinds of issues for me but as soon as I re-installed with EXT3 my problems stopped.
I am not really convinced that the freezes are caused by ext4. Some people are getting freezes with ext4, some people are getting freezes with ext3.
I had freezes with ext3 when jaunty was at alpha5, when alpha6 came along I converted the file system to ext4 and the freezes also went away, so it was the complete opposite (although I think it has no relation with the file system conversion).

Here's a bug report about jaunty freezes: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/347848](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/347848). The poster of this bug is actually using ext3 as you can see in his BootDmesg. Here's another one also ext3: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/364828](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/364828)

It could have something to do with the fact that some people are getting freezes and they think: "What's the biggest change on my system? Ahh, ext4". I am not stating this as a fact but it is certainly possible.

---

