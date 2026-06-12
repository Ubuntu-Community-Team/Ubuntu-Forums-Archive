---
title: "Numlock on login in 13.10 - numlockx not working"
date: 2013-11-10
forum: Desktop Environments
---

### Post by tompiedom on 2013-11-10
Hello, 

I'm trying to activate my numlock by default on my login screen, but it's not working.
Like many people have suggested already, I tried to add **greeter-setup-script=/usr/bin/numlockx on** (and yes numlockx is available at that location :)). 
Unfortunately I still have to activate numlock manually at login. 

Strange side-effect, I have to press numlock _twice_ to actually activate the numeric keys, with or without the setup-script. 

There's no option to set in my BIOS, and I haven't activated any particular keyboard settings myself.

For your information: I'm using Ubuntu 13.10 (upgrade from 13.04) with the default dashboard.

Many thanks already for your suggestions!

Tom

---

### Post by stinkeye on 2013-11-10
Where are you putting "**greeter-setup-script=/usr/bin/numlockx on**"?
In Saucy I don't have an **/etc/lightdm/lightdm.conf**, which was what I used in Raring, so I put it into
**/etc/lightdm/lightdm.conf.d/50-unity-greeter.conf**

---

### Post by tompiedom on 2013-11-10
I did try both of those files, but nothing seems to work.

---

### Post by stinkeye on 2013-11-10
Does the **/usr/bin/numlockx on** command work when you run in terminal?

---

### Post by tompiedom on 2013-11-10
Yes it does:
```

$ numlockx on
$ numlockx status
Numlock is on

```

I just realised that the title might suggest that. Numlockx is working, the scripted solution with numlockx doesn't work.

---

### Post by tompiedom on 2013-11-11
While I was trying out suggestions on [this site]("https://help.ubuntu.com/community/NumLock") I noticed something strange. 
When I start typing a number, numlock is active by default. But when I start typing my password, which starts with a non-digit character, numlock is disabled... 

So lets say my password is **1$pec1al**, I would type 1$pecal.

---

