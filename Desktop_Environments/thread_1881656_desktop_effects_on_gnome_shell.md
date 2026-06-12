---
title: "desktop effects on gnome shell"
date: 2011-11-15
forum: Desktop Environments
---

### Post by js_theking on 2011-11-15
I'm running Ubuntu 11.10 and recently downloaded Gnome Shell and CCSM. I tried to activate some visual effects (woobly windows, 3D-cube etc) but it's not working at all.

I have a Nvidia geforce GT430 and my driver is installed and in used. I'm am also using gnome classic.
Is there any way to activate visual effects ? It's pretty plain and I'm using it as my main OS. :(

Thanks !

---

### Post by Copper Bezel on 2011-11-16
Gnome Shell doesn't use Compiz at all. It uses Mutter, which grew up from Metacity. The Gnome project has always had very different goals from Compiz, and the understated effects in Shell reflect that.

However, Mutter via Gnome Shell is much easier to write plugins for through the Shell's extension base, and some people are hoping that the community will hash together some Compiz-style snazz for it. There's a [_proof-of-concept Trailfocus-type extension_]("http://www.webupd8.org/2011/10/gnome-shell-focus-effects-extension.html") available right now, if you want to try that.

I have to say that a desktop cube wouldn't really work with Shell, though. Would it rotate up and down instead of side to side? = )

---

### Post by js_theking on 2011-11-16
Oh that's why ! Thank you.

---

