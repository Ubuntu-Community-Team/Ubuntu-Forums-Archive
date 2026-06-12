---
title: "Need help with XGL on a Dell 9400 Laptop w/ Nvidia Graphics"
date: 2006-09-11
forum: Desktop Environments
---

### Post by Psycs on 2006-09-11
I have a Dell 9400 laptop running Dapper.  Specs: 

Core Duo T2300 @ 1.66Ghz
512 MB Ram
60 GB Hard Drive
17-inch WXGA+ (1440 x 900)
Nvidia GeForce 7800 Go - 256 MB

I cannot get XGL/Compiz to run.  

Twice I have had install Ubuntu from scratch after failing miserably.  

Also twice I have managed to (apparently) install everything properly with Ra211's Automatic Installation Script. But several seconds after I logg into the XGL session, a black screen briefly appears and I am sent back to the login screen.

Can anyone please help me and recommend best way to install XGL?

Thanks!

---

### Post by Dinerty on 2006-09-11
> **Psycs said:**
> I have a Dell 9400 laptop running Dapper.  Specs: 

Core Duo T2300 @ 1.66Ghz
512 MB Ram
60 GB Hard Drive
17-inch WXGA+ (1440 x 900)
Nvidia GeForce 7800 Go - 256 MB

I cannot get XGL/Compiz to run.  

Twice I have had install Ubuntu from scratch after failing miserably.  

Also twice I have managed to (apparently) install everything properly with Ra211's Automatic Installation Script. But several seconds after I logg into the XGL session, a black screen briefly appears and I am sent back to the login screen.

Can anyone please help me and recommend best way to install XGL?

Thanks!

Hi there mate

I have installed xgl/compiz on the model below yours (9300) and all works fine . Check this guide out I highly recommend it:

[https://help.ubuntu.com/community/CompositeManager/Xgl](https://help.ubuntu.com/community/CompositeManager/Xgl)

---

### Post by Psycs on 2006-09-11
Hey, Dinerty.  Thanks a lot for the answer and good news. I will try it out in the evening and post the results here.

---

### Post by Psycs on 2006-09-11
I have good news and bad news.

The good news is that I was able to get Xgl and Compiz running.  However, the bad news is that my Gnome panels and window borders/buttons also disapeared, even under my normal Gnome session!

Right know all my windows lack the "title bar" (or whatever its name is), the minimize, maximize, and close buttons and they cannot be resized or moved.

I would post a screenshot, but it becomes impossible given my current situation. 

:mrgreen:

---

### Post by Dinerty on 2006-09-11
> **Psycs said:**
> I have good news and bad news.

The good news is that I was able to get Xgl and Compiz running.  However, the bad news is that my Gnome panels and window borders/buttons also disapeared, even under my normal Gnome session!

Right know all my windows lack the "title bar" (or whatever its name is), the minimize, maximize, and close buttons and they cannot be resized or moved.

I would post a screenshot, but it becomes impossible given my current situation. 

:mrgreen:

well at least you got abit further this time ! :D. Is this link any use to you?

[http://www.compiz.net/topic-4187-windows-borders-missing](http://www.compiz.net/topic-4187-windows-borders-missing)

---

### Post by vblanton on 2006-10-12
That happened because gnome-window-decorator didn't run for some reason. Try pressing alt-f2 or opening a terminal and type:
```
gnome-window-decorator &
```

Does that do it?

---

