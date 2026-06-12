---
title: "Cairo-Dock Wastebasket"
date: 2009-05-19
forum: General Help
---

### Post by kestrel1 on 2009-05-19
I have installed Cairo-Dock 2 on Ubuntu Jaunty & it works very well. Only one thing I have found so far is that if I enable the OpenGL version the wastebasket disappears. The applet is still on the dock but it is essentially totally transparent. If I gp back to the non opengl version it works fine.
Any ideas?

---

### Post by fabounet on 2009-05-19
what if you select another theme for this applet ?

---

### Post by kestrel1 on 2009-05-19
Doesn't matter what theme I use, the waste stays the same.

---

### Post by kestrel1 on 2009-05-20
I have just looked again & it is not only the wastebasket that is affected. Most of the applets are. I am going to check a few other things on the system & see if I can resolve this.

---

### Post by kestrel1 on 2009-05-20
Just thought I would post a screen shot so that you can see what I mean.

---

### Post by chriskin on 2009-05-20
it happens to me once in a while, i just go to the options of the applet and change its appearance, and it comes back :P

not the theme of the dock though, i change the theme of the applet at "module" tab


edit : saw that you said about the applets theme ..strange..what about  removing it and putting it back? heheh :S i don't know

---

### Post by kestrel1 on 2009-05-20
Thanks for the reply. I have tried changing the icon via the module option, but it stays the same. I have tried removing the theme & even replacing it & it makes no odds.
I am not that fussed, but would prefer to get it sorted if I can. I have just installed the latest version from the repo's (2.0.2), but it stays as is.
If I drop back to the non openGL version the applets are fine.

---

### Post by chriskin on 2009-05-20
> **kestrel1 said:**
> Thanks for the reply. I have tried changing the icon via the module option, but it stays the same. I have tried removing the theme & even replacing it & it makes no odds.
I am not that fussed, but would prefer to get it sorted if I can. I have just installed the latest version from the repo's (2.0.2), but it stays as is.
If I drop back to the non openGL version the applets are fine.

but it is definitely not worth it, the opengl version is way better .
anyway, i don't know what is the problem, all icons work on me, with the problem i mentioned above from time to time, but it always gets fixed.
probably it would be a good idea to search their forums, but they are mostly in french :S

---

### Post by fabounet on 2009-05-20
you can post there in english without any hesitation.
post the result of cairo-dock -l debug, it may help.

---

### Post by kestrel1 on 2009-05-20
> **fabounet said:**
> you can post there in english without any hesitation.
post the result of cairo-dock -l debug, it may help.

This part of the debug report, that may be relevant:
>  g_iActiveIndicatorTexture <- 38
debug   :  (cairo-dock-X-utilities.c:_cairo_dock_xerror_handler:57)  
  Erreur (3, 18, 0) lors d'une requete X sur 69206049
debug   :  (cairo-dock-X-utilities.c:_cairo_dock_xerror_handler:57)  
  Erreur (3, 18, 0) lors d'une requete X sur 69206049
debug   :  (cairo-dock-X-utilities.c:_cairo_dock_xerror_handler:57)  
  Erreur (3, 18, 0) lors d'une requete X sur 69206049
debug   :  (cairo-dock-X-utilities.c:_cairo_dock_xerror_handler:57)  
  Erreur (3, 18, 0) lors d'une requete X sur 69206049
debug   :  (cairo-dock-X-utilities.c:_cairo_dock_xerror_handler:57)  
  Erreur (3, 18, 0) lors d'une requete X sur 69206049
debug   :  (cairo-dock-X-utilities.c:_cairo_dock_xerror_handler:57)  
  Erreur (3, 18, 0) lors d'une requete X sur 69206049
message :  (applet-notifications.c:cd_illusion_free_data:180)  

I will have a look at the forums later.
Thanks

---

### Post by kestrel1 on 2009-05-21
I also have the same problem on my machine at home. I am wondering if it is something to do with the graphics drivers. I am using an NVidia card in both machines & it is running on version 96 drivers, so it is a slightly older card. I will try it on my laptop & see if I can change the graphics card & use a different driver to see if this does anything.

---

### Post by kestrel1 on 2009-05-24
Think I have found the problem with this. It appears to be the older NVidia cards drivers. Both machines use the version 96 drivers, but I have changed the card in one machine to a slightly newer graphics card that uses the version 173 drivers & everything seems to work fine with the openGL version of Cairo-Dock.

---

