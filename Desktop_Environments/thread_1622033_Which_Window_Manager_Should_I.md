---
title: "Which Window Manager Should I"
date: 2010-11-15
forum: Desktop Environments
---

### Post by h41cyon on 2010-11-15
I've got a VPS with not a whole lot of RAM (~512MB) and I primarily want to use it to run a Windows application via Wine.

I'm going to be connecting to it using FreeNX and I was wondering what is the most efficient way of keeping this Wine app running in the background but also be able to connect to it using nomachineNX.

I've used something like XFCE to contain the Wine application and i'll just connect to the XFCE instance via nomachine.  That's alright, but XFCE seems a bit overkill for just wanting to have a single application running.

What I'd really like is something kind of like the "screen" command, but that would work with a graphical window.  Can I use screen for this?  I've never set anything up like this.

(for clarification, the windows app I want to continually run is Metatrader 4)

---

### Post by Urhungry on 2010-11-15
I don't think that I'm all that qualified to answer your question, but what I would do would be to just install a lightweight window manager such as icewm, jwm or openbox. You could also use tinywm if you don't need any window buttons or way of launching programs, but I'm not all that sure how to set a tintwm install up so that it's actually usefull.

---

