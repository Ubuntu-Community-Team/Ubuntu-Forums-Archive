---
title: "Launch split Terminator on session start"
date: 2009-05-24
forum: General Help
---

### Post by AllRadioisDead on 2009-05-24
Hi, this may be a bit of a strange request, but hear me out.
I'm using devilspie to run rTorrent on my desktop with no window decorations, and maximum height when I begin my session. However, below rtorrent, I would like to run irssi, in the same Terminator but in a different (tab?). Is there any way I can edit my startup script to start Terminator, but split into rtorrent and irssi. I've attached a screenshot of what I'm trying to achieve when I log in.

---

### Post by AllRadioisDead on 2009-05-24
bump.

---

### Post by AllRadioisDead on 2009-05-24
Bump

---

### Post by whitethorn on 2009-05-24
I'm not quite sure how to get that done.  I have an alternate idea though.  You might want to setup a different profile for gnome-terminal, and use a startup command with devilspie to set it up at underneath the other one.  Should look like what you have in the pic, and this way you'll have irrsi and rtorrent running in their own terminal window.

---

### Post by AllRadioisDead on 2009-05-24
> **whitethorn said:**
> I'm not quite sure how to get that done.  I have an alternate idea though.  You might want to setup a different profile for gnome-terminal, and use a startup command with devilspie to set it up at underneath the other one.  Should look like what you have in the pic, and this way you'll have irrsi and rtorrent running in their own terminal window.
I'm using openbox...so I don't have gnome terminal.
Are there any other terminal apps that allow such startup command?
(Gnome terminal has a lot of dependencies which I'd like to avoid)

---

### Post by AllRadioisDead on 2009-05-24
Bump

---

### Post by whitethorn on 2009-05-30
I think you should be able to use xterm.  Just write a script with 

```

#!/bin/bash
devilspie
xterm -e rtorrent
xterm -e irrsi

```

Then you'll probably also need a devilspie file to get into the right position.  You'll have to use the Application name.

> 
(if (is (application_name) "rtorrent")  
        (begin (undecorate) (geometry "199x567+1165+0")))


You just have to play around with the geometry until you get it the where you want.  Create another file for irssi.

---

