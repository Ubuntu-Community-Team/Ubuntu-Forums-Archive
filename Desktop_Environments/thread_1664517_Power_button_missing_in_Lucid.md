---
title: "Power button missing in Lucid"
date: 2011-01-11
forum: Desktop Environments
---

### Post by iammisc on 2011-01-11
Hello,

I've installed lucid on two computers now and have been using it for a few months. Overall, it's pretty good and everything just works. However, every now and then (seemingly random), the power button in the indicator applet session panel widget randomly disappears, so I'm unable to shut down my computer without re-adding the widget, or using the command line to shutdown the computer. Now this is acceptable for me, an advanced linux user. However, this is not acceptable for my parents and family, who also use ubuntu computers. Today, my mother called me to ask why she couldn't turn off her computer. I was dumbfounded, and had to walk her through turning it off "by hand."

Now this is not me accidentally removing the indicator applet session panel item. No, I can still see the user name bubble with availability information and I can still switch users. It's just that the power button is completely missing (sometimes the place where it used to be is occupied by a corrupt graphic). Additionally, if I login later, the power button magically returns without me having to do anything with regards to the panel. This is disappointing indeed.

Honestly, this is why ubuntu and linux in general still have the reputation they do of being non-user-friendly. At least in windows or mac, when I get fed-up I can turn it off. But not so in ubuntu. No ubuntu tortures me continuously and I marvel that such a simple thing has escaped the minds of such advanced programmers. I wish Canonical would focus on letting us TURN OFF the computer instead of adding crazy features that I'm not going to use. I mean how can a **real** operating system fail at such a *simple* task?

Regards,
Travis.

---

### Post by tech-hero on 2011-01-11
I also encountered those stuffs. it's just a simple bug. you could still shutdown using the terminal though. 
 
you can fix your applets. you may add or remove anything you don't like.

---

### Post by judedawson on 2011-01-11
Hi iammisc,

Try the below commands in terminal to reset the panels:

Type 'killall gnome-panel' 
or
Type 'gconftool --recursive-unset /apps/panel && killall gnome-panel'

This should bring back the missing icon.

Thanks.

From,
Jude

---

### Post by Zero2Nine on 2011-01-14
Yes you can shut down using the terminal but it's very annoying as it happens on seemingly random moments like mentioned in the OP. It happened sometimes here too and I tried to reproduce it so I know what the cause it but no success. All the solutions I've read are workarounds or maybe I haven't searched enough :P

---

### Post by philnice on 2011-01-15
Jude, thanks! +1 :)

---

