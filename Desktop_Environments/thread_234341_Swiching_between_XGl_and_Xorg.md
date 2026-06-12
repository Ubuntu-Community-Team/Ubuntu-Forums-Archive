---
title: "Swiching between XGl and Xorg"
date: 2006-08-11
forum: Desktop Environments
---

### Post by turok on 2006-08-11
Hi, i succesfully installed Xgl and Compiz following this guide: 
[http://doc.gwos.org/index.php/Swich_between_XGl_and_Xorg_through_GDM_%28or_KDM%29](http://doc.gwos.org/index.php/Swich_between_XGl_and_Xorg_through_GDM_%28or_KDM%29)
But i had to repartition my drive so i deleted that installation and did a new one. I followed the same guide but i couldn't get Xlg and compiz to work, xgl starts but i have no title bar and no compiz efects(maybe becouse packages were upgraded and the guide is old). I've followed several guides and still can't get it to work. Can you recomend me a good semi-newbieproof guide? or the one i've been using should make it work and i'm doing something wrong ?
Thanks a lot.

---

### Post by turok on 2006-08-11
Well, this is what i get when i start my xgl session:
Xgl is running but compiz dont, so i type "startcompiz" that is the name of my script to start xgl and the following happens:

cgwd: no process killed
turok@desktop:~$ Couldn't load settings.  Reverting to defaults.
Couldn't load theme.  Reverting to defaults.

and i loose the title bars.
What can i do ?
thanks.

---

### Post by turok on 2006-08-12
Please does anyone knows what can i do ?
Btw: I am using xgl without composite and after a while the system crashes and shows the login screen.
Pleeeeaseeee heelp meeeee :$

---

### Post by nixendra on 2006-08-17
nothing to help you much... just to tell you that you're not alone

i've carrefully followed this guide:
[http://ubuntuforums.org/showthread.php?t=225141](http://ubuntuforums.org/showthread.php?t=225141)

and got the same the problem as you (Xgl running fine but cgwd won't start)

i've done my Xgl update today.

Is cgwd (and cgwd-themes) "broken" in the current repo (from the very guide) ?


someone ?

---

### Post by undershepherd1 on 2006-08-17
I recently had a similar problem, though the guide I followed is here: [http://tazforum.thetazzone.com/viewtopic.php?t=2189](http://tazforum.thetazzone.com/viewtopic.php?t=2189)
What I discovered was that I had to reinstall compiz-gnome. Then, I had to go to sessions menu (System>Preferences>sessions), then click on the "startup programs."
In there, I added the startup script for compiz "/usr/bin/startcompiz" and removed any references to cgwd and compiz --replace, since those are in the start up script.  It might be "/usr/local/compiz-start" for you, I'm not sure. Then, everything worked ok again. 
Don't know if this will help or not.:confused:

---

### Post by nixendra on 2006-08-18
nope no luck, but i think that i've found my problem.

cgwd complains about GLX_EXT_PIXMAP extension - wich i read elsewere - is not implemented in the current nVidia Binary Blob.

one of the solution mentionned is to install libMesa and get this GLX_EXT_PIXMAP from the mesalib (in software) or to wait for the new binary drivers from nVidia...

---

### Post by moma on 2006-08-18
Annoying that the installation of Xgl/Compiz is a miss & hit game. Instead of stabilizing it gets worse.

But give this a try
[http://www.linuxjournal.com/node/1000081](http://www.linuxjournal.com/node/1000081)

It's important you give a full PATH for the Xgl.
/usr/bin/Xgl ....

---

### Post by nixendra on 2006-08-18
> **moma said:**
> Annoying that the installation of Xgl/Compiz is a miss & hit game. Instead of stabilizing it gets worse.

tell me, i got in working in February back then everything was perhap mor harsh but i got it working :)

> **moma said:**
> But give this a try
[http://www.linuxjournal.com/node/1000081](http://www.linuxjournal.com/node/1000081)

It's important you give a full PATH for the Xgl.
/usr/bin/Xgl ....

yep, quite the same result, read: no luck

i'll wait 'til the next nvidia blob update and hope this fix my problem.

thanks for your help anyway

---

