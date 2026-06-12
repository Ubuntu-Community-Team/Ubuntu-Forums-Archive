---
title: "32bit Desktop ?"
date: 2005-01-18
forum: Desktop Environments
---

### Post by mmuller on 2005-01-18
Can I set ubuntu to use a 32bit colour desktop. I have a laptop with a ProSavage card.

Mandrake, Fedora & M$ all work without problem in 32bit. 

Ubey doesn't want to play ball, I only have access to a nasty 24bit desktop that is all bandy when using small graduated images for the desktop picture.

---

### Post by Buffalo Soldier on 2005-01-18
Some interesting reading about 24 bit vs 32 bit color.
[http://www.studio1webdesign.com/basics6.html](http://www.studio1webdesign.com/basics6.html)

I think I have read somewhere that states 32 bit color is actually 24 bit color. Something that goes along the line of:

24 bit color = Red, Green, Blue
32 bit color = Red, Green, Blue + Alpha Channel

Still trying to look for that link. Will post once I find it.

Anyway if anyone knows more about color depth and knows that I'm wrong, please do correct me. I wouldn't want to be guilty of spreading any FUD.

---

### Post by niraj on 2005-01-18
You're right about the difference between 32 and 24 bit. 24-bit could look exactly like 32-bit. There is absolutely no difference in the number of colors each can display.

Can you tell us what you mean by "bandy"? Maybe your resolution is too low?

---

### Post by mmuller on 2005-01-21
[QUOTE=niraj]You're right about the difference between 32 and 24 bit. 24-bit could look exactly like 32-bit. There is absolutely no difference in the number of colors each can display.

Can you tell us what you mean by "bandy"? Maybe your resolution is too low?[/QUOTE]

The resolution is fine on screen, running at 1024x768 the maximum for the laptop lcd. under mandrake and windows the screen looks fine with nice smooth vignette's(gradients) but on warty and also hoary which don't offer me a 32bit desktop the bands show as blocks of colour instead of a nice smooth image. this is nothing to do with the image being scaled either as it happens when choosing a horizontal or vertical gradient too.

 :cry:

---

### Post by JimmyJazz on 2005-05-06
the gradients thing could have more to do with your driver than the colors, mine is in 24 mode and the gradients look fine.  However I would like to get 32 mode running.

---

### Post by Teo on 2005-08-27
[QUOTE=Buffalo Soldier]
24 bit color = Red, Green, Blue
32 bit color = Red, Green, Blue + Alpha Channel

Anyway if anyone knows more about color depth and knows that I'm wrong, please do correct me.[/QUOTE]
There is one very important advantage in 32bit color.
Everyone knows, that in 24bit we've got 8bit per each RGB channel (3*8bit=24bit) and in 32bits we've got 8bit per channel + 8bit for Alpha Channel (3*8bit+8bit=32bit), but 32bit is better than 24bit. Why? Coz it's easier (and faster) to transfer 2 times 16bits (in 32bit), than 3 times 8bit (in 24bit) :)

That's why I what 32bit color in my Ubuntu desktop :)

---

### Post by vr04 on 2005-09-26
i have the same problem as mmuller. gradients appear all "blocky" and don't really look like they should. there are no smooth transitions from one color to the other.

i also have a ProSavage, but i'm not sure where i can look for a better driver to solve the problem.

---

