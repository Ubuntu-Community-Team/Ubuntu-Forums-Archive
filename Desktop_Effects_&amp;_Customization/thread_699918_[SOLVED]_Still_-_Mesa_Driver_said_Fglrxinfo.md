---
title: "[SOLVED] Still - Mesa Driver said Fglrxinfo"
date: 2008-02-17
forum: Desktop Effects &amp; Customization
---

### Post by vinutux on 2008-02-17
I am totally confused. Read a lot of thead from this forum and others from googling. but not success.
I am ati x700 user installing latest driver from ATI/AMD site . After installing and rebooting fglrx info said 

display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)

I don'nt know how to fix it several time removing and hacking x.org and refreshing it or create new one with "dpkg-reconfigure xserver-xorg". But i remember it was worked for me for some days before and i am able to use compiz.The problem start after i am install driver created "build" script from ati installer.
.................................................

Plz help

---

### Post by vinutux on 2008-02-19
haaaaaaaaaaayyyyyyyy pleeezzzzzzzzzzz

---

### Post by farbror_ace on 2008-02-19
Try envy maybe.

---

### Post by Hobnobb on 2008-02-19
Vinutux

Maybe you have a proprietary driver issue which means that your standard xorg driver is not linked to the ATI proprietary driver, you could try this to link them

```
cd /usr/lib/xorg/modules/
```
First check if there is a libglx.so file in this directory, if so rename this file to something else.
Then

```
sudo ln extensions/libglx.so.169.09 libglx.so.169.09
sudo ln extensions/libglx.so libglx.so
```

restart xserver with Ctrl+Alt+Backspace

If this doesn't work rename the original libglx.so file to this name
Good luck and keep me posted!

---

### Post by vinutux on 2008-02-20
There is no "libglx.so" on usr/lib/xorg/modules/ but i fount libglx.so in [COLOR="Red"]**usr/lib/xorg/modules/extensions**[/COLOR]

..........Plz help meeeeeeeeeeeeeeee

---

### Post by Hobnobb on 2008-02-22
The intended trick is to link the libglx.so in the extensions directory to a link in the modules dir.
But this only works if u use glx.
Anyway this trick only worked for a little while for me and i could use compiz. But later this got broken again and I got the mesa driver back and I could not get direct rendering to work again.
Now I installed hardy (devolopment ubuntu which will be released in april) and  installed the xorg-driver-fglrx the ubuntu way and compiz worked at once and got the ati radeon driver back in fglrxinfo.. This is btw the latest driver from febr 13 2008 so the hardy repository is kept well updated. 
There are many others who can't get the fglrx driver work properly in gutsy. So my advice is to wait till hardy gets released in april or download hardy development now; I use it 2 days now and compiz and everything else works stable and fast.

Good luck

---

### Post by vinutux on 2008-02-22
Solved.....................Thnks alllllllllllll...................What i do exactly is uninstall my fglrx files(may be curruped) using "envy" and manually install ATI driver from ATI/AMD site and restart. I think envy remmove all my fglrx file make me fixing prob. Any way thanks all the guys

fgrxinfo now says

[COLOR="RoyalBlue"][B]display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON X700 PRO
OpenGL version string: 2.1.7281 Release[/B][/COLOR]

....................................................................................................|

:guitar:

---

### Post by vinutux on 2008-02-22
Solved.....................Thnks alllllllllllll...................What i do exactly is uninstall my fglrx files(may be curruped) using "envy" and manually install ATI driver from ATI/AMD site and restart. I think envy remmove all my fglrx file make me fixing prob. Any way thanks all the guys

fgrxinfo now says

[COLOR="RoyalBlue"][B]display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON X700 PRO
OpenGL version string: 2.1.7281 Release[/B][/COLOR]

....................................................................................................|

:guitar:

---

