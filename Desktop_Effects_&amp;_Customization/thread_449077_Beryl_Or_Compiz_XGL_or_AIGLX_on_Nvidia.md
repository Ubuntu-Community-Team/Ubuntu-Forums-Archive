---
title: "Beryl Or Compiz XGL or AIGLX on Nvidia"
date: 2007-05-19
forum: Desktop Effects &amp; Customization
---

### Post by atari05 on 2007-05-19
Ok so I have tried Beryl and compiz

So far, Beryl has better performance for me and I like most of the plugins and the fact they give me a sane way to configure plugins.

Couple of things I miss though

1.) viewport and "expose" funcationality
2.) having wobble effect menus etc. - I know this just might be because I haven't configured it yet but...figured I would metion it.

Also, ...I totally want the burn plugin, is there a package for that yet?


Last but not least, 

I have an Nvidia 8800GTS and Though ubuntu gives me AIGLX out the door, would XGL be better?


Thanks for the help in advance, ...keep on rawking!!!

---

### Post by reacocard on 2007-05-19
> **atari05 said:**
> Ok so I have tried Beryl and compiz

So far, Beryl has better performance for me and I like most of the plugins and the fact they give me a sane way to configure plugins.

Couple of things I miss though

1.) viewport and "expose" funcationality
2.) having wobble effect menus etc. - I know this just might be because I haven't configured it yet but...figured I would metion it.

Also, ...I totally want the burn plugin, is there a package for that yet?


Last but not least, 

I have an Nvidia 8800GTS and Though ubuntu gives me AIGLX out the door, would XGL be better?


Thanks for the help in advance, ...keep on rawking!!!

1) Not sure what you mean, can you explain this better?

2) Just check the 3 Menu checkboxes in Beryl Settings Manager -> Visual Effects -> Wobbly WIndows -> Advanced -> Map  and then fiddle with the sliders just below them until you get an effect you like.

For burn, go to Visual Effects -> Animations -> Close (and Create) and set #1 to Burn.

I think AIGLX is better.

---

### Post by FuturePilot on 2007-05-19
You seem to have a great graphics card. Don't bother with XGL. XGL causes too many problems. It kills your video playback.

---

### Post by atari05 on 2007-05-20
> **reacocard said:**
> 1) Not sure what you mean, can you explain this better?

2) Just check the 3 Menu checkboxes in Beryl Settings Manager -> Visual Effects -> Wobbly WIndows -> Advanced -> Map  and then fiddle with the sliders just below them until you get an effect you like.

For burn, go to Visual Effects -> Animations -> Close (and Create) and set #1 to Burn.

I think AIGLX is better.

the comparison is between compiz and beryl. With compiz (by default) I got a view port if I moved the mouse to the lower right hand side. Also, if I held crtl+alt+downarrow I would get a titled overview of open windows much like apple's expose`. There was also the the "panel" method of moving to different Virtual Desktops.

I 'm sure if I play with beryl configs that I can get it to do that but when I was running compiz, I couldn't find for the life of me how to get the "burn" feature so I didn't think it would work or exsist in compiz. Though I could be wrong! I'm new to the whole 3D DE's so forgive my lack of knowledge :(

as a matter of fact, Let me do a little netsearch on how to capture some video of my DE with compiz, then I show the 3 things I'm talking about if its still foggy.

---

### Post by atari05 on 2007-05-20
Ok, ...its small but I think it gets the point across.

In the video you will see the expose like title view, then the the view port (mouse moves to right bottom corner) and then the panel vde switcher

[http://s130.photobucket.com/albums/p266/atari05/?action=view&current=compiz_tasks.flv](http://s130.photobucket.com/albums/p266/atari05/?action=view&current=compiz_tasks.flv)

---

### Post by greatmetal on 2007-05-20
I love Beryl and AIGLX combination. Its fast and you still have direct rendering while using it. Plus unless you cant get composite its kinda pointless to use XGL seeing as it uses more resources.

---

### Post by reacocard on 2007-05-20
> **atari05 said:**
> the comparison is between compiz and beryl. With compiz (by default) I got a view port if I moved the mouse to the lower right hand side. Also, if I held crtl+alt+downarrow I would get a titled overview of open windows much like apple's expose`. There was also the the "panel" method of moving to different Virtual Desktops.

Settings for expose are under WIndow Management -> Scale, and for desktops everything is under, well, 'Desktop'. You can bind things to the screen corners in General Options -> Shortcuts (and to key/mouse combos too).

FYI, for capturing video, [xvidcap]("http://xvidcap.sourceforge.net/") is probably your best bet.

---

### Post by atari05 on 2007-05-21
> **reacocard said:**
> Settings for expose are under WIndow Management -> Scale, and for desktops everything is under, well, 'Desktop'. You can bind things to the screen corners in General Options -> Shortcuts (and to key/mouse combos too).

FYI, for capturing video, [xvidcap]("http://xvidcap.sourceforge.net/") is probably your best bet.

Thanks a MILLION. This was exactly the lead I needed. I figured it would be in one of the plugins, I just needed a good start. 

many thanks to everyone for the help!

---

### Post by kaede on 2007-05-21
anyone have problem with vlc player while running beryl? my vlc can;t display any video. but i still have the sound.

---

### Post by walkerk on 2007-05-21
> **kaede said:**
> anyone have problem with vlc player while running beryl? my vlc can;t display any video. but i still have the sound.

you need to go into preferences and change the output mode in vlc.. easy fix :)

---

### Post by reacocard on 2007-05-21
> **kaede said:**
> anyone have problem with vlc player while running beryl? my vlc can;t display any video. but i still have the sound.

The only mode that works is the X (not XVideo) output, but it's not accelerated, so it'll used LOTS of CPU.  Other players (totem, xine, etc.) seem to have no trouble with XVideo under Beryl, so it might be better just to switch to one of them.

---

