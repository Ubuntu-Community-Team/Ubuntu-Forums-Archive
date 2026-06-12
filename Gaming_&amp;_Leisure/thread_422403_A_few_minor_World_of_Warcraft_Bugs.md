---
title: "A few minor World of Warcraft Bugs"
date: 2007-04-25
forum: Gaming &amp; Leisure
---

### Post by phatalbert on 2007-04-25
Hello all,

I'm running World of Warcraft with Wine on Feisty, and for the most part it works great now. There are a few nagging issues though.

1. Sound, I've tried both OSS and Alsa in the winecfg menu, and neither seems to make a difference.
2. I run the game at a lower resolution than my native screen resolution or my desktop resolution, which means that when the mouse reaches the side of the game screen instead of stopping it will scroll and I'll see my desktop wallpaper and lose half the game. I suppose I could adapt, but this is highly annoying.
3. The minimap. It shows up fine when I'm out in the world, but when I go into a city, specifically Ironforge, the mini map area is all white, and what looks like the map, but I can't be sure, flickers in the bottom right.

Anyone know how I can fix these?

---

### Post by willskills on 2007-04-25
1 - What is your sound buffer size in Config.WTF? (Do NOT select Alsa in winecfg - only OSS, and maybe Esound if you need it for mixing with a Voice Comms program)

2 & 3 sound like graphics drivers issues, to be honest, checking this would be a good idea;

[https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

Perhaps someone with a little more knowledge can help you with your graphical issues :)

I am running WoW on Feisty with sound, and a lovely framerate to boot!!!

---

### Post by phatalbert on 2007-04-25
My sound buffer size is set to 150, and I'm back on OSS now, but no help. I had originally followed the directions from that site you linked me.

I guess I should fiddle around with the buffer size?

For the video issues, I'm loading the drivers for my ATI Mobility video card with the restricted drivers manager, might that be the problem? And if so how would I fix it?

---

### Post by phatalbert on 2007-04-25
Okay, I fixed my sound issue by increasing the buffer to 200, and fixed the problem with scrolling off the game screen by just decreasing my desktop resolution every time I play, but it's still not perfect.

Two issues are still bothering me.

The first is the mini map will not display any time I am indoors, whether it's a dungeon, a house, or a city, it just shows up blank white, and flickers in the bottom left corner of the screen.

The other is framerate. It usually starts out pretty nicely, around 20-25, but as I play for longer it drops and drops and drops, until after about an hour, it's done in the single digits and unmanageable.

Anyone know a fix?

Thanks.

---

