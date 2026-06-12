---
title: "Problem with Firefox, compiz and emerald"
date: 2008-12-31
forum: General Help
---

### Post by lsutiger on 2008-12-31
I have a reoccurring problem with firefox, that I believe is being caused by compiz and emerald.
What happens (and I have no idea why it happens), but frefox will loose it's titlebar and take up all of the screen. I have a small panel to the right and that gets covered and AWN disappears. The only way to get out of that is to press F11 to go full screen then reverse. When it comes back, the emerald theme is no longer there, but the default Ubuntu one is there.

Anybody having similar problem?

8.04, ATI 1150 express video card on Dell Inspiron laptop.

---

### Post by gettinoriginal on 2008-12-31
In terminal type:

```
compiz --replace
```

Then download from synaptic "Compiz Fusion Icon"  it will enable you to select your window decorator and window manager.

Happy New Year :popcorn:

---

### Post by lsutiger on 2008-12-31
Thanx, bu I have all of that installed and running, and have had so for months. The problem jst started about 2 weeks ago. I read a couple of threads about it, but none of them solved the problem.

---

### Post by gettinoriginal on 2008-12-31
Go to CCSM > Window Decoration > Command and type Emerald --replace

---

### Post by caro on 2008-12-31
I had a similar problem the other day.  I clicked on a website that maximized the window and covered my panels, both top and bottom.  Hitting F11 twice allowed me to get back to normal, but when I would launch FF again, it would expand back.  

This fixed it for me:  Launch FF, hit F11 twice to get the window back to "normal."  Then click on the window and resize it smaller.  Hit the maximize button on the window so it moves back covering the whole screen except the top and bottom panel.  Close FF and relaunch.  FF should launch like normal.  

I'm not running Emerald so this may not work for you.

BTW - nice win for the LSU Tigers tonight in the Chick-fil-a Bowl.  (From an Auburn Tiger!  War Eagle!)

---

### Post by magnus0 on 2008-12-31
I've had this problem too

---

### Post by L8erG8er on 2009-01-01
Hey all, 

To fix the hidden title bar problem, go into CCSM (CompizConfig Settings Manager) and put a check mark next to Place Windows.  It's in the Window Management section of the CCSM.  Quick fix.

---

### Post by lsutiger on 2009-01-03
Thanx to all the replies,and thanx caro...I am still wondering where that team was all year :?

I have tried all those options but it stll pops up every now and then. I guess I'll live with it until a real fix comes along!

And good luck to your team L8erG8er..I'll be pulling for ya!

---

### Post by magnus0 on 2009-01-04
You can try deleting the .mozilla folder in your home. But backup your bookmarks before doing that!

---

### Post by zika on 2009-01-04
> **lsutiger said:**
> Thanx to all the replies,and thanx caro...I am still wondering where that team was all year :?

I have tried all those options but it stll pops up every now and then. I guess I'll live with it until a real fix comes along!

And good luck to your team L8erG8er..I'll be pulling for ya!

Go to CompizConfig Settings Manager->Utility->Workarounds->Legacy Fullscreen Support and uncheck it. [http://ubuntuforums.org/showthread.php?t=986482&highlight=ff+window+top+disappear](http://ubuntuforums.org/showthread.php?t=986482&highlight=ff+window+top+disappear)

---

