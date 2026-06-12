---
title: "Thumbs Plus, Xara3D Linux replacements or Wine compatibility"
date: 2006-07-13
forum: Desktop Environments
---

### Post by jayson7 on 2006-07-13
Hello I am a web developer and am needing linux replacements for the following programs:

Xara3d6 (Easily create 3d text)
[http://www.xara.com/xara3d/](http://www.xara.com/xara3d/)

ThumbsPlus (thumbnailer, but needs to have web page generator)
[http://www.cerious.com/](http://www.cerious.com/)

I've tried running all these in Wine but unfortunately am having no luck.

Thumbsplus 7.0 gives me a 5015/8008 "unable to allocate memory" error even after I install all the database components.

Xara3D6 is is also giving me errors.

If anyone knows how to get these working in Wine or has good native Linux replacements, please let me know.  I can live without Xara3d and just use Gimp, but the thumbnailer is vital to me as I need to be able to easily generate web pages from images.  I've tried using BreezeBrowser Pro in Wine as well but likewise it will not work. :(

Thanks for any help you can give.

---

### Post by orb9220 on 2006-07-13
Well I use gThumb and looking into Gwenview to both are kinda like acdsee,Thumbplus clones.

gThumbs has more built in tools but gwenview has a plugin menu with no plugins installed yet. Haven't looked to see what plugs are avaiable.

Both installed from synaptic package manger just run and search on image and install anything that may fit the bill.

also check out Gimp,Cinepaint for doing 3d char stuff.

For actual 3d rendering and animation. Blender is the way to go tho the interface is complex and a steep learning curve for begineer's.

Hope I have been some help.

---

### Post by jayson7 on 2006-07-13
> **orb9220 said:**
> Well I use gThumb and looking into Gwenview to both are kinda like acdsee,Thumbplus clones.

gThumbs has more built in tools but gwenview has a plugin menu with no plugins installed yet. Haven't looked to see what plugs are avaiable.

Both installed from synaptic package manger just run and search on image and install anything that may fit the bill.

also check out Gimp,Cinepaint for doing 3d char stuff.

For actual 3d rendering and animation. Blender is the way to go tho the interface is complex and a steep learning curve for begineer's.

Hope I have been some help.

orb9220,

Yes, thank you.  You have been a very BIG help.  The "web album" feature of gThumbs should work well for me.  The only thing is it does not automatically handle movies, but I'll figure something out.  Now I can reasonably do my work in Linux and can let my Windows partition collect virtual dust.  Thanks again. :)

---

### Post by PriceChild on 2006-07-13
Have you checked the winehq applications database about those programs? You never know, there may be a quick fix in there from someone.

---

### Post by jayson7 on 2006-07-13
> **PriceChild said:**
> Have you checked the winehq applications database about those programs? You never know, there may be a quick fix in there from someone.

Yes. Thanks. I was trying to get Xara3d v. 6 working and no such luck.  But someone did mention version 5 worked.  So I got that and sure enough success!  Xara3d 5 works perfectly on my system.

For anyone who reads this in search and needs Xara3d, if I set it to win98 things worked but the text was never spacing itself correctly and was writing over other text.  Changing to "windows 2000" using winecfg did the trick.  Everything seems to work great.  I will register there and write a note about it.  Xara3d 5.0 appears to be a platinum program in wine, While Xara 6.0 seems to be in garbage state (for me anyway).

Unfortunately Blender isn't working.  I'm not able to get GLX support working right with my old S3 card.  Oh well, Will save that for later since with Xara3d5 operational I do not need Blender. I'm just happy to have gotten both Xara3d and a great Thumbsplus replacement.  These forums rock! :)

---

