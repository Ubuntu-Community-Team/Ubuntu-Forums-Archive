---
title: "Ubuntu 2D"
date: 2012-05-28
forum: Desktop Environments
---

### Post by gettinoriginal on 2012-05-28
I have just upgraded to 12.04.  I am new to Unity and have a problem.  At sign in, I can only log in under Ubuntu 2D, Ubuntu gives me a wallpaper but no launchers or top bar.  Using 2D I am unable to change the launcher icon size or Compiz,  and 3D is not listed as an option.  Any help would be appreciated.
My System is Dual Boot with Windows 7
Details are Ubuntu 12.04
Memory 2.7 GiB
Processor AMD Athlon II Dual Core M300 x 2
Graphics Vesa: RS880M
OS type 32 Bit
Disk 131.7 GB

---

### Post by Frogs Hair on 2012-05-28
Run the following test in the terminal to see if you have Unity 3D support.```
/usr/lib/nux/unity_support_test -p
```
If 3D is supported login to Ubuntu use Ctrl + Alt + F1 to enter TTY. Next enter user name, password, and run the following command. ```
unity --reset
```
Wait until the process is complete and your user name appears again. Use Ctrl + Alt + F7 to renter the desktop environment.

If there is error reporting wait until finished. If Unity doesn't appear within a minute or two restart and login to Ubuntu and see what happens.

---

### Post by Frogs Hair on 2012-05-28
If you have only 2D see this post.[http://ubuntuforums.org/showthread.php?t=1943423](http://ubuntuforums.org/showthread.php?t=1943423)

---

### Post by gettinoriginal on 2012-05-28
It says yes to 3D, but TTY will not let me log in, says log in is incorrect ??  Yet I can log in from the log in screen.

---

### Post by Frogs Hair on 2012-05-28
Weird ! , make sure you use lower case when you enter the user name next to login: and the password prompt should follow.

---

### Post by gettinoriginal on 2012-05-28
did all that, still "incorrect login"  should I log in as admin ?  if so is that different ??

---

### Post by Frogs Hair on 2012-05-28
> **gettinoriginal said:**
> did all that, still "incorrect login"  should I log in as admin ?  if so is that different ??

Use admin login.

---

### Post by gettinoriginal on 2012-05-28
still won't let me log in.  Where do I find my passwords or keys in case I misspelled when I originally installed this version

---

### Post by Frogs Hair on 2012-05-28
It will be in passwords and encryption keys . It will give you the option to change passwords by right clicking the passwords folder.

The unlock folder option is not available on my installation though.

---

### Post by gettinoriginal on 2012-05-28
Thanks, solved

---

