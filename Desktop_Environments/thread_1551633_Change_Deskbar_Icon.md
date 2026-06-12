---
title: "Change Deskbar Icon"
date: 2010-08-12
forum: Desktop Environments
---

### Post by ThomasB2k on 2010-08-12
Hi! So what I want to do is change the icon that the deskbar applet shows in the panel. I've read that you can change the icon that is in the text input box ([http://is.gd/eeSha](http://is.gd/eeSha)), but I've had no luck finding any thing to change the actual panel icon.

tl;dr version:
I want to change this icon: [http://is.gd/eeSmR](http://is.gd/eeSmR)

The icons in /usr/share/deskbar-applet/art/ don't manipulate this icon.

Thanks in advance.

---

### Post by cmcanulty on 2010-08-12
I was also hoping to use custom icons for some of my stuff , like certain folders but no luck so far.

---

### Post by ThomasB2k on 2010-08-22
Bump

---

### Post by mcbiff on 2010-09-18
bump - OP is right, the icons in /usr/share/deskbar-applet/art do not correspond to the one on the panel. anyone got any ideas?

---

### Post by Wage on 2010-09-25
Just stick an icon with the name deskbar-applet.png in your icon themes apps size 24 folder. /usr/share/icons/ is where ubuntu icon themes are stored.

---

### Post by cmcanulty on 2010-09-25
I downloaded some icons to that location but still don't see how to  have it appear on panel. I rt clicked the icon on panel and did properties but no icon option, thank you.I do see if I go to properties of a file, there is an emblem option but I can't see how to add a custom one. I looked in usr/share/icons but then there are a bunch of folders and I don't know which one to paste my icons into

---

### Post by C.B.Leslie on 2010-09-25
> **Wage said:**
> Just stick an icon with the name deskbar-applet.png in your icon themes apps size 24 folder. /usr/share/icons/ is where ubuntu icon themes are stored.

Confirming this works. :) Thank you.

---

### Post by cmcanulty on 2010-09-26
Thanks but there are about 20 folders but none named themes apps 24 I did paste them into the icons folder but they still don't show up as a choice.

---

### Post by Wage on 2010-09-27
> **cmcanulty said:**
> Thanks but there are about 20 folders but none named themes apps 24 I did paste them into the icons folder but they still don't show up as a choice.

What theme are you using? If you're using Humanity for example, the icon would go in /usr/share/icons/Humanity/apps/24/

---

### Post by cmcanulty on 2010-09-27
Well that's what I thought but I am using Clearlooks theme and there is no Clearlooks folder.

---

### Post by Wage on 2010-09-27
> **cmcanulty said:**
> Well that's what I thought but I am using Clearlooks theme and there is no Clearlooks folder.

Check in ~/.icons/

---

### Post by cmcanulty on 2010-09-28
Here is a screenshot of the folder but still it doesn't appear as on option. I am trying to use the guitar.pgn icon, thank you

---

### Post by Wage on 2010-09-29
> **cmcanulty said:**
> Here is a screenshot of the folder but still it doesn't appear as on option. I am trying to use the guitar.pgn icon, thank you

If you're trying to change the deskbar icon on your panel it needs to be in the apps folder and called deskbar-applet.png

If you don't have an apps folder you'll need to create one and add it to your index.theme file.

---

### Post by cmcanulty on 2010-09-29
I'm trying to change some folder icons in Documents and folder on the panel

---

