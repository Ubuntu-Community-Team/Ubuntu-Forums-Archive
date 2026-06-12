---
title: "Window Appearance changes"
date: 2012-01-26
forum: Desktop Environments
---

### Post by caseykoons on 2012-01-26
Hello all.

I'm new to ubuntu, having been a Mac geek for many years.
The glitch I'm experiencing is minor and aesthetic, I mostly worry about it as a sign of instability.

When I suspend the computer and re-awaken it, all the active windows title bars are dimmed. The buttons are dim dark grey rather than the red close button, and the title is grey rather than white. Focusing on the window does not remove this effect. Oddly, focus away from a window does not trigger it either, it only occurs after sleep.
[IMG]http://farm8.staticflickr.com/7011/6768785603_9ea8228bd4.jpg[/IMG][IMG]http://farm8.staticflickr.com/7149/6768785677_2898a4832d.jpg[/IMG]
I've installed 11.10 on a new HP Pavilion g7 laptop with an ATI Radeon HD 6250g graphics card. I am using fglrx because I could not get the RADEON open-source driver to recognize my display. If anyone knows about my window glitch, or possibly how to get the open-source driver to recognize my graphics card, I would be grateful.

---

### Post by jefelex on 2012-01-26
> **caseykoons said:**
> Hello all.

I'm new to ubuntu, having been a Mac geek for many years.
The glitch I'm experiencing is minor and aesthetic, I mostly worry about it as a sign of instability.

When I suspend the computer and re-awaken it, all the active windows title bars are dimmed. The buttons are dim dark grey rather than the red close button, and the title is grey rather than white. Focusing on the window does not remove this effect. Oddly, focus away from a window does not trigger it either, it only occurs after sleep.
[IMG]http://farm8.staticflickr.com/7011/6768785603_9ea8228bd4.jpg[/IMG][IMG]http://farm8.staticflickr.com/7149/6768785677_2898a4832d.jpg[/IMG]
I've installed 11.10 on a new HP Pavilion g7 laptop with an ATI Radeon HD 6250g graphics card. I am using fglrx because I could not get the RADEON open-source driver to recognize my display. If anyone knows about my window glitch, or possibly how to get the open-source driver to recognize my graphics card, I would be grateful.

Do the close and minimize buttons still work like they are supposed to when they are greyed out like that?  have you installed both the suspend and the hibernate libraries?

John

---

### Post by caseykoons on 2012-01-26
They do function yes.

I have not installed any additional libraries for suspend and hibernate. Which packages do you recommend?

Thanks!

---

### Post by jefelex on 2012-01-26
> **caseykoons said:**
> They do function yes.

I have not installed any additional libraries for suspend and hibernate. Which packages do you recommend?

Thanks!

I'm not exactly sure with 11.10 - but in 11.04 the libraries are called uswsusp and hibernate - they should be the same for 11.10.  I have an HP G62, doesn't have that problem in 11.04, I have also just discovered as I write this that I do not have them installed either! :-) - but then again I don't bother with suspend or hibernate - If I'm done, I just shutdown.

---

### Post by caseykoons on 2012-01-29
> I'm not exactly sure with 11.10 - but in 11.04 the libraries are called uswsusp and hibernate...

I installed the libraries suggested above, and while they did seemed to speed the laptop's ability to hibernate, it did not fix the window appearance problem.

I have noticed a new fix of sorts to the problem. If I resize the window using the Compiz Grid feature, to take up half of the screen or maximize it, the buttons and title bar returned to true brightness.

Again, I realize this is a minor glitch, it does not really affect function. I'm a recently former Mac user that perhaps cares too much about interface consistency. But I worry that I broke my window management system's stability by messing around in the Compiz Settings Manager. I really love Ubuntu's features and speed, and I want to use it as my primary OS, but I keep getting dragged into glitches.

Any advice or words of encouragement would be welcome.

---

