---
title: "Error in Building Live CD"
date: 2010-07-23
forum: Development CD/DVD Image Testing
---

### Post by aditya.gnu on 2010-07-23
[SIZE=2]Dear Linux Geeks,

I am currently working on Debian based Operating System, and my objective is to make a live CD.
I ve followed the specified steps to buid a live CD, and finally I ve made an .iso file too.
Now,I am facing some issues to execute that .iso on Qemu(Virtual Interface),those are:

1. While builing it into an .iso,I skipped the md5sum step, is that mandatory to be built for making a live CD?
And when I am trying to make an MD5SUM using the following command ,

**cd cdrom && find -type f -not -name md5sums -not -name boot.cat -not -name isolinux.bin -exec md5sum '{ }' \; > md5sums**

 its giving me the following error:

[B]find: paths must precede expression
Usage: find [-H] [-L] [-P] [path...] [expression]
[/B]
Kindly specify me, where exeactly the error in the command for creating the md5sum?

2. While executing the .iso file in Qemu using the following command :

[B]qemu -cdrom /root/file.iso -boot d
[/B]
And the I am able to watch the Operating System booting initialization and then when I select the option as "Install as Live CD"

its giving me the following error:

"**Kernel Panic - not syncing: Attempted to kill init!** "

I request who ever reads this thread, please send me some kind of a response.I'll be thankful to them.

Regards,
linux techie.[/SIZE]

---

