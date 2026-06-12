---
title: "Installing packages without Synaptic"
date: 2005-10-22
forum: Desktop Environments
---

### Post by irv on 2005-10-22
I am some what new to Linux, and I find installing packages confusing :confused: There are .deb, gz, and .bin files and no real instructions on how it all work.
So far I did figuar out how to us sudo dpkg -i to install .deb files, but when I tried to install gxine all I get is lib files not found. (libxinel 1.0.1 and libsmjsl) I do have libxinel 1.0 installed but it neeeds 1.0.1. How do I install bin and gz files? and where are all this files going?

---

### Post by Ali_Baba on 2005-10-22
Hi,I had the same problem when I started using Ubuntu :) .gz files are packages,so you need to extract them first.
Bin files you can start from command line.
Runnable files go to /bin or /usr/bin.There you can start programs.
Other files of a program go around the filesystem.When you install a program in synaptic you can check where the files are installed.I suggest you use synaptic.It has almost all programs that you need and its easy to use.

---

### Post by poofyhairguy on 2005-10-22
I moved this to the correct forum.

---

### Post by irv on 2005-10-22
I had this in this forum, see:
 [http://ubuntuforums.org/showthread.php?t=80518](http://ubuntuforums.org/showthread.php?t=80518)
Thanks for getting me on the right track.

---

### Post by dbw on 2005-10-24
Additionally, I would recommend "checkinstall", which helps log any programs you compile from source into your Synaptic logs.

---

