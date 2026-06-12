---
title: "Any suggestions . . ."
date: 2009-09-26
forum: Desktop Environments
---

### Post by Lukios on 2009-09-26
On the side I do a lot of computer work. Lately, they have all been older computers, most of which I have put Ubuntu on. I know there are other distros out there that run great on older computers but there are several reason why I choose to use Ubuntu. Anyways, I have been building these from the ground up using the Mini.iso. After doing a few of these computers, I realized that I will probably be doing more, I decided to go ahead and make my own Live Remix CD. For most of the older systems I have been using LXDE with the newer lxpanel 0.5.3 or gnome-panel along with the developmental AWN trunk. So far everything works well on most of the computers, but as you can imagine, some have really old graphics card and cannot handle certain composite managers. So my question is this. What are your experiences with different composite managers? Which ones have you found to be the most stable, fast, and least resource intensive as well as being able to run on most older cards. Though I have not had any problems running AWN smoothly on these computers (as old as P3) I am open to any suggestions to other docks you feel may be better for older systems. In my experience, the AWN dock does not require a lot of resources to run, but it does take a bit to load, which is pretty ugly to watch on an older computer. Basically, I want to make a CD that's going to work for the majority of older computers while being stable, fast and user friendly.

Also, I would like any feedback on what you guys think I should add to my cd to make things more user friendly and fast, as well as any other suggestions you may have. 

Just another thought, does anyone know how to set up a installation disk that will detect whether or not your graphics card can handle certain composite managers, and then automatically choose which dock and or composite manager would be best for that particular computer if one at all? Of course, I'm guessing I would have to set the parameters for this, but it would be a lot nicer if it was automatically done. This one is beyond me, but I thought it was worth asking.

BTW:  If your wondering why I want to use a dock for an older system, I have found that it has been easier for windows users to simply have what they need displayed at the bottom.

---

### Post by clonne4crw on 2009-09-27
I think you're better off scrapping the 3D-rendered dock and just making a GNOME-panel that looks like one. Make the size of it big, enable transparency if you wish, and disable it from expanding across the length of the screen. Hell, make a background image for it. It may or may not be as functional as AWN, but trust me, you will get way better performance. I've got a screenie of something that I threw together in about 5 minutes.

Just my thoughts on the whole thing...

--Edit--

Oh, yeah, I think there's a command to probe whether or not you have a 3D graphics card. I can't seem to remember what it was or where I read it, all I know that it worked in version 6.06. I'll keep looking, though. :)

---

### Post by clonne4crw on 2009-09-27
Here it is! Right under my nose!:

```

glxinfo | grep rendering

```

---

### Post by Lukios on 2009-09-27
Actually I did something similar with the lxpanel, but when I do the background transparent, it doesn't render it properly. Well it does, but if you put something behind it like a window, instead of seeing the window behind it, you will end up seeing the background of the wallpaper.

---

### Post by clonne4crw on 2009-09-28
And that is to be expected from older graphics cards that only support 15 or 16 bit color. Whatever works for you.

---

### Post by Lukios on 2009-10-01
actually I think its because its psedo (fake)-transparency

---

