---
title: "Strange VNC problem."
date: 2007-05-14
forum: Desktop Environments
---

### Post by Garf on 2007-05-14
Hi Everyone...

I have a weird problem with VNC... It took me a while to get it to work cause I was too stupid to set it to allow people to view my desktop through the gui...

Before that I did sudo aptitude install vnc4server... anyway don't know if I needed to do that..

Anyway I tried connecting to my ubuntu computer from my winxp laptop, and it worked, but the screen would not refresh. I could move the mouse around, and move things around on the desktop, and also I could type..

But nothing other then that first screen grab was able to be seen on the windows machine...

Can anyone see a reason for this. I am running desktop effects so I am thinking maybe that has something to do with it.

Anny help much appreciated.

---

### Post by AZzKikR on 2007-05-14
I have the same problem. I can connect from Terminal Server Client to my WinXp laptop with no problems. Screen refreshes nicely, good performance and whatnot. However, when connecting from WinXP to my Feisty desktop, the screen will not refresh. I've tried several other VNC clients but they all show the same disfunctions. 

I am not using any desktop effects. My video card is an ATI X800, maybe that's the issue?

---

### Post by Rhubarb on 2007-05-14
While I don't have windows to test this out on, I have noticed that if you try to connect to a pc running Feisty with the Beryl effects turned on, the screen will not refresh on the client pc.
Once Beryl is turned off (and hence Metacity is on) on the vnc server, everything works nicely.

---

### Post by Garf on 2007-05-14
Yeah I figured it might be...

Probably should have tested it :)

But anyway it there a way to have beryl not on for a user logged in through vnc?

> **Rhubarb said:**
> While I don't have windows to test this out on, I have noticed that if you try to connect to a pc running Feisty with the Beryl effects turned on, the screen will not refresh on the client pc.
Once Beryl is turned off (and hence Metacity is on) on the vnc server, everything works nicely.

---

### Post by lazyart on 2007-05-14
What you need is a different VNC.

```
sudo apt-get install x11vnc
```

Launch it this way:
```
x11vnc -noxdamage
```

Since you likely have vino running, this will listening on display 1, which is port 5901 or *computername*:1

When I want to access my ubuntu machine (named calvin) I launch VNC from the windows box and use calvin:1 as the server name.

When i get in I have my beryl desktop.  I added the launch command to my sessions and it will be there after rebooting.

---

### Post by fastpakr on 2007-05-17
What repository does xllvnc come out of?  I'm getting a 'could not find package' on that.

---

### Post by davmac on 2007-07-05
It is not xll (xray lima lima) it is x11 (xray one one)

---

