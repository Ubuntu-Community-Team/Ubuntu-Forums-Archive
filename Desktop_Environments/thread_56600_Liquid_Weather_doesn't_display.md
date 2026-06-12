---
title: "Liquid Weather doesn't display"
date: 2005-08-13
forum: Desktop Environments
---

### Post by DrQuincy on 2005-08-13
Hi

I have downloaded Liquid Weather and when I run it through Karamba it runs as a theme but it is invisible (I can tell its running because if I right-click over it I can the theme menu) - can anyone help?

Thanks.

---

### Post by eMuNiX on 2005-08-13
Which version of Superkaramba do you have installed?  I have 0.37 running and liquid weather works okay.

---

### Post by DrQuincy on 2005-08-13
Only 0.35 :(.  Is it possible to get 0.37 via apt-get?

Many thanks.

---

### Post by hammett111 on 2005-08-13
Had the same problem and am running version 0.36 of superkaramba, but I managed to get it working. All you have to do is refresh your desktop.

Right click on desktop, refresh desktop and it will show. It has to do with the bugger connecting to an online source and looking for updated info on the weather. It hangs  until it has the info, if you refrsh the desktop its forced to draw before it locks up.

Cheers
Heres my desktop, with it running.

---

### Post by f1dave on 2005-08-14
Superkaramba is pretty easy to install without apt-get anyway... You grab the tar file, extract it, run ./configure, make and sudo make install as specified in the INSTALL file, and bam, you've got yourself the latest superkaramba.

---

### Post by DrQuincy on 2005-08-15
Thanks for your replies.  I tried refreshng the desktop and it still does nothing.  I've noticed also that there are some other Karamba themes that don't display properly.  Some display the base PNG but no data.

---

### Post by usnmustanger on 2005-08-16
[QUOTE=DrQuincy]Thanks for your replies.  I tried refreshng the desktop and it still does nothing.  I've noticed also that there are some other Karamba themes that don't display properly.  Some display the base PNG but no data.[/QUOTE]
 Yeah, same problem here.  I've got .35 running, and refreshing the desktop does nothing.  Had the same issue in PCLinuxOS as well.  Strange.  Anyone?  Any logs we can check?

---

### Post by f1dave on 2005-08-16
I'd say you'd be better off grabbing the latest superkaramba in all honesty.

---

### Post by dolny on 2005-10-05
Well. I have the newest Superkaramba, the newest Liquid Weather theme and it doesn't show up. Even when I try to update or refresh. I don't understand why, because all other themes are working. I re-downloaded the theme but that didn't work. Damn :( I'm running KDE 3.4.2 and Breezy. It's not the issue with Breezy though, cause I had the same problem on Hoary :( I cannot see anything.

I'll compile it from sources again and let you know.

Edit: Ok. My Superkaramba WAS outdated. The newest one works like a charm and is great (after compilation). I had to install python 2.3.

---

