---
title: "Maverick install on Inspiron M5030"
date: 2010-12-27
forum: Dell Ubuntu Support (CLOSED)
---

### Post by wgarider on 2010-12-27
Seems to be more than a few sales of this laptop during the holiday season; I've seen them in the US at Best Buy, Amazon and other places for a decent price point. 
After struggling with a few issues to get 10.10 working, I  thought I'd pass along some of the things I did to get Maverick installed and running like I needed..... 
To be clear, my laptop came with the AMD 'Vision'/Athlon II dual-core p340 CPU, 3 GB mem, 320GB HD and the ATI 4250 video chip....

To give credit where it's due, much of this is other people's troubleshooting - I just summarized in one post, in the hope of it being useful to others.

_ACPI/Grub2_
First issue I encountered was that unless I disabled ACPI during the install, I got the 'flashing cursor' screen. Once that was remedied, 10.10 installed without issue. Once I got to the first reboot, the boot process hung again at the flashing cursor - the solution is to edit grub, removing 'quiet splash' and replacing it with 'pci=noacpi'. Remember to permanently edit grub once you're booted fully.
**Reference:**
[http://ubuntuforums.org/showthread.php?t=1633642&](http://ubuntuforums.org/showthread.php?t=1633642&)

**As a side note, until I permanently edited grub, I also had no battery information. Afterwards, I did......*

_Movie player/Medibuntu_
I inserted a DVD to test playing movies and was immediately hit with an error. After some research, I found that even though I had installed everything I'd installed in the past, gstreamer, ubuntu-restricted-extras, etc., it wouldn't work, nor would k9. Once I followed all the steps here:
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

If I run across anything else, I'll update this post.....

---

