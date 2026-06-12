---
title: "Realplayer won't work in Opera"
date: 2006-12-27
forum: Desktop Environments
---

### Post by itsjustarumour on 2006-12-27
Has anyone managed to get the RealPlayer plugin working in Opera?  

When I click on a link to a clip (eg on the BBC website), the Realplayer plugin displays OK but doesn't start automatically - and when I hit the "Play" button the box just greys out and then Opera crashes.

Anyone have any ideas what might be causing this? I've managed to get Realplayer working OK in Firefox 2.0 but for completely subjective personal reasons I prefer using Opera, and I don't want to switch to the OSS plugins/players as I need to be able to fast-forward and fast-backward reliably through very long clips and only Realplayer (I think) can do this...

(Edgy 6.10 32bit, Gnome 2.16.1 btw)

---

### Post by itsjustarumour on 2007-01-01
Anybody?  :confused:

---

### Post by obsidion on 2007-01-01
Ok installed Opera just to check it out. I checked the realplayer radio stream at 
[http://www.bbc.co.uk/bbc7](http://www.bbc.co.uk/bbc7) and it worked fine for me. A little more info as to how you installed realpayer and opera would help us to help you. Ie did you get them both from the commercial repos or did you install it from theie respective websites for instance. One thing to make sure is that it points to the right place for the plugins, mine points to /usr/lib/mozilla/plugins for instance.

---

### Post by itsjustarumour on 2007-01-01
Obsidion - thanks v much for the reply.  Both Opera and Realplayer were installed from the Ubuntu "dirty" repositories.  Thanks for the tip on the plugins, I'll check that they point to the right places when I get chance (can't check now though unfortunately as can't boot to my desktop, but thats another issue which I've just put up a post for!) I'll let you know I get on - cheers again, and happy new year!

:)

---

### Post by ffi on 2007-01-01
> **itsjustarumour said:**
> Has anyone managed to get the RealPlayer plugin working in Opera?  

When I click on a link to a clip (eg on the BBC website), the Realplayer plugin displays OK but doesn't start automatically - and when I hit the "Play" button the box just greys out and then Opera crashes.

Anyone have any ideas what might be causing this? I've managed to get Realplayer working OK in Firefox 2.0 but for completely subjective personal reasons I prefer using Opera, and I don't want to switch to the OSS plugins/players as I need to be able to fast-forward and fast-backward reliably through very long clips and only Realplayer (I think) can do this...

(Edgy 6.10 32bit, Gnome 2.16.1 btw)

Works for me, edgy/opera 9.10. If the plugin doesnt work why don't you use the standalone player?

Try renaming you ~/.opera dir to see if some setting is messing things up.

---

### Post by itsjustarumour on 2007-01-01
FFI - thanks for you comment, but I've just inadvertently found a solution to the problem! (and thanks again Obsidion)

Whilst trying to fix an unrelated problem I was using Synaptic Package Manager to install some KDE components, and it seems that installing "kde-core" fixes the Opera/Realplayer issue. I have no idea what kde-core includes that my default Gnome install didn't, but I've uninstalled/reinstalled three times to test it and it works every time!  

Anyway, thanks again for your input, kind sirs!  :)

---

