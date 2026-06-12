---
title: "D600 display problem"
date: 2008-01-22
forum: Dell  Ubuntu Support
---

### Post by scottws on 2008-01-22
I am running Kubuntu 7.10 Gutsy Gibbon on a Dell Inspirion D600 laptop.  It works fantastically for the most part, aside from some issues with Flash and Konqueror, and my wireless connection after suspending.

But I am having trouble with the display in some games that run full screen in a lower resolution than native.

For instance, I am running *Starcraft* through wine.  It works fine as long as I run it windowed.  The problem is that the game is 640x480, meaning it's a tiny little window on my 1400x1050 display.

If I run the game fullscreen, it works adequately except that there are two big vertical black bars on the screen.  One runs down the left side and one runs down just right of center.  It's almost as if the pixels are dead or something when this is happening because if you place the cursor in the area where the black bars are, the cursor will disappear.

This is not just a wine problem.  There was another Linux-native game I installed through the Add/Remove Programs Adept app that ran full screen at a lower resolution than 1400x1050 and it had the exact same problem.

I am using the open ati driver.  I tried installing the proprietary fglrx driver but the X Window System wouldn't start.

Any help on this issue would be much appreciated.

---

### Post by scottws on 2008-01-22
Update, I just tested setting my desktop to 640x480 @ 60Hz and a very similar thing happened.  The bars were in the same position, but they were white this time.  Again the cursor disappears behind the bars.

Also, I noticed the screen was flickering a bit.  The windows were sort of vibrating up and down and there was a thin horizontal line right at center that was flickering.

I tried setting the monitor from "Plug 'n Play" to "Dell 1400x1050 laptop monitor," but this made no difference after restarting the X Window System server.

Any ideas would be appreciated.

---

### Post by scottws on 2008-07-11
UPDATE:  I just tried *Starcraft* fullscreen again and it works fine now.  I don't know what the solution was, but I suspect is has something to do with updating to Kubuntu 8.04.

---

