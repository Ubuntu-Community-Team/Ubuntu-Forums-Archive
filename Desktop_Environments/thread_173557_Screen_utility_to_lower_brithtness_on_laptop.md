---
title: "Screen utility to lower brithtness on laptop?"
date: 2006-05-10
forum: Desktop Environments
---

### Post by carlos123 on 2006-05-10
Hi there, 

I just installed Ubuntu and am quite impressed.  Just wondering if there is some kind of screen adjusting utility (like there is under Windows XP) to diminish the screen brightness and save on battery power?  

Under Windows XP the utility is part of the menu that comes up when I left click on the battery icon in the task bar.  It allows me to set all kinds of things that affect battery power.  The Power Management utility under GNOME is EXTREMELY simple and does not allow for much control.  

The battery power is subsequently draining much faster under Ubuntu than it does under Windows XP. 

Any tips or tricks would be appreciated.  Thanks.  

Carlos

---

### Post by 23meg on 2006-05-10
Do your keyboard shortcuts for adjusting brightness not work in Ubuntu?

---

### Post by 23meg on 2006-05-10
You should also have an "lcd" entry that you can manipulate via the echo command probably somewhere under /proc/acpi . I have /proc/acpi/toshiba/lcd , and I can adjust brightness with the command ```
sudo echo "brightness: n" > "/proc/acpi/toshiba/lcd"
``` where n is a value between 0 and 7 (my screen has 8 adjustable brightness steps). For this to work I had to change ownership of "lcd" to my user with ```
sudo chown *system_username* /proc/acpi/toshiba/lcd 
```

---

### Post by carlos123 on 2006-06-13
Thanks very much for your additional input 23meg.  I did not see your post until today as my Ubuntu internet is REAL slow (even with ipv6 use turned off) and I have had lots of other configuration issues to attend to.  

I do indeed have an LCD entry but it is a directory.  Within that directory there is a file called brightness.  And if I cat that file I get the following appearing on the screen...

carlos@laptop:/proc/acpi/video/GFX0/LCD$ cat brightness
levels:  80 60 0 20 40 60 80 100
current: 0

I tried....

carlos@laptop:/proc/acpi/video/GFX0/LCD$ echo "brightness: 20" > "brightness"
bash: echo: write error: Invalid argument
carlos@laptop:/proc/acpi/video/GFX0/LCD$ echo "current: 20" > "brightness" 
bash: echo: write error: Invalid argument
carlos@laptop:/proc/acpi/video/GFX0/LCD$ sudo echo "current: 20" > "brightness"
echo: write error: Invalid argument

So I am not sure as to how to change the value of current yet.  The file itself appears to be empty or at least it is when I gedit it.  

Don't really know what I am doing inside the /proc tree.  Don't understand where the info comes from that appears when I cat a file under that tree if it's not in the file.  Nor do I understand where one can learn the various options that can be set by writing something to the file.  

Any further input or suggestions would be appreciated.  

Thanks.  

Carlos

---

