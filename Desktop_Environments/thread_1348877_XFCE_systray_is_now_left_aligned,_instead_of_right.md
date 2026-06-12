---
title: "XFCE systray is now left aligned, instead of right???"
date: 2009-12-07
forum: Desktop Environments
---

### Post by ProDigit on 2009-12-07
I left my computer on for about 5 days in a row, putting it to sleep or hybernate at night.
Now I noticed that the volume, clock and the little exit sign to quit or close down the desktop are aligned to the left, right next to the FF and HELP icons.

How can I get them back in original position? (some icons aligned to the left, while others to the right of the top bar)...?

---

### Post by m_duck on 2009-12-08
I've not got an XFCE box to hand at the moment, but I think to move the items around the panel, you just need to right click one (such as the exit icon) and click move. Then move the mouse to position it where you would like (you should see a black bar to show where it will end up) and left click to drop it. As I said, I *think* that's right but cannot check. As for why they moved, I've no idea, could be something as simple as an update modifying something.

---

### Post by ProDigit on 2009-12-08
I've tried that, but with no avail,

Here's a possible reason:
I had a game called ONI, on a CD, which I wanted to test if it worked on wine.
The game's intro movie started nice, but it crashed as the game was about to start. It's a 3rd person 3d action game.
When I got back to my desktop, it had a 640x480 or 800x600 resolution or something similar. All my icons where in this small window.
I reset the value to 1280x800 but noted that the icons still remained organized on the left top of the desktop.

The icons on the top bar, where about the same aligned. If I want to move them by rightclicking and 'move', the icons stay left aligned.
I can reorganize them, but not align them to the right.
I tried restarting but without much avail.

Please help :(

---

### Post by m_duck on 2009-12-08
Is the window list still displaying? I think it is usually that that "expands to fill" the gap between left and right aligned applets. Failing that, I think if you add a separator, if you go to its properties, you can set that to be invisible and expand which should push the items to the far left/right.

It's possible I'm just talking nonsense as I'm working from memory at present, I will try have a play with XFCE at some point soon. If the above doesn't work could you post a screenshot so I know I'm interpreting correctly?

---

### Post by ProDigit on 2009-12-10
Here's a slightly cropped sample:
[IMG]http://img689.imageshack.us/img689/7734/desktopesg.jpg[/IMG]

---

### Post by rabidbadger on 2009-12-11
There probably isn't any weirdness going on, other than an expanding separator having gotten moved to the RHS of the panel. So that we can see exactly how the panel is configured, can you post the output of the following, please (type into a 'terminal' window):

```
cat ~/.config/xfce4/panel/panels.xml
```

---

### Post by XubuRoxMySox on 2009-12-11
That's what it looks like to me too. Right click on the black space to the right of the "exit door" and select "Remove." Or you could select "Move" if you prefer and put it to the left of the "exit door." It looks like a "stretched" separator.

-Robin

---

### Post by ProDigit on 2009-12-19
I fixed it by adding a line or separator between the question mark and the battery indicator.
thanks anyways!

---

### Post by eugenevdm on 2011-05-12
> **m_duck said:**
> ...Failing that, I think if you add a separator, if you go to its properties, you can set that to be invisible and expand which should push the items to the far left/right...

Thanks that did it for me.

---

### Post by perdubug on 2012-12-20
How about this? Open 'Panel Preferences'->select your panel,1 or 2->'Diaply' tab->Uncheck 'Lock panel',then drag your item even panel1/panel2 to a right position. Remember to lock it again if you like.

---

### Post by Toz on 2012-12-20
Thank you for sharing, but this thread is over a year old. Please do not post to stale threads. Closing.

---

