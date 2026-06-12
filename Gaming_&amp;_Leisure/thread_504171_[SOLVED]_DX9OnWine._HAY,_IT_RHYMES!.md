---
title: "[SOLVED] DX9OnWine. HAY, IT RHYMES!"
date: 2007-07-18
forum: Gaming &amp; Leisure
---

### Post by BlahMan_of.Doom on 2007-07-18
directx.log: [http://pastebin.com/m3e5f27e9](http://pastebin.com/m3e5f27e9)
dx error.log: [http://pastebin.com/m479dc671](http://pastebin.com/m479dc671)
Those are the logs from when I attempt to install DirectX 9 on Wine. Can anyone help?

---

### Post by cogadh on 2007-07-18
Sure, I can help, this is an easy one. :)

Don't install DirectX on Wine, it will break it. Wine already has DX9 support, so you don't need to install it anyway. From the official Wine FAQ:
> Wine itself provides a DirectX implementation that, although it has a few bugs left, should run fine. Wine supports DirectX 9.0c at this time. Plans for DirectX 10 are underway.

If you attempt to install Microsoft's DirectX, you'll run into some problems. You can install the runtime, but it will not run. The runtime needs access to the Windows drivers, and Wine cannot access them for obvious reasons. The only native Microsoft DLLs that could be useful anyway are the d3dx9_xx.dll type ones, and these require you to accept Microsoft's license. Regardless, don't try and do this.
[http://wiki.winehq.org/FAQ#head-fbaa851e07d7484640cc10b6d0c48abc741260b2](http://wiki.winehq.org/FAQ#head-fbaa851e07d7484640cc10b6d0c48abc741260b2)

---

### Post by BlahMan_of.Doom on 2007-07-19
Whaaat..so I can't play DirectX 9 games on Ubuntu?

I read the thing, but I can't use DirectX9 in CS:S.

---

### Post by cogadh on 2007-07-19
Yes, you can play DX 9 games, as I said, Wine already has DX 9 built into it. However your hardware and the game must both support DX 9 interfaces. If you don't have a fully DX9.0c compatible video card, Counter Strike: Source won't let you use higher than DX 8 interfaces.

Have you already followed the CS:S config advice on AppDB?
[http://appdb.winehq.org/appview.php?iVersionId=3731](http://appdb.winehq.org/appview.php?iVersionId=3731)

---

### Post by bastiegast on 2007-07-19
Fact: > Wine supports DirectX 9.0c at this time
Your interpretation : > Whaaat..so I can't play DirectX 9 games on Ubuntu?


:-\"

---

### Post by BlahMan_of.Doom on 2007-07-19
Why don't you read the whole reply :mad:

Okay I'll follow that guide.

> **cogadh said:**
> Yes, you can play DX 9 games, as I said, Wine already has DX 9 built into it. However your hardware and the game must both support DX 9 interfaces. If you don't have a fully DX9.0c compatible video card, Counter Strike: Source won't let you use higher than DX 8 interfaces.

Have you already followed the CS:S config advice on AppDB?
[http://appdb.winehq.org/appview.php?iVersionId=3731](http://appdb.winehq.org/appview.php?iVersionId=3731)

I have a sig for a reason. I believe that an 8800GTS can do more than DirectX 9.

---

### Post by BlahMan_of.Doom on 2007-07-19
> **BlahMan_of.Doom said:**
> Why don't you read the whole reply :mad:

Okay I'll follow that guide.



I have a sig for a reason. I believe that an 8800GTS can do more than DirectX 9.

Okay DirectX 9 works, but in CS:S I can't use anti-aliasing.

---

### Post by cogadh on 2007-07-19
You'll need to use the Nvidia settings tool to set AA globally, Wine usually can't pass AA parameters (for some reason).

BTW - I don't actually read sigs anymore, almost no one puts anything useful in them (including me). And yes, the 8800 GTS can do DX 9 and 10.

---

### Post by BlahMan_of.Doom on 2007-07-19
Okay cool. But is it possible to get the same performance that I get on Windows on Ubuntu?

---

### Post by cogadh on 2007-07-19
Yes, it is possible, but it really depends on your system and Wine configuration. For some people, performance is equal to or far better than Windows. Others can barely squeeze 20 FPS out on Linux while pulling 60+ FPS on Windows. On my system, I could barely get the game to launch. All of my Steam-based games are pretty much the only thing I still use Windows for.

---

### Post by BlahMan_of.Doom on 2007-07-19
Oh okay. Well, I'm quite satisfied with today. I got DX9 to work. Thanks! [SOLVED]

---

