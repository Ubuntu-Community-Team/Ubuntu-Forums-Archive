---
title: "do I really need xgl? (running compiz with nvidia, gutsy)"
date: 2007-10-30
forum: Desktop Effects &amp; Customization
---

### Post by sgleo87 on 2007-10-30
After upgrading to gutsy and then installing the latest nvidia drivers (100.14.23) I was getting a white screen after my desktop loaded. So then I uninstalled compiz: nothing changed. Then I removed xserver-xgl and then everything was fine. I reinstalled Compiz and it runs just fine without xgl and I don't really notice any difference. So what exactly do I need xgl for anyhow? Or am I just fine without it?

---

### Post by MrFSL on 2007-10-30
There used to be a time when Xgl was necessary however the composting code has already been merged into Xorg so it is no longer necessary nor recommended.

---

### Post by santiagoward2000 on 2007-10-31
> **MrFSL said:**
> There used to be a time when Xgl was necessary however the composting code has already been merged into Xorg so it is no longer necessary nor recommended.

That's for NVidia cards, right? I can't run Compiz on my ATI without XGL...

---

### Post by MrFSL on 2007-10-31
Ooops!

Jumped the gun on that last response. Not the foggiest idea about configuring ATI cards.

---

### Post by santiagoward2000 on 2007-10-31
> **MrFSL said:**
> Ooops!

Jumped the gun on that last response. Not the foggiest idea about configuring ATI cards.

LOL. I'm not too sure about it, but I think NVidia cards use AIGLX, which is installed together with their drivers. Most ATI cards will need XGL to run compiz, and you'll have to install xserver-xgl from the repositories.
Still, XGL has been greatly improved in Gusty. It runs smoother, and you no longer have to create a new session to run it.

---

### Post by FuturePilot on 2007-10-31
If you have a Nvidia card, no, you don't need XGL. Since xorg 7.1 XGL is no longer needed for Nvidia cards. ATI users may still need XGL unless you get the very latest driver as it has support for AIGLX.

---

