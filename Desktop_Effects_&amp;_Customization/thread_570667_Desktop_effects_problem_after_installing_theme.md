---
title: "Desktop effects problem after installing theme"
date: 2007-10-08
forum: Desktop Effects &amp; Customization
---

### Post by Cobbs on 2007-10-08
Okay, I had been using one of the themes that came pre-loaded with Ubuntu and I had enabled the desktop effects on my laptop.  I decided to change the theme to one I downloaded from gnome-look.  Once I installed the theme I was unable to do a number of things.  

1) I noticed that I was unable to reset the colors of the firefox input fields back to the default as was directed by the theme.  For some reason I can't find the firefox file to load the .css into (I've only been using Linux for a short time).

2) I was unable to use my desktop effects after loading the theme.  I managed to get the wobbly windows to work, but not the cube.  When I switch to the next workspace, it flips like a piece of paper instead of a cube.  
    I am wondering if there is a way to restore the DE back to the defaults, since it seems like the theme added a different effect?

Here is the theme that I installed: [http://www.gnome-look.org/content/show.php?content=65533&forumpage=0](http://www.gnome-look.org/content/show.php?content=65533&forumpage=0)

Any help or suggestions would be great, I'm pretty stumped on how to fix it.

Thanks

---

### Post by Cobbs on 2007-10-08
okay, I managed to get firefox back to defaults... I have no idea how I did it though.  But I still can't get the cube to work, so any ideas with that?

---

### Post by skotadi on 2007-10-08
I'm not sure why that happened, but try this:

get the compizConfig program (I'm not at my Ubuntu computer, so I'm not sure exactly what it's called....Use Synaptic Package Manager and search for compiz.  the actual package you want is compiz-settings-manager or something like that)

So install that, then go to it (system -> preferences -> CompizConfig)

click on the button under "general settings".
There should be a bunch of tabs at the top.  I'm sorry I can't remember which one it is, but flip through them until you find the slidebar that is labeled something like "horizontal number of viewports" or "horizontal number of virtual desktops".  crank that to 4.  

Hope that helps

---

### Post by Cobbs on 2007-10-08
Thanks skotadi! That fixed my problem!  :)

---

