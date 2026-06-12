---
title: "GRUB 0.97 and splash screens"
date: 2006-08-06
forum: Desktop Environments
---

### Post by teasum on 2006-08-06
I've searched and searched for information regarding this minor issue, but I've come up with nothing so far.  First, let me say that I can edit GRUB, and I know how to install splash screens.  However, I want to install a splashimage for GRUB that matches the dimensions of the GRUB menu.  If you search on gnome-look.org, you'll find several GRUB splash screens that match the dimensions of GRUB 0.95 (with a relatively short menu box).  For example: [http://www.gnome-look.org/content/show.php?content=36907](http://www.gnome-look.org/content/show.php?content=36907). 
GRUB 0.97 seems to have different dimensions, and therefore does not match any of these splash screens (actually, I don't know if this is particular to my installation, or if this is a change in GRUB 0.97).  In any case, the screenshots of these splashimages I've found online all show that GRUB 0.95 is running (in other words, I've never seen a screenshot of 0.97 that matches these splashimages).

1) Is there a way to adjust the dimensions of the menu displayed by GRUB,
2) Are there any splashimages out there that match the GRUB menu as displayed in Dapper?

I know this is nit-picking, and not a high-priority issue.  I'm just trying to get my eye-candy just where I want it.  Thanks.

---

### Post by louis_nichols on 2006-08-06
I dunno about changing grub, but a nice guy over here (I don't remember who exactly) was king enough to give me a splash that exactly matches the size of 0.97. I'm attaching it here.

You can use it as a model.

---

### Post by teasum on 2006-08-06
Thanks!  That's exactly what I needed.  I used your file as a template, as you suggested, and created a rather boring splash image (see attachment).  It's a start, however, and perhaps I'll make some more to match the GRUB menu in Dapper and post them on gnome-look.org.  

Incidentally, I also found out that the 'colors' command does not work in the Ubuntu version of GRUB.  See the following bug report for GRUB: [http://savannah.gnu.org/bugs/?func=detailitem&item_id=16190](http://savannah.gnu.org/bugs/?func=detailitem&item_id=16190).

Instead, to use colors in Dapper's version of GRUB, you need to change the color using the 'background' and 'foreground' command, which accepts html color codes rather than color names.  

Just FYI, in case anyone out there is searching for this information.

---

### Post by Dunska on 2006-08-06
You may also want to try out gfxboot for a really nice graphical grub screen.
[http://www.ubuntuforums.org/showthread.php?t=208855&highlight=gfxboot]("http://www.ubuntuforums.org/showthread.php?t=208855&highlight=gfxboot")

---

