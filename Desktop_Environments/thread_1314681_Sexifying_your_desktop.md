---
title: "Sexifying your desktop"
date: 2009-11-04
forum: Desktop Environments
---

### Post by Jguy on 2009-11-04
Hi,

first off, I'm realitivly new to using Ubuntu full time. I've had it on my laptops with good success and usability, so I'm finally making the jump to using it full time. I've always had free copies (or really cheap) copies of Windows, so I've never had to worry....but now that I'm not in school, I'm refusing to buy Windows 7, and I don't want to go back to XP 64-bit.

Anyway, in about 2 hours, I'll be installing Ubuntu 9.04 64-bit on my desktop at home. I was curious to see what kind of tools and/or programs that people use to make their desktop look 'sexy'. From the looks of some tools and programs out there, GNOME is a much better alternative to a lot of things Windows can do (I LOVE the screensavers). I'm looking for a nice interface, login screens, tools, widgets or gadgets (whatever you want to call them), as well as a good object dock. (There was an object dock similar to MacOSX that I saw in the package manager, but it refused to work for me :( )

any suggestions, thoughts?

thanks.

---

### Post by NoaHall on 2009-11-04
First things first. System -> Admin -> Hardware Drivers

Then, look in the package manager for "compiz". Install it.

Then, install "avant-window-navigator"

Make sure compiz is running, then launch avant :).

---

### Post by ptrinder64 on 2009-11-04
[www.gnome-look.org]("http://www.gnome-look.org") is good for that type of stuff. Personally in terms of the app dock I prefer Gnome Do in Docky interface. But it's all down to preference really, there is also Avant and Cairo Dock (but I think Cairo Dock is no longer supported, and from memory wasn't fantastic).

---

### Post by xuCGC002 on 2009-11-04
The title of the thread had mislead me, but I'll help nonetheless- I agree that GNOME-look is an amazing resource, and I also think [http://art.gnome.org]("http://art.gnome.org") is a good place too.

---

### Post by Pasdar on 2009-11-04
> **Jguy said:**
> Hi,

first off, I'm realitivly new to using Ubuntu full time. I've had it on my laptops with good success and usability, so I'm finally making the jump to using it full time. I've always had free copies (or really cheap) copies of Windows, so I've never had to worry....but now that I'm not in school, I'm refusing to buy Windows 7, and I don't want to go back to XP 64-bit.

Anyway, in about 2 hours, I'll be installing Ubuntu 9.04 64-bit on my desktop at home. I was curious to see what kind of tools and/or programs that people use to make their desktop look 'sexy'. From the looks of some tools and programs out there, GNOME is a much better alternative to a lot of things Windows can do (I LOVE the screensavers). I'm looking for a nice interface, login screens, tools, widgets or gadgets (whatever you want to call them), as well as a good object dock. (There was an object dock similar to MacOSX that I saw in the package manager, but it refused to work for me :( )

any suggestions, thoughts?

thanks.

how about you install kubuntu so you already have a sexy desktop by default... you can then even sexify it even more...

---

### Post by 5BallJuggler on 2009-11-04
If you go here

[http://ubuntuforums.org/showthread.php?t=281865](http://ubuntuforums.org/showthread.php?t=281865)

You'll find lots of useful....or not ways to sex up your desktop, the first few hundred pages are pretty basic and will teach you alot about the coding, towards the last pages it gets abit more indepth, but the extra work is well worth it, check out this site for some other info

[http://conky.linux-hardcore.com/?page_id=63](http://conky.linux-hardcore.com/?page_id=63)

Have fun.
Phil

---

### Post by PuddingKnife on 2009-11-04
- Change theme to "Night Impression"

- Reduce workspaces from 4 to 2

- Uncheck the "Expand" option top panel properties.

- Delete bottom panel

- Install Gnome-Do and set it to "Docky"

- Install compizconfig-settings-manager and:

1. Enable "Wobbly Windows"

2. Change Focus animation to "dodge"

3. Change minimize animation to "Curved Fold"

- Find a boat load of awesome wallpapers at interfacelift.com


Enjoy  :D

---

### Post by &#32 Greg on 2009-11-04
Make everything pink, get rid of window borders, obtain an awesome wallpaper, and run all your apps in transparent terminals.

---

### Post by jnew93 on 2009-11-04
> **NoaHall said:**
> First things first. System -> Admin -> Hardware Drivers

Then, look in the package manager for "compiz". Install it.

Then, install "avant-window-navigator"

Make sure compiz is running, then launch avant :).

This. Also, the reason that AWN wasn't working for you before is most likely because you didn't have compositing effects enabled on your desktop. To enable them simply run compiz, or if you would like to use AWN with metacity (used if you do not have desktop effects enabled at all) open a terminal, run:

```
sudo gconf-editor
```

then go apps --> metacity --> general --> click the box labeled "compositing manager"

Cheers! :D

---

### Post by fabounet on 2009-11-05
of course Cairo-Dock is supported (and the latest 2.1.1 version is just what you need to "sexify" your desktop) ;-)

---

### Post by ptrinder64 on 2009-12-14
I've revisited Cairo Dock and grossly misjudged it - it's awesome!

---

