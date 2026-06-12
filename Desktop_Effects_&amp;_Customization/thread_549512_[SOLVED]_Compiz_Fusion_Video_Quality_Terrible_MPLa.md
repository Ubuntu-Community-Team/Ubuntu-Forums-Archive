---
title: "[SOLVED] Compiz Fusion Video Quality Terrible: MPLayer?"
date: 2007-09-12
forum: Desktop Effects &amp; Customization
---

### Post by 1337455 10534 on 2007-09-12
I have never used MPlayer before, but after experiencing bad sound quality on VLC and terrible clarity on Totem I thought I might give "The Ultimate Movie Player For Linux" a try. The problem (MAY OR MAY NOT BE) that I have Compiz Fusion. MPlayer refuses to install through Synaptic, Add/Remove, and even the all mighty terminal. :

```

family@The-Family-Desktop:~$ sudo apt-get install mozilla-mplayer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  mozilla-mplayer: Depends: mplayer (>= 2:0.99+1.0pre7) or
                            mplayer-nogui (>= 2:0.99+1.0pre7) but it is not going to be installed or
                            mplayer-powerpc (>= 2:0.99+1.0pre7) but it is not installable or
                            mplayer-g4 (>= 2:0.99+1.0pre7) but it is not installable
E: Broken packages

```

Yes, the one
```

sudo apt-get install mozilla-mplayer

```
line will install the plugin and the player.

When using Synaptic:
I (Ctl + F) "mplayer" and select the "mplayer" package:
> 
mplayer:
 Depends: libggi2 (>=1:2.2.1) but it is not installable
 Depends: libopenal0a  but it is not installable
 Depends: libsvga1  but it is not installable
 Depends: mplayer-skins  but it is not installable


Can anybody tell me what is wrong here?
One more thing, I did add trevinos repos and a PubKey err messege showed up. Software Sources kept on showing me the err and asking me to Reload the information again and again. So finally I just said close.

---

### Post by jsully1 on 2007-09-12
You may want to try using the X11 video setting under preferences -> video.

---

### Post by 1337455 10534 on 2007-09-14
Umm, that doesn't help at all.
Which preferences menu?
What do I change the settings to?

I finally got MPLayer, and the quality is better all around, but it wont go fullscreen

---

### Post by 1337455 10534 on 2007-10-09
It works on Gutsy...

---

