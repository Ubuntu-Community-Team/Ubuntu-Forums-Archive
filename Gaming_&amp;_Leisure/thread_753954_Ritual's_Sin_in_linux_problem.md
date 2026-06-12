---
title: "Ritual's Sin in linux problem"
date: 2008-04-13
forum: Gaming &amp; Leisure
---

### Post by Nick Blinko on 2008-04-13
I'm trying to run the game Sin under linux, the problem is the installer won't descramble the binary files since it never shows the window to enter my registration key. I found the answer here:

During the installation, you will not be prompted for the CD-KEY, and the binary
will not be descrambled:
- "./sin.exe" -> "give cannot execute binary file"
- "ldd sin.exe" -> "the file is not a dynamic executable"
- "md5sum sin.exe" ->  "ff3f64a7c8fd5d64439a87bcb5c703a7"

The solution is to get the descrambled executable and to put it in the right
directory. You can get it either by:
- installin SiN first on an older machine (seems to work with Linux Mandrake
<=9.2)
- <path_to_your_SiN_CD>/unsupported/x86/sin.exe.gz
(89c53aadddad1327f4a0ddb1295d6460)

The right binary is 56b776f7e9fab339240bc9245a877237 .

where can I can get the right binaries? or descramble the file..

---

