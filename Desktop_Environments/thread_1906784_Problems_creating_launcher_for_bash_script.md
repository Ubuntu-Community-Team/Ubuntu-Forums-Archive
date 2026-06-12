---
title: "Problems creating launcher for bash script"
date: 2012-01-09
forum: Desktop Environments
---

### Post by diamond_D on 2012-01-09
I have a bash script that I use to secure delete the trash. Here is the code

```
#!/bin/bash
/usr/bin/srm -lrvz $HOME/.local/share/Trash/* | zenity --auto-close --auto-kill --progress --width 350 --text "Securely Emptying the Trash - Please be patient." --title "Securely Erasing Files"
```My OS is Ubuntu 11.10 and I tried creating a launcher for this bash script using this method:
```

gnome-desktop-item-edit ~/Desktop/ --create-new
```It does nothing.

When I run the srm command above from the command line, the scripts works and I get the zenity popup. I'm just waiting for it to finish to I can see if it terminates properly. I'm kind of a N00b to bash scripting so any assistance is greatly appreciated.

---

### Post by Kemon on 2012-01-10
Looking for this one?:
> ln -s file.sh shortcut

---

### Post by diamond_D on 2012-01-12
Actually I did some debugging of the script and was getting an error message saying "Bad interpreter". I checked my syntax and everything looked good but I noticed at the bottom of VIM the file format was showing [dos]. I started writing this script on Windows and then transferred it to my Linux box thinking that it should still run but I guess not. 
 
When I retyped the code in Linux it worked perfectly.

---

