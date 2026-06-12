---
title: "Quake 3 problems (audio and video)"
date: 2005-06-01
forum: Gaming &amp; Leisure
---

### Post by noerej on 2005-06-01
Hello people,

I've installed Quake 3 from the Windows version. When I try to run it I have no sound.
This is the output regarding the sound I get :

------- sound initialization -------
Could not mmap dma buffer PROT_WRITE|PROT_READ
trying mmap PROT_WRITE (with associated better compatibility / less performance code)
/dev/dsp: Input/output error
Could not mmap /dev/dsp

---

### Post by thrift on 2005-06-01
Are you using alsa for the sound?  I've had this problem before, there are plenty of ways to get around it.  I'd do a google search for your mmap error...

---

### Post by noerej on 2005-06-01
Yes, I'm using ALSA for sound. I found that entering echo "quake3.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss as root helps. Now it'd be nice if I was able to put it in a nice little script which I can run every time I run Quake 3. Up until now I haven't been able to do this, despite numerous attempts.
Are there any other workarounds for this?

---

### Post by thrift on 2005-06-01
simply add it on startup.  

You don't need it every time you start quake if it's already been done.  /etc/init.d/gdm would be a great place for it, since your not going to be starting quake without X and GDM loads X.

---

### Post by noerej on 2005-06-02
I added it to the file you said, and sound now works on startup! Much thanks thrift!

But now when I connect to a multiplayer game, the game hangs just before entering the game. Any ideas?

---

### Post by tomdeb on 2005-06-02
> echo "quake3.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss 
In my case this didn't, don't ask me why.

I had to install esound-clients via
```
sudo aptitude install esound-clients
``` 

whish provides esdctl command

then create a script quake3-esd-sh

```

esdctl off
sleep 5
quake3 +set "fs_game osp"
esdctl on

```

hope this helps

---

### Post by noerej on 2005-06-02
Well, I don't know if the hangups are related to the sound, but that would seem odd to me. In single player mode the game hangs when I finish a match, and in multiplayer it hangs on the screen "waiting for snapshot".

---

### Post by noerej on 2005-06-03
*bump*

---

