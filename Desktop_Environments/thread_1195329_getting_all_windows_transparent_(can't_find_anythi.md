---
title: "getting all windows transparent (can't find anything that is mentioned in guides)"
date: 2009-06-23
forum: Desktop Environments
---

### Post by v1nsai on 2009-06-23
I've been lookin around for ways to make all of my windows transparent, just a little bit to give a sort of glassy look I think it would rock, I found _[this](http://sudosys.be/?q=fully_transparent_ubuntu)_ guide in which the author explains how to do this, but in compizconfig-settings-manager, my General Options Window does not have opacity settings (crappy screenshot included, gimp doesn't cooperate with me)

I've found a few different guides on how to do this now, I'm familiar with Google and how to use it I promise, but nothing I have found works for me, for reasons like this.  I appreciate any help!

<edit>
Disregard, found a more recent explanation, looksl ike some things got changed around recently.

---

### Post by kelvin spratt on 2009-06-23
You are looking in the wrong place opacity brightness and saturation is what you need to be looking at and for a glassy look you need reflection you can get the refletion images from [http://www.gnome-look.org/](http://www.gnome-look.org/) 
This is what I use for transparent menus etc in  opacity brightness and saturation, click edit  and copy paste this set at 80                                                              name=gnome-panel | type=Menu | tooltip |  PopupMenu | DropdownMenu  
if you want everything transparent leave blank

---

### Post by FormatSeize on 2009-06-23
> **kelvin spratt said:**
> You are looking in the wrong place opacity brightness and saturation is what you need to be looking at and for a glassy look you need reflection you can get the refletion images from [http://www.gnome-look.org/](http://www.gnome-look.org/) 
This is what I use for transparent menus etc in  opacity brightness and saturation, click edit  and copy paste this set at 80                                                              name=gnome-panel | type=Menu | tooltip |  PopupMenu | DropdownMenu  
if you want everything transparent leave blank

Hi,

I'm trying to follow the instructions you gave, but I am having trouble installing the .tar.gz I downloaded. The instructions on the website didn't work for me.

Also, where do I find the opacity brightness and saturation?

---

### Post by raymondh on 2009-06-23
Hello,

The guide I used for transparency

[http://forlong.blogage.de/entries/2007/8/29/How-to-set-up-Compiz-Fusion](http://forlong.blogage.de/entries/2007/8/29/How-to-set-up-Compiz-Fusion)

---

