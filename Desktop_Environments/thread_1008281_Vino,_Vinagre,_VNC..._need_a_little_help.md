---
title: "Vino, Vinagre, VNC... need a little help"
date: 2008-12-11
forum: Desktop Environments
---

### Post by rogerdean on 2008-12-11
Hello all

I've abandoned my poor mother with a new Hardy install and disappeared to the other side of the world. I'd really like to support her remotely without huge phone bills, so hope VNC might be the way

I've not found a good howto for this, so here's what we've got - I'm on Intrepid, she's on Hardy. She connects to broadband in the UK via a wireless router, I have a rubbish satellite link in Afghanistan. Don't think either of us has a static IP at the moment, if that matters

I don't know the difference between Vino, Vinagre or the host of other options that seem to be available. Seems Ubuntu has renamed these things anyway, right? And I understand they are not suited to slow connections.

Folks, what should we do, and how should be do it? Any help appreciated!

Cheers
Roger

---

### Post by SalsaDoom on 2008-12-11
Hi Roger,

My experience is that Vinagre isn't there yet, its just missing too many features for prime time. VNC isn't great over slow links, but it is usable if you don't mind the display looking a bit ugly.

I recommend you get rid of Vinagre, and use xvnc4viewer. It integrates with the existing tsclient ("Terminal Server Client"). 

```
sudo apt-get install xvnc4viewer
```

That should install that for ya. Its performance is significantly higher then vinagre's, which doesn't support scaling down the colour depth.

Vino, on the other hand, works like a charm. Just make sure you open a port forward -- and make sure you enter a good password. Vino can change the listening port too, I'd change that to lower the amount of port scanning thats gonna hit it (System->Preferences->Remote Desktop->Advanced).

I support my mom in this way too ;) Works well!

An alternative with better security is to install an openssh-server on her computer, and using ssh's port forwarding so all this vnc stuff goes through a crypto tunnel. Ubuntu's default openssh lets you do this. On your computer, you'd run the command:

```
ssh moms.outside.ip -L localhost:5900:moms.inside.ip:5900
```

I'm assuming she has a router of some kind setup, so make sure her lan address is in the second one. Then you tell your vnc client to connect to your computer ("localhost:5900"). If you are running a vnc server on your computer you might need to change the local port you connect to so the ports don't conflict.

Cheers,
--SD

---

### Post by ugm6hr on 2008-12-11
Consider using Gitso: [http://code.google.com/p/gitso/](http://code.google.com/p/gitso/)

That way, things are easy for your mum - she just has to type in your IP (which means she will have to call / IM you to find out what that is at the time).  I think this might help: [http://whatsmyip.org/](http://whatsmyip.org/)

Not sure how your satellite internet will work, but if there is no router, you just have to open port 5500 (gufw [http://gufw.tuxfamily.org/index.html](http://gufw.tuxfamily.org/index.html) will make that very easy, and readily reversible) and allow her to connect to you.

---

### Post by rogerdean on 2008-12-12
Folks, thanks very much indeed for both those posts. That's two solid starting points for me - if I run into any problems I'll certainly come back to you!

Cheers
Roger

---

