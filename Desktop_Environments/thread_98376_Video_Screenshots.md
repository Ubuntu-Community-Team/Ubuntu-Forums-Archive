---
title: "Video Screenshots?"
date: 2005-12-03
forum: Desktop Environments
---

### Post by agger on 2005-12-03
OK, there I was, writing a review of an online movie, and I wanted to include a couple of screenshots. 

Very easy: Pause xine, choose System/Take Screenshot, cut out the movie still and ready to go!

Except - this doesn't work! I get a blue rectangle where the xine window used to be. 

Tried the same in mplayer, same result. I didn't try totem because I never use it (usually doesn't work too good is my experience).

Is this some sort of copy protection restriction or are there technical reasons for this? AND, is there some workaround?

Thanks very much in advance
:KS

---

### Post by matthewv on 2005-12-03
Try changing the video renderer to "software" for the purpose of taking screenshots... change it back once you're done.

---

### Post by agger on 2005-12-03
[QUOTE=matthewv]Try changing the video renderer to "software" for the purpose of taking screenshots... change it back once you're done.[/QUOTE]

Thanks a lot! But how do I do that? The "Multimedia Systems Selector" doesn't seem to have such an option.

---

### Post by xmastree on 2005-12-03
Use Totem, there's a screenshot available in the edit menu.

Oh, and for normal screenshots you can use Print Screen for the whole desktop, or Alt-Print Screen for just the active window. None of that messing with menus.

---

### Post by matthewv on 2005-12-03
[QUOTE=agger]Thanks a lot! But how do I do that? The "Multimedia Systems Selector" doesn't seem to have such an option.[/QUOTE]
I think its a xine related option eg.. when using kaffeine with the xine engine, you select (I think) xshm as the video output, which is software output. It basically means that the cpu is rendering output, so the whole system sees it, as opposed to being output by the graphics card

EDIT: Doesn't xine have a take screenshot option??

---

### Post by cow_racer on 2005-12-03
I remember being able to take screen shot of movies played on ogle.

---

### Post by agger on 2005-12-03
I couldn't find any "render in software" option in connection to xine (I'm using GNOME), but the "Take screenshot" option in Totem worked. I still prefer xine and mplayer to Totem, though. 

But thanks a lot to all!
:KS

---

### Post by rejser on 2005-12-03
there is an option in mplayer also, don't remember the button though, but works great. maybe on mplayer homepage

---

### Post by jrib on 2005-12-03
```
mplayer -vo x11 moviefile
```

Should let you take screenshots.  Also if you are not aware of it, ALT+[PrntScrn]  will take a screenshot of only the currently selected window and not the entire desktop.

---

### Post by _4ace on 2005-12-03
use the screenshot capture in totem. It works just fine. The problem why you get a blue rectangle instead of the movie is that the video image you see on your screen is produced by your graphics card, therefore YOU can see it but your OS can't. just like the printscreen can't capture gdesklets animations

---

### Post by richardhp on 2006-02-05
I know it's not exactly the same kind of problem, but I was wondering if there was any way to take live video recording of the screen (gnome), in the same way as taking a screenshot, but storing the result as a video instead.

I'm not sure if this is even possible, but if it is it would be neat to take videos of linux to show off to my windows buddies.

Cheers

---

### Post by Madpilot on 2006-02-05
There's an app called "istanbul" that can apparently take video screenshots - I've never used it, though.

---

### Post by cwaldbieser on 2006-02-05
[QUOTE=richardhp]I know it's not exactly the same kind of problem, but I was wondering if there was any way to take live video recording of the screen (gnome), in the same way as taking a screenshot, but storing the result as a video instead.

I'm not sure if this is even possible, but if it is it would be neat to take videos of linux to show off to my windows buddies.

Cheers[/QUOTE]
[http://www.unixuser.org/~euske/vnc2swf/]("http://www.unixuser.org/~euske/vnc2swf/")

---

### Post by Ugeek on 2006-02-06
I use avidemux2 software for better result. is has frame capturing capacity. cheers.

---

