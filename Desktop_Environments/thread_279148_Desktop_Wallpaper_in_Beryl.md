---
title: "Desktop Wallpaper in Beryl"
date: 2006-10-17
forum: Desktop Environments
---

### Post by igknighted on 2006-10-17
Is it possible to put a different wallpaper on each side of the cube?  It didn't work in compiz, but I was hoping that since each side is a virtual desktop now perhaps it was possible.

---

### Post by Aberrix on 2006-10-17
This would be very cool and I'd be interested as well.

---

### Post by emil.s on 2006-10-31
No one who know? It would realy be cool. :cool:

---

### Post by banankrem on 2006-11-03
Yes, it would be really cool. 
If it was possible to split a 4x widescreen wallpaper over the entire cube. That would give the user a more complete view. All though I do not know where I would find such wide wallpapers.

Anyone knows?

---

### Post by igknighted on 2006-11-03
I suppose you could put together 4 wallpapers with gimp, sort of a conglomeration... I would be concerned about getting all the sizes exactly right though

---

### Post by banankrem on 2006-11-03
> **igknighted said:**
> I suppose you could put together 4 wallpapers with gimp, sort of a conglomeration... I would be concerned about getting all the sizes exactly right though
Yes, but is it possible to choose a seprate wallpaper for each desktop? Shoudn't be too hard getting it right in Gimp though, while you know your resolution..

---

### Post by phoeganleisha on 2006-11-11
I actually tried doing that. It acts like it's a 1280x1024 window, so your larger image just gets cropped until it fits, which gets you a half/half wallpaper on every workspace.

Wallpapoz doesn't work either.

---

### Post by SaltyTaro on 2007-01-06
*bump*
i want to know the answer to this problem myself

---

### Post by qamelian on 2007-01-06
I'm running Beryl 0.1.5-svn and the Beryl Settings Manager now has a plugin in the Desktop section call Wallpaper Manager for just this purpose.

---

### Post by SaltyTaro on 2007-01-06
hhmm, i just followed a bunch of how-tos when i installed my beryl.  how do i know which version i have, and how do i upgrade?

---

### Post by qamelian on 2007-01-06
> **SaltyTaro said:**
> hhmm, i just followed a bunch of how-tos when i installed my beryl.  how do i know which version i have, and how do i upgrade?

If you run the Beryl Settings Manager, it should display the version number in the title bar of the settings window.

---

### Post by smartsonny00 on 2007-01-06
i don't want to seem retarded but i don't understand how the wallpaper manager for svn works... why are there so many background.pngs

---

### Post by qamelian on 2007-01-06
> **smartsonny00 said:**
> i don't want to seem retarded but i don't understand how the wallpaper manager for svn works... why are there so many background.pngs
I don't use it myself, but I believe you just double-click on one of the slots for a wallpaper and enter the path and filename: ```
/home/USERNAME/my_wallpapers/cool_image.png
```

You can probably delete the unnecessary slots.

---

### Post by Ptero-4 on 2007-01-06
Isn't the wallpaper thing defined by the wallpaper app in your DE? Because if it is, then gnome doesn't have the ability to put one wallpaper in each workspace.

---

### Post by Pallazzio on 2007-01-07
I deleted the extra slots and pointed it to 4 different images but nothing happened.  Does anyone know if there is something else i have to do?

thx

---

### Post by emil.s on 2007-01-07
NICE!
Anyone who know when 1.5 will be stable?

---

### Post by qamelian on 2007-01-07
> **Ptero-4 said:**
> Isn't the wallpaper thing defined by the wallpaper app in your DE? Because if it is, then gnome doesn't have the ability to put one wallpaper in each workspace.

It's handled by the window manager. Although Metacity doesn't handle this feature, other window managers do. When you are using Beryl, Metacity is no longer the window manager, Beryl is. It is the window manager, not gnome itself that gives you this ability.

---

### Post by smartsonny00 on 2007-01-07
> **Pallazzio said:**
> I deleted the extra slots and pointed it to 4 different images but nothing happened.  Does anyone know if there is something else i have to do?

thx

i did this too, and nothing happened... the background.png file is like just a pixel for me as well...

---

### Post by Pallazzio on 2007-01-14
I got it to work, sort of.  I have separate wallpapers now, but no desktop icons.  Here's what I did:

In a terminal type: gconf-editor 
apps -> nautilus -> preferences               uncheck show_desktop
desktop -> gnome -> background            uncheck draw_background

then I think I had to log out or at least restart beryl for it to work.

---

### Post by orb9220 on 2007-01-15
Yeah I to tried this awhile back with no joy. 
Probably just me. 

But I was wanting the screensaver plugin which goes to cube zoom back and starts to rotate as a screensaver type effect after so many minutes of inactive keyboard or mouse events.

Guess I'll just have to wait for the stable version with those effects already included.

In SVN I saw alot of plugins you had to compile against such and such version of beryl and so on and so on.

---

### Post by Peter Sommer-Larsen on 2007-02-22
Could someone plz help..
I have just installed Beryl, and it works fine (although I have no 3D accel)

My problem is, that every time i press on my desktop, it moves it a bit down, and then I
see, that the same desktop is behind.. wierd.. so I must have like two desktops..
It look really ugly, because ive got a black line in the top section of my desktop..

---

### Post by vedace on 2007-03-07
> **Peter Sommer-Larsen said:**
> Could someone plz help..
I have just installed Beryl, and it works fine (although I have no 3D accel)

My problem is, that every time i press on my desktop, it moves it a bit down, and then I
see, that the same desktop is behind.. wierd.. so I must have like two desktops..
It look really ugly, because ive got a black line in the top section of my desktop..

It sounds like you have Beryl set to initiate cube rotation whenever you press your mouse button (on your desktop).

Run beryl-manager, click on the "Desktop" tab, the "Rotate" sub-tab, and the "Shortcuts" sub-sub tab.  Then expand the "Bindings" entry, and under the "Mouse" column, in the "Initiate Rotation" row, change the entry from "Button1" to whatever you want to use to initiate cube rotation (for example, "<Control><Alt>Button1").

---

### Post by rainwalker on 2007-03-07
In the Beryl Settings Manager (I'm assuming you're running the same version of Beryl that I am) in "General Options" under the "Desktop Background" tab there's a checkbox for "Desktop Manager Supports viewports". I don't know if that's what you're looking for, but when I check it 3 out of my 4 desktops becoms transparent (the non-transparent one being the one with the Beryl Settings Manager open on it) with no way to set a background...just a hunch, but look into that and you might find what you're looking for. Hope that helps  :)

---

### Post by freebird54 on 2007-03-07
Strange - I just got updated last night, and that item (Wallpaper) is GONE now.  However - it could be because I wasn't the only one who crashed every time I activated it??

However - in the last week I went from what I would call "proof of concept" usability to fairly stable and good looking effects in Beryl.  The effects have smoothed out, everything is quicker, and it has been running 48 hours now without any downs (!)

Your mileage may vary....

(BTW - I put the improvements down to being able to run in auto mode rather than copy mode.)

---

### Post by usergentoo on 2007-03-09
I upgraded this morning and the wallpaper plugin is gone on mine also.

---

### Post by vinx on 2007-04-20
Want to know which side of the cube you are?

Set the cube-options "Opacity when not moving" to 95%
Use the attached file as background image for the cube. It is an black image with the numbers 1 to 4 on it. You can optionally switch the dull black color with your favourite image, but notice it will be somewhat visible on your desktop.

---

### Post by darkbluexplorer on 2007-09-18
did anyone ever get the desktop icons back? i have lost mine!

---

