---
title: "i can't get Enemy Territory to run full-screen! :("
date: 2007-08-26
forum: Gaming &amp; Leisure
---

### Post by ijason on 2007-08-26
i've looked through a few threads that seemed similar, but none of them answered my question, so i'm posting this.

i can't get Enemy-Territory to run full screen! it installed fine. it works properly. i don't think that i'm having video-card issues, because the game runs like it should - just in a window. i've tried all kinds of [enter] twice and [alt] + [enter] options to try and make the window go full-screen. i can't drag the border. when i set the game to run in full-screen mode it still displays in a small window and turns the rest of my screen to garbage.

any suggestions? pls give step-by-step if you have directions for me, i'm still new at this.

/again, the game works perfectly. just ONLY in a window.
/this is the linux build of ET

---

### Post by asipi on 2007-08-27
goto ingame menu, you can check a checkbox for fullscreen or pull down ingame console with '~'-key and type:
[b]/seta r_fullscreen 1
/vid_restart[/b]

---

### Post by ijason on 2007-08-28
i tried your suggestion... it crashed my computer like nobody's business!

to be specific, the game goes full-screen and then locks up with keyboard and mouse being totally unresponsive until i do a hardboot.

---

### Post by asipi on 2007-08-29
not normal, I can do it on my system without problems.

What type of videocard you have?
Did you install the latest drivers for it?

---

### Post by ijason on 2007-08-29
it's an ATI, i'll install the new drivers and see if that fixes it.

/thanks for your help sofar

---

### Post by ijason on 2007-08-29
hmm. well, i attempted to install the new ATI drivers as described in this ([http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide)) guide, but the last step where you're confirming the install shows an error message similar to :
              ~$ fglrxinfo
                   * error, ATI dri not found*    (paraphrasing from memory)
                    display: :0.0  screen: 0
                   etc etc.

it also lists all the open GL drivers as Mesa drivers, instead of ATI. but now my Compiz effects aren't working >,< at least it looks like i was able to restore things well enough that the computer is working ok.

---

### Post by asipi on 2007-08-31
sorry I never had an ATI hardware, can't help more... But I recommend not to use compiz or beryl while playing 3D accelerated games, they could conflict to each other. This issue is not well handled in the linux distros.
On the other hand nvidia drivers are more stable under linux so I always recommend to use nvidia cards for gaming under linux.

---

