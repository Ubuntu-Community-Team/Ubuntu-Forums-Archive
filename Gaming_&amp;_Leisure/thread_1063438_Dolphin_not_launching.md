---
title: "Dolphin not launching"
date: 2009-02-07
forum: Gaming &amp; Leisure
---

### Post by zero777zero on 2009-02-07
hello, i've just finished downloading a 32bit linux program and i double clicked on a "linux executable" file with no result. this has happened before. am i supposed to run it in the terminal or something? how do i do that?

---

### Post by howefield on 2009-02-07
What's the name of the file, and site you got it from ?

---

### Post by zero777zero on 2009-02-07
its the Dolphin emulator, compiled specifically for 32bit linux

dolphin-emu.com

edit: i've had this issue with other linux software before

---

### Post by zero777zero on 2009-02-07
hi i downloaded and tried the two latest dolphin's for 32bit linux here
[http://www.dolphin-emu.com/downloads.php?cat_id=2](http://www.dolphin-emu.com/downloads.php?cat_id=2)

when i double click on the executable nothing happens

---

### Post by mb_webguy on 2009-02-07
Any file in Linux can technically be executable, depending on the file permissions.  Sometimes, when you download and extract archive, you may need to correct the file permissions before you can run a file that should otherwise be executable.  (Of course, if the contents of the file aren't something that can be executed, it of course doesn't matter if the file permissions say that it can be executed.)

In the terminal, cd to the directory containing the file you want to run.  Use "ls -lsh" to view the contents of the directory and the file permissions.  If your user account owns the file, you should have an "x" in the fourth position in the file permissions column (the first column, containing 10 characters).  If you don't see one, fix it with the command "chmod u+x *filename*".  If your user account doesn't own the file, but is in the group associated with the file, then you need an "x" in the seventh position in the file permissions column.  If not, you can fix it with "sudo chmod g+x *filename*".  If you don't own the file and aren't in the group associated with the file, you need an "x" in the last position in the file permissions column.  If not, you need to fix it with the command "sudo chmod o+x *filename*".

Also, if there's a problem with the executable file itself, you can often see error messages you wouldn't ordinarily see by running the file from the terminal.  Just type the path and filename of the file to run it (assuming you have execute permissions on the file as described above).  For example, if I have a file in my home directory, I can run it with "~/*filename*".  File in a bin directory can be executed by simply typing the filename.

---

### Post by hikaricore on 2009-02-07
Hi there.

Don't make duplicate threads on the same topic.

---

### Post by howefield on 2009-02-07
It is a dolphin-xxxx-fastlog.tar.bz2 file, is that right ?

---

### Post by zero777zero on 2009-02-07
@ mb_webguy: here is my output from ls -lsh
total 3.8M
1.9M -rwxr-xr-x  1 yakuza7 yakuza7 1.9M 2009-02-02 09:11 Dolphin
1.9M -rwxr-xr-x  1 yakuza7 yakuza7 1.9M 2009-02-02 09:11 DolphinNoGUI
4.0K drwxr-xr-x  2 yakuza7 yakuza7 4.0K 2009-02-02 09:11 Libs
4.0K drwxr-xr-x  2 yakuza7 yakuza7 4.0K 2009-02-02 09:11 Plugins
4.0K drwxr-xr-x  5 yakuza7 yakuza7 4.0K 2009-02-02 09:09 Sys
4.0K drwxr-xr-x 13 yakuza7 yakuza7 4.0K 2009-02-02 09:09 User

@ howefield: yes, except i extracted them already

----

aparantly i'm missing the dependency libbluetooth.so.2, but it doesnt appear anywhere in synaptic, only libbluetooth-dev which i already have installed.

---

