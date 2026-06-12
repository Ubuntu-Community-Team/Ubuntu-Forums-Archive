---
title: "[SOLVED] Best way to backup (without &amp;quot;Partimage&amp;quot;)"
date: 2006-09-22
forum: Desktop Environments
---

### Post by wieman01 on 2006-09-22
Hey Guys, 

I want to backup my harddisk (root, home, data) but don't really know the most efficient way to do it. Here are my constraints:

1. No internet connection because Live CD does not recognize my wireless card. So Partimage is out of the question.
2. I don't want to do it the "dumb" way and copy & paste using GParted or command line.

Does anybody have a smart idea? This is another tough one I suppose.

---

### Post by lagagnon on 2006-09-22
I do not understand. You do not need a wireless card to run PartImage. All partimage does is take an image of your parttions and creates one large file which you can then store anywhere. Please explain.

---

### Post by wieman01 on 2006-09-22
I want to backup my root partition. Sadly I cannot do so after having booted Ubuntu because Partimage complains that "root" is mounted.

So the only option is using the Live CD, however, Dapper Live CD does not come with Partimage preinstalled. Cannot find it. That's it.

_EDIT:_
But perhaps I am missing something. What did you do to get it done?

---

### Post by wkulecz on 2006-09-22
Get the Knoppix DVD (CD will be fine if it has Partimage) boot it and back up your partitions to a different drive or a large USB memory stick.  Worked for me, although Partimage is lame compared to Ghost if the destination partiton size is different (I was cloning systems and ended up using Ghost and Knoppix to install grub).  Norton's Ghost will work too, but its not free, but Fry's usually has it for cheap after rebate.

---

### Post by wieman01 on 2006-09-22
Ok, that's it then. You don't use Ubuntu's Live CD then. Is there no way to achieve that under Ubuntu? I cannot believe it.

---

### Post by wieman01 on 2006-09-22
Answer to my own question: I still use Partimage but boot from a Live Rescue CD which can be found here:

[http://www.sysresccd.org/Download]("http://www.sysresccd.org/Download")

Works great & is pretty fast. Just in case anybody wants to hear about it. Like a charm.

There is a good howto:

[http://www.ubuntuforums.org/showthread.php?t=226402]("http://www.ubuntuforums.org/showthread.php?t=226402")

---

