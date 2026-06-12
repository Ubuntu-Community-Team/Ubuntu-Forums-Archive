---
title: "Best fonts setup..."
date: 2007-04-21
forum: Desktop Effects &amp; Customization
---

### Post by GoalieCa on 2007-04-21
I found some time today to install feisty. I decided to do a clean install of my system. Including junking all of the .hidden files in my home directory except of course the obvious .vimrc, etc. that i just couldn't live without. The only thing i forgot to deal with was my fonts!

The problem I've run into though is the font setup in feisty blows. It feels like i've got blurry vision, fonts too small, lcd sub-pixel makes gnome terminal go all rainbow, etc. 

I'm having a hell of a time trying to figure out what it was i did back in the dapper-beta days which is when i last did a clean install. 

Font de-uglification is a really common issue so here's my proposal... 

**Share your setup!**

Let us know what fonts, font size, etc. you use for gnome, kde, firefox, gnome-terminal, or any other application.

---

### Post by Gannin on 2007-04-21
Have you tried typing "sudo dpkg-reconfigure fontconfig-config" in a terminal and choosing Autohinter?

---

### Post by reclusivemonkey on 2007-04-21
Mine isn't as nice as I would like, but I have;

Smoothing: Subpixel (LCDs)
Hinting: Slight
Subpixel Order: RGB

And I have my resolution set to 89 dots per inch as reported by

```

monkey@mother:~$ xdpyinfo | grep resolution
  resolution:    89x87 dots per inch

```

---

### Post by GoalieCa on 2007-04-21
What font family's though. Are you using bistream vera, just plain sans/serif/mono, dejavu, etc...

thanks for the dpi tip :D

---

### Post by reclusivemonkey on 2007-04-21
Lucida Grande for everything except the console; I'm using Lucida Console for that.

---

### Post by reclusivemonkey on 2007-04-21
I'm presuming you have a LCD monitor? If so, you should check this out;

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_improve_sub-pixel_font_rendering_for_Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_improve_sub-pixel_font_rendering_for_Feisty)

I just did this and my fonts are beautiful now! I was going to do a before and after, but I forgot the before :-S

Trust me though, there is a heck of a noticeable difference...

---

### Post by GoalieCa on 2007-04-21
Yeh. that made a huge difference. Still not too happy about the font family i'm using but at least i'm not going blind. No more foggy vision :D

---

### Post by zgornel on 2007-04-23
> **reclusivemonkey said:**
> I'm presuming you have a LCD monitor? If so, you should check this out;

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_improve_sub-pixel_font_rendering_for_Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_improve_sub-pixel_font_rendering_for_Feisty)

I just did this and my fonts are beautiful now! I was going to do a before and after, but I forgot the before :-S

Trust me though, there is a heck of a noticeable difference...

I can definetly see a huge improvement in KDE with this tweak ;) . The resolution got bumped from 83x86 to 86x88. Cheers!

---

### Post by NoTiG on 2007-04-23
> **reclusivemonkey said:**
> I'm presuming you have a LCD monitor? If so, you should check this out;

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_improve_sub-pixel_font_rendering_for_Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_improve_sub-pixel_font_rendering_for_Feisty)

I just did this and my fonts are beautiful now! I was going to do a before and after, but I forgot the before :-S

Trust me though, there is a heck of a noticeable difference...

omg. I'm in heaven . TY

---

