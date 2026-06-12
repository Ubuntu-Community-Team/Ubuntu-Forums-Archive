---
title: "Pretty up a desktop, sans compiz/desktop effects?"
date: 2007-10-15
forum: Desktop Effects &amp; Customization
---

### Post by tschneiter on 2007-10-15
Hi all-
I am running gutsy on an intel 945gm video chipset. Also, I am using xrandr to allow for a hotswappable external monitor. As such, I need to have a "Virtual" line in my xorg.conf that gives my desktop the potential to be 2720x1924. My video chipset has a limitation where DRI cannot be enabled on anything that has the potential to be over 2048x2048, thus, I cannot use compiz/desktop effects/anything that requires DRI.

My question is, how can I pretty up my desktop without using desktop effects/compiz? Id love to have _some_ eyecandy, even if it is a bit primitive.

Also, does anyone know if there is some alternate compositing manager that doesnt require DRI?


Thanks for any input!

---

### Post by celettu on 2007-10-15
Lots depends on taste, of course. I'd check out the [monthly desktop thread]("http://ubuntuforums.org/showthread.php?t=564335"), see if there's anything you like.

---

### Post by Rupertronco on 2007-10-15
xcompmgr MIGHT not require direct rendering. I'm not sure as I haven't used it myself for more than a day of testing to see what it could do. I do recommend it to those who are unable to get compiz/beryl working and would still like some eye candy, namely avant-window-navigator (AWN) which, in my opinion, is the best dock available for a Linux desktop currently. 

For additional eye candy you can use screenlets, or gdesklets and select from a bunch of different docks (including kiba which has a bunch of eye candy) that do not require a compositor.

---

### Post by erginemr on 2007-10-15
You may try playing with the background color / translucency degree of the panels. (right click on them -> properties) 

I have seen very cute desktops without any composite manager, having the right combination of wallpapers (mostly green a la vista) and transparent panels.

---

### Post by tschneiter on 2007-10-16
Thanks for the tips everyone!

I installed xcompmgr, as well as AWN to give me a little eye-candy. I played with my panels a little, but didn't find anything too intriguing.

AWN ran terribly until I modified my xorg.conf's device section to look like so: (the options are what were added)
```

Section "Device"
	Identifier	"Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller"
	Driver		"intel"
	BusID		"PCI:0:2:0"
	Option "AccelMethod" "XAA"
	Option "XAANoOffscreenPixmaps"
EndSection

```

After that, AWN runs like a dream, though it isnt the most stable of things. Another big addition was Conky, which is eyecandy in that very geekish kinda way. 
Also, I used devilspie to create a terminal background for my fourth viewport. This looks neat but I dont know if Ill keep it around, since having to switch the the 4th just to get to it seems silly to me.

Righto, thanks for the suggestions everyone!

---

### Post by tschneiter on 2007-10-16
By the By, heres a screenshot of what I've come up with :) Hopefully this'll benefit someone.

---

### Post by Rupertronco on 2007-10-16
What's awn doing hanging out up there in the stratosphere? Or do you have two different resolutions on your monitors?

---

### Post by tschneiter on 2007-10-17
Hah, forgot to talk about that. Yeah, I've got my external  @ 1280x1024 and my internal @ 1440x900, so awn looks like its floating. Sadly, it means menus and pointers can drop off the bottom of the internal screen, but its tolerable. Id rather have that than one monitor :)

---

### Post by Rupertronco on 2007-10-17
> **tschneiter said:**
> Hah, forgot to talk about that. Yeah, I've got my external  @ 1280x1024 and my internal @ 1440x900, so awn looks like its floating. Sadly, it means menus and pointers can drop off the bottom of the internal screen, but its tolerable. Id rather have that than one monitor :)

I think I would too. Widescreen resolutions are incredibly annoying though. I mean, I love my displays (widescreen) but it seems as if they always need some extra bit of tweaking, or just don't quite do exactly as they're supposed to.

---

