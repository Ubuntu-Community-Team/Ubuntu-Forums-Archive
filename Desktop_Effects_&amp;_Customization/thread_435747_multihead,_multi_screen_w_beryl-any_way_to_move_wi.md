---
title: "multihead, multi screen w/ beryl-any way to move windows between screens"
date: 2007-05-07
forum: Desktop Effects &amp; Customization
---

### Post by timczer on 2007-05-07
I have posted this problem already, but with no help so far.  I think the post title was not right.  anyway...

I have beryl running on two seperate screens, with two nvidia cards.  I have read on the beryl forum that you cannot drag windows from screen to screen with this setup.  It does not seem possible from what I have read on these forums, as well as Beryl's forums, and anything I have googled, that you can run xinerama and beryl at the same time (RandR problems).  

My goal is that if I cannot drag a window from screen to screen, is there any way to tell it to go to the other screen.  Action taken on one screen does affect the other. (if I have an Openoffice doc open on screen 1 and try to open one on screen 0 it will follow the first one to screen 1.)  In metacity you had the option in the title bar of sending an open window to another desktop.  So, is there a way to move the window from screen to screen without dragging?

Lastly, if this is not possible, how do I get the app I am opening to stay  on the screen I opened it in.  If I have a Calc sheet open on one screen I want to be able to open another on the second screen so I can see both at the same time (this is why I used xinerama set up).  Currently, as I mentioned above, when one sheet is open, the second will follow to the same screen as the first, regardless from which window it was opened.

Thanks for any help you can give on either of these goals.

---

### Post by hartz on 2007-05-07
Have you tried nVidia TwinView mode?

Have a look at this page: [http://www.phoronix.com/scan.php?page=article&item=387&num=1](http://www.phoronix.com/scan.php?page=article&item=387&num=1)

What I don't know is if TwinView can work across multiple GPUs.  If it does not, you may as well use both the ports from one of the two cards that you have installed.

I've done some searches on this forum and there are many posts on Beryl + Twinview, etc, so have a look around.

Even with Twinview setting up a single desktop, I find that windows sometimes does not obey the "stay-local" settings.  Well-behaved programs should be able to keep their child-windows go to either
+ Same window as parent, or
+ Same window as Mouse Cursor

depending on your settings, Window manager, application, etc your millage will vary.

You can however definitely move windows from one screen to the other.

---

### Post by timczer on 2007-05-07
I have googled this extensively, and I have not found a way to use twinview with two separate, single head video cards.  

I keep running up against the xinerama, beryl conflict.  It appears that I can drop beryl, and turn xinerama back on and get a large desktop with dragging, I can keep beryl running on two separate desktops with no moving windows, or go out and buy a new two-head video card and use twinview and beryl.

---

### Post by hartz on 2007-05-08
Those do indeed seem like your only options.  It looks like just about all current Graphics card, even the cheapest ones, have two outputs however, what model nVidia cards are you using?

---

### Post by timczer on 2007-05-08
One is the one on board the computer, the other a pci card.  They are both GeForce4 MX (one is nForce the other is 4000).

---

