---
title: "Web Browser on the leightest weight gui.."
date: 2008-03-11
forum: Desktop Environments
---

### Post by #Reistlehr- on 2008-03-11
What's the closest you can get to running Mozilla as a DE?

I'm createing a lightweight Desktop Application Environment that's web based. I would prefer if i didnt have to use GDM, or KDE, XFCE, Flux, etc. I want to be as barebone to a gui as possible just to launch a web browser to handle it. Think of it as a Web Based Desktop..

---

### Post by x1a4 on 2008-03-11
How about [LessTif]("http://www.lesstif.org/")?  Or, if LessTif is still too big, [Ratpoison]("http://www.nongnu.org/ratpoison/").

EDIT: Two others you might also be interested in are [Matchbox]("http://matchbox-project.org/") (great for hand-helds and kiosks) and  [Oroborus]("http://www.oroborus.org/") which at 75K is probably the smallest window manager you'll likely to find.

They are all in the repositories.

---

### Post by bharadwaj on 2008-03-12
how about sticking to terminal only??? very less GUI infact no GUI and extremely high speed in launching or ending the programm and very less space to occupy.

---

### Post by kerry_s on 2008-03-12
i did a base for a friends kiosk project loads straight to iceweasel.
be back, i might still have it on google doc.

your in luck, attached
ps: that's meant to give you ideas, you don't have to use it.

---

### Post by #Reistlehr- on 2008-03-14
You guys are awesome. So many choices haha. 

I'm thinking about the authentication part now. I dont know if i should use something simple like SLiM, or if i should just have an auto login with a regular user, and have the script take over and authenticate in the web based app itself. 

If i use slim, is there anyway to link SLiM, or perhaps GDM for educational purposes to MySQL instead of PAM? I need to check into PHP to see if there's a way to authenticate PHP to PAM.. hmm.. 

Thanks again guys!

---

### Post by kerry_s on 2008-03-14
> **#Reistlehr- said:**
> You guys are awesome. So many choices haha. 

I'm thinking about the authentication part now. I dont know if i should use something simple like SLiM, or if i should just have an auto login with a regular user, and have the script take over and authenticate in the web based app itself. 

If i use slim, is there anyway to link SLiM, or perhaps GDM for educational purposes to MySQL instead of PAM? I need to check into PHP to see if there's a way to authenticate PHP to PAM.. hmm.. 

Thanks again guys!

if your using debian the auto login part is in the doc->
```
1:2345:respawn:/sbin/rungetty tty1 --autologin user
```
with a script in ~/.bashrc for security, but if you don't need security, put this in ~/.bash_profile instead and it will start X on auto log in.
```
if [ "tty1" ]; then
startx
fi

```

in ubuntu /etc/inittab would be  /etc/event.d/tty1

no need for a resource draining login manager.

---

