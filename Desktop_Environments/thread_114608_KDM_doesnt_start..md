---
title: "KDM doesnt start."
date: 2006-01-08
forum: Desktop Environments
---

### Post by npodges on 2006-01-08
For some reason, my computer froze and restarted. when i booted back up, it didnt go into kde, but to tty1... i logged in, and did "sudo kdm" and then "startx" and it boots up fine and everything seems normal. the only problem is that right now, i'm running as root, and i really dont want to be. if i try to end the session, it reboots, and does the samething. how do i make KDE load normally?

---

### Post by Divan Santana on 2006-01-09
Ok, no problem.

Not sure if this is the best way but simply install bum ( from terminal type apt-get install bum )

Then open bum from graphical view and tick kdm.

That simple

---

### Post by Thirsteh on 2006-01-09
npodges, the fact that you did startx after you launched KDM could indicate that KDM is still not working as it would automatically spawn an X session for you. If there is no luck with KDM whatsoever, keep in mind that you can use all the other window managers as well, e.g. Ubuntu's GDM, or disable all login managers completely and do a console login followed by "startx" --- I consider that the "hardcore" way ;)

---

### Post by npodges on 2006-01-09
heh, thanks. well let me say i tihnk the first time, i did startx before kdm, and it loaded into kde right away... only at like 640x480. if i start kdm first, nothing happens, but then when i startx, everything works normally(that is except that i'm still logged in as root)

---

### Post by npodges on 2006-01-10
does nobody know how to fix it so taht it just boots correctly? is there any more info i can give that would suggest anything?
-thanks

---

### Post by Adrian on 2006-01-10
[QUOTE=npodges]does nobody know how to fix it so taht it just boots correctly? is there any more info i can give that would suggest anything?
-thanks[/QUOTE]

I don't really know, but you can try this:
```
sudo dpkg-reconfigure kdm
```

---

### Post by npodges on 2006-01-10
alright, well that didnt work. actually i may be worse off now. here's my deal:(or rather, here was my deal)
$kdm
only root wants to run kdm!
$sudo kdm
$startx
(it attempts to start, but gives some errors, including saying that it can't find any screens)
$sudo startx
then, it starts x just fine, and runs KDE, but as root the whole time.

now, things have changed a bit
everything starts the same, but when i do "sudo startx"
it attemps to start... it gives me a cursor and sorta a checkered grey background. if we switch to tty1, we see:
```
..
AUDIT: Tue Jan 10 17:55:16 2006: 6996 X: client 1 rejected from local host
Xlib: connection to ":0.0" refused by server
Xlib: no protocol specified
```
it repeats that like infinity times, then finally says ```
giving up.
xinit:unable to connect to X server
xinit: Server error.
xauth: error in locking authority file /home/nick/.Xauthority
```

---

### Post by npodges on 2006-01-10
if i have to, i can reinstall kdm. is that the case?

---

### Post by veloct on 2006-01-10
```
sudo dpkg-reconfigure xserver-xorg
```

That should take care of the screen issue.  Do you have GDM installed? If so, 

```
sudo apt-get remove gdm
``` 

and then,

```
sudo dpkg-reconfigure kdm
```

hopefully that helps

---

### Post by npodges on 2006-01-10
okay thanks. that actually did help a lot.. i just reconfigured x, and it works fine now.
although... while i was not able to use kde, i just isntalled xfce via xubuntu-desktop. 
anyhow, i tihnk kde is working fine, now, so thanks a lot!

---

### Post by npodges on 2006-01-10
acutally, i spoke a little too soon. it doesnt work just yet, but i'm hoping that's because i didnt reconfig kdm afterwards, so i'll try that

---

