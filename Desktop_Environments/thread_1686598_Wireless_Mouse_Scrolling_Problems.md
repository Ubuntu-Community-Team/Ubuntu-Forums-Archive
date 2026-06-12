---
title: "Wireless Mouse Scrolling Problems"
date: 2011-02-12
forum: Desktop Environments
---

### Post by gdea73 on 2011-02-12
I have a wireless keyboard/mouse combo, and it's been nothing but problems in Ubuntu. I've finally figured out the other problems (back/forward buttons not working, nothing works at ALL randomly, etc), but this one prevails:

My mouse's scroll wheel is physically fine. However, whenever I scroll down for example, it's really erratic. It's kind of hard to explain, but if I scroll down 4 notches, the 4th always scrolls **UP**. Same way going up, the 4th time always goes **DOWN**. I was having problems with my previous wireless desktop, and exchanged it for a brand new one this afternoon. this is a brand new mouse, so the scroll wheel is NOT dirty or damaged. I tried it on a Windows laptop and it was fine.

So this isn't a hardware problem. I have btnx installed and working, tried assigning the scroll up and scroll down to actually REW/WHEELFORWARD and REW/WHEELBACK I think. But I had this problem *before* installing BTNX and enabling the scrolling up and down in btnx did not work.

What do I do? This is extremely frustrating ...

---

### Post by gdea73 on 2011-02-12
Interesting - as a test, I used BTNX to configure the scrollwheel differently:
ScrollUp I assigned to KEY_1
ScrollDown I assigned to KEY_2

... So opening gedit and scrolling up produces this:
1211111211111211111211111211111211111211 ... etc. 5 up, 1 down. really irritating.
same result scrolling down.

also, while doing this test, the mouse also scrolled lthe window around a bit too. Even though it was not supposed to...221222

---

### Post by Copper Bezel on 2011-02-12
Wow. And it's perfectly regular. So the hardware is functional, but it has some really weird driver stuff going on, then. I really doubt there's a simple fix. Did it require any "installation" if you've used it on a Windows machine? (God, I hate peripherals that can't just follow standards.)

---

### Post by jerrrys on 2011-02-12
go to edit>preferences 

[ATTACH]183322[/ATTACH]

and try scroll options

---

### Post by gdea73 on 2011-02-12
Thanks everyone for the help:

@ Copper Bezel - Yes, it had software that required it to function (supposedly). The thing that really sucks though is I had the **exact same model keyboard** on the SAME ubuntu installation, same PC - but this new one has the scrolling problem. Maybe it *is* hardware - but I figured if it was regular ...

@ jerrys: thanks for the suggestion, but I've already tried messing with the scrolling preferences in Firefox. And also, this affects every application that utilises scrolling - it's not simply limited to FF.

Any other help? This is really annoying ... time to dig through my mouse collection: PS/2, PS/2, dead, serial port for DOS :D , oh there's a MS USB one ...

---

### Post by gdea73 on 2011-02-13
Dang. it IS a hardware problem... tried it again on m y Windows PC and same problem... tried to take thing apart but didn't help at all.

---

