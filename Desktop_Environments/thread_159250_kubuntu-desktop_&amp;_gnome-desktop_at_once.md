---
title: "kubuntu-desktop &amp; gnome-desktop at once??"
date: 2006-04-12
forum: Desktop Environments
---

### Post by stairwayoflight on 2006-04-12
hi everybody,

my name is Tim, and i'm a windows-aholic. its been at least a week since i have used windowz, and i completely removed my xp partition. this has all been possible since i recognized my higher power!

MY QUESTION: i like ubuntu/gnome, but i have used kde before and like that too.

is it possible to install the kde-desktop without changing any functionality for my gnome sessions? i like everything, except sound juicer doesn't always grab the track names i know i've got from freedb or somewhere before.. also rhythmbox isn't as fullfeatured as i would like.

but i like everything so much, i don't want to break it. if i could try the "kde-desktop" as an add-on, and then be sure I could remove everything later if i needed, i would like that very much.

i think i would like to experiment with both desktops, pim apps & multimedia, without screwing my current install.

is this possible?

---

### Post by aysiu on 2006-04-12
It won't change Gnome's functionality, but you'll see a lot more applications in your application menu.

---

### Post by Ramses de Norre on 2006-04-12
I'd try kubuntu-desktop.```
sudo apt-get install kubuntu-desktop
```
You can then choose which one you want to load from the session menu in the login screen.

---

### Post by aysiu on 2006-04-12
It's probably best to do this: ```
sudo aptitude update
sudo aptitude install kubuntu-desktop
``` Aptitude will remember what came with *kubuntu-desktop*, so it'll be easier to uninstall later, should you wish to do so.

---

### Post by stairwayoflight on 2006-04-12
Thanks for the tips...

...I could try it but (memory foggy) I thought either with breezy or dapper (I tried out DDF5 as well) installing "kubuntu-desktop" messed with totem or totem-xine or something like that.

For sure it won't screw my multimedia?

Thnx

---

### Post by stairwayoflight on 2006-04-12
***_EDIT: OH CRAP I DON'T KNOW HOW TO DELETE THIS, SORRY TO REPOST MY BROWSER DIDN'T REFRESH PROPERLY SO I POSTED THE SAME QUESTION._***hi,

I'd do it except I seem to remember installing "kubuntu-desktop" screwing up multimedia functionality, like maybe changing the totem backend and crap like that. Or maybe I just didn't understand the problem. It could've been when using dapper, I'm back on Breezy now though.

Will it for sure not screw with anything, just install new apps?

---

### Post by Sef on 2006-04-13
> Will it for sure not screw with anything, just install new apps?

I had no problems when I did it.  Dapper is alpha, so there is something there that will get fixed before it goes gold.   Breezy is stable, so should be no problem at all.

---

