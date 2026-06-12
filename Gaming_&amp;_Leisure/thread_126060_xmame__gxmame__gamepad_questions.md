---
title: "xmame / gxmame / gamepad questions"
date: 2006-02-05
forum: Gaming &amp; Leisure
---

### Post by renzokuken on 2006-02-05
ok, firts off, i have xmame and gxmame running and am able to load games fine. however, when the game starts, my screen goes black. i have found a way round this as follows 

1. load the game
2. screen goes black
3. switch to another terminal (ctrl + alt + F6)
4. switch bacvk to original terminal (ctrl + alt + F7 )

and i have my desktop back complete with the loaded game, anyone know why this happens or a way of avoiding it.

secondly, can anyone recommend a good game pad to use with linux specifically for zsnes and xmame.

thanks

---

### Post by Pragmatist on 2006-02-05
My friend has a very similar problem which he solved by using xmame-SDL which you can install with apt-get/synaptic

I've used the Saitek P880 Dual Analog  and the Logitech Dual Action.  I like them both, but I don't know the exact game your referring to so I can't say whether these will work with that game.

---

### Post by Biased turkey on 2006-02-06
I iubstalled xmame-SDL using synaptic and doesn't have any problem at all.
How did you install x mame? compiling from source, using Synaptic or from a .deb package ?

P.S. I lnstalled Xmame mostly to play depth-charge.

---

### Post by Pragmatist on 2006-02-06
My friend and I both installed xmame-x via synaptic

---

### Post by renzokuken on 2006-02-06
um lets see.... i think this is the order i did it in

1. installed xmame-x from repos/synaptic
2. installed gxmame deb from a thread in here somewhere
3. tried ur suggestion and installed xmame-sdl from synaptic

......but no change with problem, still got black screen, easy to get around though, just mildly annoying i guess.

should i have removed xmame-x before installing xmame-sdl?

---

### Post by Pragmatist on 2006-02-06
I would definitely try uninstalling them both and then just reinstalling xmame-sdl  The whole thing shouldn't take more than a few minutes.

If your ambitious, you can try this:

```
CTRL-ALT-F6
```
```
/etc/init.d/gdm stop
```
```
CTRL-ALT-F6
```
```
startx
```

Try running xmame that way and tell me if you still have a problem.  If you do, the areas I would investigate: 

1. Power management stuff like ACPI:  Try temporarily turning it off.
2. Framebuffers

Also, check this out: [http://x.mame.net/mailinglist.html](http://x.mame.net/mailinglist.html)

---

### Post by akiro.yamamoto on 2006-02-06
I'm currently using a Logitech Dual Action Game Pad.
It's USB and was automatically detected and recognised, no modifications were
necessary to get it to work with my games.
BTW: Samurai Showdown 4 really kisks a%%. LOL.

---

### Post by 8bit on 2006-02-06
Hate to Hijack but...

I tried installing xmame from the universe repository but it's not there. What could I be doing wrong.

Also, I've noticed that some have installed mame for windows using wine. Is the win version that much better or less buggy? Why would you want to do this?

---

### Post by akiro.yamamoto on 2006-02-06
I think you have to enable the Multiverse Repository!

---

### Post by akiro.yamamoto on 2006-02-06
Use Synaptic and go to Repositories and enable Universe and Multiverse rpos. ;)

---

### Post by leech on 2006-02-06
[QUOTE=8bit]Hate to Hijack but...

I tried installing xmame from the universe repository but it's not there. What could I be doing wrong.

Also, I've noticed that some have installed mame for windows using wine. Is the win version that much better or less buggy? Why would you want to do this?[/QUOTE]

I have no idea why you'd want to install the windows version, with the small exception of the fact that xmame usually trails slightly behind on the version of release of the official mame.

While speaking of versions of mame, I will recommend installing the xmame packages from the Debian server, they are a whole lot of versions ahead of the ones in Multiverse.

[ftp://ftp.debian.org/debian/pool/non-free/x/xmame](ftp://ftp.debian.org/debian/pool/non-free/x/xmame)  You'll want to get the xmame-sdl, xmame-common and xmame-tools

Leech

---

