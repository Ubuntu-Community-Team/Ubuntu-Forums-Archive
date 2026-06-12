---
title: "[SOLVED] transparent taskbar"
date: 2007-11-15
forum: Desktop Effects &amp; Customization
---

### Post by ep3w on 2007-11-15
I am running 7.10 gnome and I am wondering if there is any way of making the taskbars transparent.  I searched and I can't seem to find a way of doing it in gnome.  I know you can right click>properties and change it, but that leaves the icons/menus/tasks nontransparent.  Anyway of making the whole thing transparent? I tried looking around in compiz fusion settings and couldn't find anything. thanks!

---

### Post by Wiebelhaus on 2007-11-15
Left Click panel then right click properties:

---

### Post by ep3w on 2007-11-15
In my other post I said i tried that and it still leaves the icons/menus/tasks nontransparent.  Here is a screenshot... 

Any way of fixing that?

---

### Post by GlennW on 2007-11-15
Pardon me, I'm not at my Gutsy box at the moment, but if I remember correctly, and if this is what you're after, right click on the task bar and you'll have the options right there.

---

### Post by ep3w on 2007-11-15
> **GlennW said:**
> Pardon me, I'm not at my Gutsy box at the moment, but if I remember correctly, and if this is what you're after, right click on the task bar and you'll have the options right there.

Read my two previous posts

---

### Post by reacocard on 2007-11-15
> **ep3w said:**
> In my other post I said i tried that and it still leaves the icons/menus/tasks nontransparent.  Here is a screenshot... 
<image snip>

Any way of fixing that?

don't use anything else that changes the appearance of the bars, ie. get rid of whatever it is making your bars black in that picture.

(FYI, it's considered polite to post large images as either attachments or thumbnails instead of inline)

---

### Post by pedrogl on 2007-11-16
if you are using compiz (desktop effects), you can add true transparency.
go to System->Prefs->Advanced desktop effects settings
Click on General opts.->Opacity settings, and add the following entry at top of the list:
Opacity windows: type=dock
Opacity windows values: 80 (adjust this to your like)

if you dont have the advanced desktop settings util, just install it:
sudo apt-get install compizconfig-settings-manager 

this will make entire panel transparent

---

### Post by ep3w on 2007-11-16
> **pedrogl said:**
> if you are using compiz (desktop effects), you can add true transparency.
go to System->Prefs->Advanced desktop effects settings
Click on General opts.->Opacity settings, and add the following entry at top of the list:
Opacity windows: type=dock
Opacity windows values: 80 (adjust this to your like)

if you dont have the advanced desktop settings util, just install it:
sudo apt-get install compizconfig-settings-manager 

this will make entire panel transparent

Exactly what I was looking for, thanks a lot! :)

---

### Post by ep3w on 2007-11-16
> **reacocard said:**
> 
(FYI, it's considered polite to post large images as either attachments or thumbnails instead of inline)

Sorry about that, I realized that after posting and could not figure out how to make it a thumbnail.  Is that something that can be done through the forum, or does it need to be done with the uploader?

---

### Post by rundee_f on 2007-11-16
> **ep3w said:**
> Sorry about that, I realized that after posting and could not figure out how to make it a thumbnail.  Is that something that can be done through the forum, or does it need to be done with the uploader?

u can simply use "Manage Attachments".. or u can reduce the size of ur screenshot before u post it inline.. ;)

---

### Post by ep3w on 2007-11-16
> **rundee_f said:**
> u can simply use "Manage Attachments".. or u can reduce the size of ur screenshot before u post it inline.. ;)

Thanks! I will remember that for next time...

---

### Post by misfitpierce on 2007-11-16
The theme you have is making the bars black. Change look to clearlooks for look and change bar to transparant.

---

### Post by mattchess on 2007-11-16
Is there a way to keep the text and icons bright, and just make the backgrounds transparent, for example for the menu bars?

---

### Post by steveneddy on 2007-11-19
This looks cool with the new [Autumn Leaves]("http://ubuntuforums.org/showthread.php?t=616230&highlight=autumn+leaves") Compiz plugin.

---

### Post by pedrogl on 2007-11-19
i think that for leaving icons bright you must use the settings from gnome panel, the compiz trick works per window, it doesn't distinguish individual widgets like buttons or icons

---

