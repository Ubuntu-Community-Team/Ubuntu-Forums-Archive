---
title: "nautilus crash"
date: 2007-08-29
forum: Desktop Environments
---

### Post by analyzer on 2007-08-29
Hello everybody

For a couple of weeks the amount of crashes of nautilus have been increased.
1.All icons on the Desktop disappear
2.I can not open a new nautilus window
3.Applications like GIMP and VLC are still working

By means of these points, I think nautilus crashes. 

```
nautilus -c
```

No errors.
```
nautilus --browser

Initializing gnome-mount extension


```
No window open.

```
ps -Al | grep nautilus

0 S  1000  2198  1958  0  78   0 - 32627 -      pts/0    00:00:00 nautilus
```
Shows one running instance of nautilus

Unfortunately there is no nautilus.log file at the home directory. Dito no error messages in Xorg.log or  syslog.

Thanks.

My system: Ubuntu Feisty Fawn.

---

