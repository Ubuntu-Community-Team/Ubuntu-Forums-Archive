---
title: "X11 initialization failed"
date: 2014-06-05
forum: Desktop Environments
---

### Post by josejohn on 2014-06-05
Hi,
 I am running
Ubuntu 12.04.4 LTS
I have installed Xserver and am logging using
$ssh -X username@machineip
When I start eclipse, it gives me this error

** (java:3174): WARNING **: Command line `dbus-launch --autolaunch=6ff9a50c9edfab7a264133b300000009 --binary-syntax --close-stderr' exited with non-zero exit status 1: Autolaunch error: X11 initialization failed.\n
Eclipse: Cannot open display:

even gedit gives me this

Cannot open display: 

How do I fix it? 
Have tried going through the forum, removing .Xauthority does not help.
Any input will be of great help. Thanks

---

### Post by tgalati4 on 2014-06-05
When having problems with an X-forwarding, I try the following:

```
ssh -2 -Y user@machine
```

Then run some small programs such as *xeyes*.

---

