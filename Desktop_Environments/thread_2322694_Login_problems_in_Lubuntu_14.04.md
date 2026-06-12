---
title: "Login problems in Lubuntu 14.04"
date: 2016-04-29
forum: Desktop Environments
---

### Post by linux_lom on 2016-04-29
Hello:

Yesterday, all my icons and the menu dissapeared and I only could see the wallpaper and the mouse cursor.
I reinstalled lxde using:

```
sudo apt-get install --reinstall lxde
```

After that, I can see the login screen but it is different of Lubuntu login screen default, and I can't see my user names, only "usbmux" and "ntp"

The only way I can login and run lxde is using:

CTRL + ALT + F1 to enter the terminal
```
sudo -s
```
```
startx
```

Please, I need some help to add mi user names to login screen and login using them. Now I only can login using root.

---

### Post by DuckHook on 2016-04-30
Welcome to the forums, linux_lom

Starting X under root (which is what you did) is *never* a good idea. Just an invitation to get owned. First, do you have backups of your most important data? If not, do so *right now*. If your data is safe, then log in *as yourself* (none of that "sudo -s" stuff) to a CLI with <Ctrl>+<Alt>+<F1> and do:```
sudo apt-get update
sudo apt-get install --reinstall lubuntu-desktop
```Then reboot and try logging in normally again.

---

### Post by linux_lom on 2016-04-30
Hello[B] DuckHook:

[/B]I have reinstalled lubuntu-desktop and I have a different graphical login screen now, but the users names are still gone. If I try to login writing their names and passwords it doesn't work.  [**[COLOR=#C61919][B]**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=1256508")

---

### Post by DuckHook on 2016-05-01
Try the following:```
rm ~/.Xauthority
```...then reboot and try logging in. If that doesn't work then try:```
sudo apt-get update
sudo apt-get install --reinstall lightdm
```If that doesn't work, then:```
sudo apt-get purge lightdm
sudo apt-get install lightdm
```

---

### Post by linux_lom on 2016-05-01
Hello, DuckHook:

Yesterday I had to login with root user again and I saw the hard disk was 98% used, so I freed space to 89%. This morning I reboot and try again and now I can login writing users names and passwords. Maybe, full disk was the problem.  
I have just read your reply now so I have not tried the commands you say.

Thank you very much for your help!  :)

How can I put this thread resolved?

---

### Post by DuckHook on 2016-05-01
Glad you finally solved the problem. The *solved* option is in "thread tools" in the upper right of the thread toolbar.

You've taught me something: to look for simpler reasons than to assume complex ones all the time.

As a final note, you may wish to look at offloading some of your data or getting a larger HDD. It is not a good idea to run your disk so close to full in Linux. Quite aside from the wonky behaviour that you've just had to deal with, the file system starts to fragment when the disk is too full.

Good luck and Happy Ubuntu-ing!

---

