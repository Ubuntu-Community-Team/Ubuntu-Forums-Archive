---
title: "How did I hide my grub2 menu?"
date: 2010-05-13
forum: Desktop Environments
---

### Post by ario on 2010-05-13
I searched a lot in internet and found that everyone have the same problem as me. When installing ubuntu 9.10 and earlier, It will install grub2 as its boot loader. It is a good ability for some people to hide grub menu until pressing shift key during boot sequence. But grub2 will not hide menu after it detects another OS.
I pressed Alt+F2 and typed **gksudo nautilus**
Then in a file manager window navigated to /etc/default and opened **grub** file. In opened **gedit** window in Edit menu clicked preferences and deselected **Enable text wrapping** or something like this.
Then in file set the **GRUB_HIDDEN_TIMEOUT** value to 10 (for then seconds wait for pressing shift key). Saved file and again navigated to /etc/grub.d and opened **30_os-prober** file.
In the file changed the line
```
if [ "x${found_other_os}" = "x" ] ; then

```
to
```
if [ true ] ; then
```
opened a terminal and typed
```
sudo update-grub
```
then after it prompted ```
**done.**
``` rebooted my PC and Viola!

---

### Post by mister_playboy on 2010-05-14
Thanks for the tip. :)

---

