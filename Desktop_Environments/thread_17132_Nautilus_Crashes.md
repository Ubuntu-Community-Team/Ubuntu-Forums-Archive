---
title: "Nautilus Crashes"
date: 2005-02-26
forum: Desktop Environments
---

### Post by nero22 on 2005-02-26
Hello everybody,
I broke my Nautilus. I think it was when I tried to save a file as .jpg :roll: in Inkscape. When I ran Nautilus to see if it did, it crashed, and now, every time I run it, it freezes and I have to force quit or it restarts by itself. Basically it's unusable. I did reinstall it with synaptic, but with no success.
Please help.
Milan

---

### Post by jensyt on 2005-02-26
I'm having nautilus problems, too. Been having them for a few days, really. I wasn't going to complain about it, since I hardly have a use for it, but I figured I'd confirm a problem...

Of course, this could just be a problem locally for the two of us...

---

### Post by nero22 on 2005-02-26
Well I can't seem to manage without Nautilus, so I need help, quickly, I can't stand Endeavour.
This should mean something: when I run Nautilus from the "Disks" ( in the "Computer" drop-down menu on the panel) it works, and I can browse everything except the Home folder. It seems like it loads something that crashes it.

---

### Post by martijntje on 2005-02-26
[QUOTE=nero22]Well I can't seem to manage without Nautilus, so I need help, quickly, I can't stand Endeavour.
This should mean something: when I run Nautilus from the "Disks" ( in the "Computer" drop-down menu on the panel) it works, and I can browse everything except the Home folder. It seems like it loads something that crashes it.[/QUOTE]
 Well, if it's something in your home folder, make a new folder, and one by one copy all the files from your home folder to the new one, and keep trying nautilus on the new folder to see which file is causing trouble.

---

### Post by cwaldbieser on 2005-02-27
I had this problem when I first installed Ubuntu, and I logged a bug about it.  The Gnome folks have taken care of it in a later version of Gnome.

Basically, I downloaded some SVG images to play with in Inkscape, and one of them drove Nautilus bonkers.  I just used the terminal program to remove the offending file, and Nautilus worked fine again.

If I recall correctly, it had something to do with Nautilus trying to render the image preview of what the file looked like.

---

### Post by nero22 on 2005-03-01
Yeah, that was it. I deleted all the SVG files I messed with and Nautilus works fine now.
Thanks for the help cwaldbieser.

---

### Post by masterr on 2007-07-25
Sorry for the necro, but I ran into this problem as well. Running Feisty.

An SVG I created with Inkscape crashes Nautalis. The offending SVG is attached. Anyone have a solution besides removing the SVG or disabling previews completely?

---

