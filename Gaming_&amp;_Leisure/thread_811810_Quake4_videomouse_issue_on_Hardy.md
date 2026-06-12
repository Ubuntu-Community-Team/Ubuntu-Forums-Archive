---
title: "Quake4 video/mouse issue on Hardy"
date: 2008-05-29
forum: Gaming &amp; Leisure
---

### Post by joemilx on 2008-05-29
Usually, when I start cold and immediately run Quake4, it comes up in full screen mode and runs fine.  However, if I start Firefox first or if I quit, then restart Quake4, it usually starts in a window with jumpy video and no mouse control.

I say "usually" because it is erratic.  Sometimes it fails after a cold start and sometimes it works after Firefox is started first.

In any case, once it happens, I shut Hardy down and try again.

I am using the restricted ATI driver on an X800 GT at 24 bit, 1440x900 on a Samsung 941bw LCD.  Other games, including Quake3, don't have this problem.

---

### Post by breadbin on 2008-06-04
Sorry for hijacking your thread but I have the same problem. Didn't associate it with firefox but it could be. Did you get it sorted? 

I was playing q4 fine there yesterday but now when I run it, it goes to a maximized window and I can't use the mouse. I can still use the console though and when I alt-tab to something and then back to q4 it goes fullscreen for maybe half a second and then back. I can stay in fullscreen mode and it proceeds as normal if I keep moving the mouse. Once I stop moving the mouse it exits fullscreen. obviously somehting grabbing the focus from it.

there was a thing in quake 2 called _windowed_mouse or something like that I will try it.

let me know if you got/get it fixed 

ed

btw im using hardy too on AMD64, latest nvidia drivers, everything up to date.

---

### Post by joemilx on 2008-06-04
Breadbin, it's nice to have company!  Have not found a solution yet.  Probably not the video driver, you being Nvidia and mine is ATI.  Write back if you figure it out.

---

### Post by breadbin on 2008-06-05
Hiya, I sort of figured it out. Well a workaround really. I changed the resolution in Quake to something other than the desktop res which for me is 1024x768 so I changed the quake res to 800x600 and it works like a dream now. some sort of bug there i guess. hope that works for you;)

---

### Post by Brebs on 2008-06-05
Try turning off DGA before running the game:
```
export SDL_VIDEO_X11_DGAMOUSE=0
quake4
```

---

### Post by joemilx on 2008-06-05
> **Brebs said:**
> Try turning off DGA before running the game:
```
export SDL_VIDEO_X11_DGAMOUSE=0
quake4
```
Thanks, Brebs.  That worked just fine for my situation.

---

### Post by joemilx on 2008-06-05
> **breadbin said:**
> Hiya, I sort of figured it out. Well a workaround really. I changed the resolution in Quake to something other than the desktop res which for me is 1024x768 so I changed the quake res to 800x600 and it works like a dream now. some sort of bug there i guess. hope that works for you;)
That worked but I'd like to keep my 16:10 aspect radio on the LCD.  I'll try what Grebs recommends.

---

### Post by fuzzmo on 2008-06-05
Just for completeness sake I have the same issue with Doom3 and penumbrablackplague... i'll check into changing resolution but it is strange to say the least... playing WoW on wine works perfectly....

---

### Post by breadbin on 2008-06-05
> **joemilx said:**
> That worked but I'd like to keep my 16:10 aspect radio on the LCD.  I'll try what Grebs recommends.

i didn't mean to set your resolution to 800x600 just something different to the desktop;) I might try the dga thing too its more complete fix instead of a workaround.

---

### Post by godvalve on 2008-11-10
> **Brebs said:**
> Try turning off DGA before running the game:
```
export SDL_VIDEO_X11_DGAMOUSE=0
quake4
```
Thank you for this useful info. I could get quake4 to run great, but I would lose mouse control at the main menu. Thank you!

---

### Post by vinyard on 2009-02-07
I went around this issue by setting r_fullscreen to "0" in ~/.quake4/qbase/Quake4Config.cfg. I got back control of my mouse & it allowed me to keep my desktop resolution & it still runs in fullscreen. Don't know why this works for me but it does.
Hope this helps someone else.

---

### Post by lenzoid on 2009-04-13
Your problem I guess is the same as **[that one.](http://ubuntuforums.org/showthread.php?t=1069365)** 

As I stated in that thread, with using Brebs' solution, **y-axis negative ceases to function**, which makes actual gameplay impossible. (tested with q3a but assuming q4 the same). Is there a fix or any1 having the same god damn problem? (I hope no one feels "insulted" by my language...)

*Happy quaking & play more promode!* ;)

---

### Post by vinyard on 2009-04-14
Well I don't have mouse lags. My cursor just didn't move when games had the same resolution as my desktop (1680x1050). Using a lower resolution works but I wanted to use my monitor native resolution. I think this has something to do with compiz but like I said in my previous post I got around this issue by playing in windowed mode while still having my game at my desktop's resolution. The game still looks like if it was being played in fullscreen & I can move the cursor. I tested this out with Quake 4 & Nexuiz running in sdl mode.

My cursor was also going crazy after about 10 minutes of playing a game I solved this by disabling the screensaver. (screensaver was set to kick in after 10 minutes.)

---

### Post by caravel on 2009-04-15
I had a similar problem to this with UT2K4.  Whenever I set the game resolution to the same as the desktop it would keep dropping into windowed mode and the X server mouse cursor would appear with the games cursor, those they would be in different parts of the screen.  I managed to solve this by simply disabling compiz before running the game.

---

