---
title: "cannot edit xorg.conf"
date: 2008-09-13
forum: Desktop Environments
---

### Post by yackmaster on 2008-09-13
Here is what I'm trying to do,  my Ubuntu login screen (where I enter my user name and password) is about 2 times larger than my monitor. Once I log in, everything is fine.

The fix listed here is not working "http://ubuntuforums.org/showthread.php?t=190081"

I'm stumped. when i try to edit xorg.conf I cannot. I'm using the "System Tools/Root Terminal" so i do not have to type in "sudo".  i use the command of "gedit /ect/X11/xorg.conf" and the files pulls up but there is not data in the file. no text at all.  when i do a filesystem search i do find my xorg.conf file in "ect/X11". if i click on it i can open the file and see all the text but i cannot edit the text.

Thanks in advance for any help.

system stats
Dell Laptop D610
Intel i915 video
2bg ram
60gb HD
1.7 mhz P4 Mobil cpu
Ubuntu hardy 8.04
Gnome 2.223
Kernel 2.6.27-19-generic

---

### Post by swimb on 2008-09-13
Make sure you are typing the correct path, I see an error in the one you typed. It should be
/etc/X11/xorg.conf

---

### Post by benerivo on 2008-09-13
Just to check that the command you're using has no typing errors. It should be /etc and not /ect

---

### Post by yackmaster on 2008-09-13
well duh :-0 

i guess i should have not fat fingered it. worked like a charm! 

THANKS

---

