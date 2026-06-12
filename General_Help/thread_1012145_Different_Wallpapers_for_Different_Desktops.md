---
title: "Different Wallpapers for Different Desktops?"
date: 2008-12-15
forum: General Help
---

### Post by Roger Allott on 2008-12-15
Having now been sorted out for PC eye-candy by Forlong in the thread about Compiz, I have a request for customisation that either isn't immediately obvious or isn't available.

I have set up my Compiz with the infamous cube thingy with four desktops. What I would like is to assign a different wallpaper piccy to each of them.

Could someone let me know whether that's possible and, if it is, how I go about setting them up? I've tried what I had assumed would be the obvious way of doing it by simply going to desktop 2 and right-clicking to get the choosing background tab, but that assigns the one I choose to all four desktops.

A related question is whether one can assign an animated image (e.g. animated png or gif) to the desktop. Anyone know whether the animation is preserved when doing that?

---

### Post by aboud on 2008-12-15
all that is possible, 
for different destops : 

[http://ubuntuforums.org/search.php?searchid=53171349](http://ubuntuforums.org/search.php?searchid=53171349)

but the best of all is not between those, it's to disable nautilus drawing your desktop, then assiging different cub faces from the comppiz manager > cube > appearance . but the problem is i don't remmeber the that tiny things that disable nautilus, 

i saw animated wallpaper again i don't remmeber the programms it runs .., so don't give up just keep looking .., post if you find something helping.

---

### Post by Wartender on 2008-12-15
ok to be precise type alt-f2, then gconf-editor, go to apps->nautilus->preferences, and uncheck the show-desktop box
then in ccsm, go to wallpaper and set the images (from top to bottom are the workspaces) for the screensavers, enable and enjoy :)

---

### Post by Roger Allott on 2008-12-15
> **Wartender said:**
> ok to be precise type alt-f2, then gconf-editor, go to apps->nautilus->preferences, and uncheck the show-desktop box
then in ccsm, go to wallpaper and set the images (from top to bottom are the workspaces) for the screensavers, enable and enjoy :)

Spot on! Thanks for that.

Now, can anyone recommend an Ubuntu graphics program that can create and save animated .png files?

---

### Post by Wartender on 2008-12-15
i'm not sure there is such a thing as an animated .png files, ibelieve you only do that with .gif files. and you're welcome!

---

### Post by Roger Allott on 2008-12-16
> **Wartender said:**
> i'm not sure there is such a thing as an animated .png files, ibelieve you only do that with .gif files. and you're welcome!

gif doesn't support partial transparency as png does, and it's limited to 256 colors compared to png's full palette of 16.7 million.

Firefox 3 introduced support for animated png files but there have been very few programs out there that I've found to create them.

But now, after a bit of googling, I've found a very basic one that's an add-on for Firefox, which is a novel approach if nothing else.

[https://addons.mozilla.org/en-US/firefox/addon/5519]("https://addons.mozilla.org/en-US/firefox/addon/5519")

To test it, I found a few jpg pics of some friends of mine on my PC and created a little photo montage of them.

[IMG]http://i476.photobucket.com/albums/rr122/Latrax/animation-test.png[/IMG]

Functionality is very limited, so no frame transitions and, from what I can see, no compression of similar frames, but it's a start I think.

Unfortunately, it won't do what I originally wanted, as if you load a pic that's the size of desktop wallpaper, the image obliterates all the control icons!

---

### Post by Roger Allott on 2008-12-17
I spent most of last night making some animated png files on a Windows prog I found called [GIF Movie Gear]("http://www.gamani.com/") (30 day free trial).

Having four nice ones, I then proceeded to transfer them onto my home directory in Ubuntu and referenced them in CompizConfig for the four desktops of my cube.

Sadly, it seems that the Ubuntu cube cannot render animated png files yet, and from what I an tell, no other part of the desktop can. Indeed, the only programs I've found that do render an animated png are Firefox (v3) and Opera (v9.5+).

Is there anyone here who's developing Ubuntu who can tell me if there are any plans afoot to enable animated png rendering in the desktop?

And I'm still searching for a debian linux app that creates animated png files, if anyone is aware of anything.

---

