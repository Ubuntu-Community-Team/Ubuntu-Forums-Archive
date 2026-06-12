---
title: "command line to gui"
date: 2006-04-13
forum: Desktop Environments
---

### Post by usreddieb on 2006-04-13
Hello,
I'm not new to computers I've worked with Macs and windows. I'm a guru with graphics with the platform mentioned but I'm new to linux. So like just I installed ubuntu last night for about 4 times and after installations and all four times I got a error message about X?? something and now I can only run from the command line and not the GUI interface. Thats fine with me because it gives me the oppertunity to learn command which draws this question. What can I type in command line to run gnome? Is this possible? If any of you know a fix to why it doesn't boot GUI, please lend a hand. Thank you.

---

### Post by zubrug on 2006-04-13
What graphics card do you have.
Is this a laptop

---

### Post by usreddieb on 2006-04-14
Yup, it's a laptop. It seems to be reading the card correctly or at least it I see it during up.

---

### Post by aysiu on 2006-04-14
Try these:

```
startx
```
```
sudo /etc/init.d/gdm restart
```
```
sudo dpkg-reconfigure xserver-xorg
```
```
sudo apt-get update
sudo apt-get install ubuntu-desktop
```

---

### Post by John_the_linux_newbie on 2006-04-14
[QUOTE=aysiu]Try these:

```
startx
```
```
sudo /etc/init.d/gdm restart
```
```
sudo dpkg-reconfigure xserver-xorg
```
```
sudo apt-get update
sudo apt-get install ubuntu-desktop
```[/QUOTE]

THANKS!
I managed to geek up my system enough so that the gui wouldn't load on startup.  This thread made life easier - startx launched the gui and then sudo apt-get install ubuntu-desktop reenabled the GUI at startup.

---

