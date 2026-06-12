---
title: "Frets on Fire: Some Frets Work, Others Don't"
date: 2007-10-08
forum: Gaming &amp; Leisure
---

### Post by tonyr1988 on 2007-10-08
I just got my PS2 guitar and USB adapter today, and it seemed to work immediately. When I go to key settings, I can define everything just fine (it recognizes my 1-5 keys as f,b,a,c, and d). But, whenever I test the keys (or play the game), the only things that work are the first fret, last fret, strum (both ways), and start button.

I've restarted the program, but it didn't work. What could be wrong, especially since it detects them fine when I define the keys? I'm using Feisty, and an unmodded FoF.

---

### Post by tonyr1988 on 2007-10-08
I found the problem - now I just need a solution. I found it while running jstest. When I push the first key (and hold it), it shows:

number 5, value 1

And, when I let go of the first key:

number 5, value 0

However, when I press/hold the second key, it shows:

number 1, value 1
number 1, value 0

And when I let go, it doesn't show anything. So, for some of the keys, it's doing a "quick press" and for others, it's actually holding it. Any idea what would be causing this bug? Is it probably adapter or software-related? I patched it per [this]("http://blog.yibble.org/2007/06/06/feisty-usb-joystick-issue-resolved/#comment-3796") guide, just in case that was my problem, but it wasn't.

---

### Post by tonyr1988 on 2007-10-09
Got it fixed. In case anyone on the interwebs finds this, it was my adapter. None of our RadioShacks had one (they said it was discontinued), and said that a PS2-to-PS3 adapter (by Pelican) should work, too. Apparently it didn't. However, I called back, and a RadioShack about 30 min. away had one, so I got that and it worked out-of-the-box! uber-w00t

---

### Post by Vadi on 2007-10-09
Looks like an interesting game.

---

