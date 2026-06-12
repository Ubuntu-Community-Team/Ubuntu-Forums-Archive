---
title: "[SOLVED] Multiple Wallpapers in Compiz-Fusion"
date: 2007-06-23
forum: Desktop Effects &amp; Customization
---

### Post by Megaqwerty on 2007-06-23
Is there a way to completely remove (or at least make transparent) the gnome wallpaper? (I have a different background for each workspace set up using compiz-fusion, but it's being covered by the gnome wallpaper (setting it to no wallpaper just makes the Desktop colors show up, and setting a transparent png for the background produces the same results))

Thanks,
Megaqwerty

---

### Post by Happy_Man on 2007-06-23
You could instruct Nautilus (which, in addition to being a file manager, also draws the desktop) to stop drawing the desktop. This would also get rid of any and all desktop icons you may have. Just a suggestion.....

---

### Post by Megaqwerty on 2007-06-23
That works, but I'd rather not get rid of my icons. If you know of a way to tell nautilus not to draw the background however...

---

### Post by ivesjd on 2007-06-23
I was trying to do the same thing last week, the only thing I could find was getting rid of icons and background.

---

### Post by Megaqwerty on 2007-06-24
Argh, oh well, I can only hope someone here has a more favorable solution. Or, if not, it's not like it's a critical system component. ;-)

---

### Post by steveneddy on 2007-06-24
has anyone looked at wallpapoz lately?

---

### Post by Megaqwerty on 2007-06-24
> **steveneddy said:**
> has anyone looked at wallpapoz lately?
I'm not sure I understand the point of your comment...

---

### Post by steveneddy on 2007-06-24
> 
has anyone looked at wallpapoz lately?

No one searches Google anymore?

> **Megaqwerty said:**
> I'm not sure I understand the point of your comment...

[wallpapoz]("http://wallpapoz.akbarhome.com/") is a program for Gnome that puts a different wallpaper on each desktop.

It is supposed to be Compiz/Beryl aware if you set Compiz/Beryl up correctly.

---

### Post by pt123 on 2007-06-24
> **Megaqwerty said:**
> Is there a way to completely remove (or at least make transparent) the gnome wallpaper? (I have a different background for each workspace set up using compiz-fusion, 
Thanks,
Megaqwerty


Does compiz fusion expose its wallpaper settings to gconf tool or something similar, because  I run a script which changes my wallpaper every hour, ?

[PHP]gconftool-2 -t str --set /desktop/gnome/background/picture_filename "$wpPath"[/PHP]

---

### Post by Megaqwerty on 2007-06-24
Ah, my mistake. I assumed that that was a misspelling of "wallpapers." I did in fact search google, but was looking for ways to remove the gnome wallpaper, not ways to have multiple wallpapers on different workspaces. (After all, Compiz provided me with that right?  ;-) )

---

### Post by Megaqwerty on 2007-06-24
> **pt123 said:**
> Does compiz fusion expose its wallpaper settings to gconf tool or something similar, because  I run a script which changes my wallpaper every hour, ?

[PHP]gconftool-2 -t str --set /desktop/gnome/background/picture_filename "$wpPath"[/PHP]

I'm not sure, but it does have an optional Gconf configuration backend if that says anything.

---

### Post by pt123 on 2007-06-24
> **Megaqwerty said:**
> I'm not sure, but it does have an optional Gconf configuration backend if that says anything.

Cool found it gconf. Time to muck around.
But when I add the images through CF Config Editor they are not appearing in the gconf background 

/apps/compiz/plugins/cube/screen0/options/backgrounds

They also are not showing up as wallpapers on the sides of the cube

---

### Post by steveneddy on 2007-06-24
> **Megaqwerty said:**
> Ah, my mistake. I assumed that that was a misspelling of "wallpapers." I did in fact search google, but was looking for ways to remove the gnome wallpaper, not ways to have multiple wallpapers on different workspaces. (After all, Compiz provided me with that right?  ;-) )

I am sorry. I misunderstood your question.

---

### Post by Megaqwerty on 2007-06-24
No, you understood it correctly. I do want a way to have multiple wallpapers on different workspaces. Those just weren't the terms I searched for in Google.

---

### Post by metalhead8816 on 2007-12-26
Did anyone figure out how to do this??

Having a different background on each side of the cube with icons still in place?

---

### Post by Megaqwerty on 2007-12-27
Yes, using wallpapoz. A .deb of wallpapoz is avalible at [http://getdeb.net](http://getdeb.net)

Hope that helps,

Megaqwerty

---

### Post by tiachopvutru on 2007-12-27
> **Megaqwerty said:**
> Yes, using wallpapoz. A .deb of wallpapoz is avalible at [http://getdeb.net](http://getdeb.net)

Hope that helps,

Megaqwerty

You may want to add www. before getdeb so it would be [http://www.getdeb.net](http://www.getdeb.net) (or at least, it only works for me when I do that)

---

### Post by lewisskinner on 2007-12-28
wallpapoz is rubbish.  Yes, it'll change wallpaper for you, but it only physically changes them when you rotate to it - so if you rotate the cube using the mouse you still see the same image on all four sides, and using ctrl + alt + <= / => means that you see the wallpaper of the view you were just in, and then when it's finished bouncing, then it changes the background.

What I have is a 1600 x 1200 desktop, on 4 sides of a cube using compiz-fusion.  I have also made a panorama of my city using 4 1600 x 1200 images taken from a park on high ground (ie a 6400 x 1200 image) which I would dearly love to see wrapped around all four faces of my cube when I use mouse-rotate.  does anyone know how to do this?

As I've said, I have compiz-fusion and have tried wallpapoz.  I use Ubuntu 7.10 Gutsy in GNOME, though I have KDE installed as well for some applications which I prefer (I want a GNOME solution if possible though).  My PC spec is in my sig.

---

### Post by dapaintballer331 on 2007-12-29
I really want to know if there is a way to do this as well. For now, I installed wallpaper-tray to just cycle wallpapers every minute. Not useful for quick desktop identification but its pretty cool.

---

### Post by jryprt on 2007-12-29
If you do not use Desktop icons [This](http://n00buntu.blogspot.com/2007/11/step-3-finishing-touches.html)
will work.

---

### Post by lewisskinner on 2008-02-20
> **Megaqwerty said:**
> Yes, using wallpapoz. A .deb of wallpapoz is avalible at [http://getdeb.net](http://getdeb.net)

Hope that helps,

Megaqwerty

No, that only changes the wallpaper after the cube snaps to the screen.  I want the different wallpapers to appear whilst the cube is rotating, so I can easily tell between the different desktops (I use each desktop for different things)

---

### Post by Savel on 2008-02-20
> **Megaqwerty said:**
> Is there a way to completely remove (or at least make transparent) the gnome wallpaper? (I have a different background for each workspace set up using compiz-fusion, but it's being covered by the gnome wallpaper (setting it to no wallpaper just makes the Desktop colors show up, and setting a transparent png for the background produces the same results))

Thanks,
Megaqwerty

Check this:
[http://forum.compiz-fusion.org/showthread.php?t=6199](http://forum.compiz-fusion.org/showthread.php?t=6199)

---

