---
title: "VICE emulator - .d64 related file extension problem"
date: 2013-12-28
forum: Emulators
---

### Post by tschill on 2013-12-28
I am experiencing some problem with VICE 2.3 emulator under Ubuntu 12.04. It works fine with most .d64 files now after some adjustments (the installation is not really easy, I have to say. Took me some time because files were missing.)

But not all .d64 files are accepted. All files have the file extension .d64, nonetheless Ubuntu identifies some .d64 files as TGA image files. (How is this possible? I thought the file extension defines for the OS what to do with the file.) I have the impression that usually the second side of the floppy disk image is misinterpreted as an image TGA file, but not all of them. When I try to attach such a fake TGA .d64 file to a drive, VICE crashes. 

[IMG]http://img849.imageshack.us/img849/5244/zp8z.jpg[/IMG]

In my Ubuntu setting TGA files are associated with the image viewer and GIMP. Assuming this is part of the problem, I tried to remove these TGA associated applications with Ubuntu Tweak. Surprisingly I was able to remove one file association, but was not allowed to remove the last remaining entry in the list. But maybe the file association is not responsible for the problems VICE experiences with these fake TGA files, so this might be a secondary problem.

Any help is greatly appreciated, since I am not very familiar with Ubuntu.

---

### Post by codemaniac on 2013-12-28
Thread closed, dupe of [this]("http://ubuntuforums.org/showthread.php?t=2196246").

Please do not start multiple threads for the same issue.

---

