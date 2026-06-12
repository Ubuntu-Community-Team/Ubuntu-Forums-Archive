---
title: "Incorrect monitor size after install"
date: 2009-04-23
forum: General Help
---

### Post by ghostu on 2009-04-23
Hi,

I have a 28" HannsG monitor hooked up to my pc.  After installing 9.04 today the display looked sharp, but a little off.  I checked the Display settings under the Preferences and it shows HSD 27".  What would be the best way to force Ubuntu into detecting my 28" monitor?

---

### Post by miegiel on 2009-04-23
> **ghostu said:**
> Hi,

I have a 28" HannsG monitor hooked up to my pc.  After installing 9.04 today the display looked sharp, but a little off.  I checked the Display settings under the Preferences and it shows HSD 27".  What would be the best way to force Ubuntu into detecting my 28" monitor?

The inches aren't really important. You want the right number of horizontal and vertical dots and the right refresh rate. If the HSD 27" has the same resolution and refresh rate as your 28" just leave it.

(just in case you don't know where to set it)
System > Preferences > Screen Resolution

---

### Post by ghostu on 2009-04-23
The refresh rate that it shows is 60Hz which should be fine.  The problem is that when I maximize a window, the right side of that window is now cut off.  Thus, I only see a part of the scrollbars.

Very strange.

---

### Post by miegiel on 2009-04-23
> **ghostu said:**
> The refresh rate that it shows is 60Hz which should be fine.  The problem is that when I maximize a window, the right side of that window is now cut off.  Thus, I only see a part of the scrollbars.

Very strange.

I guess it's not the right resolution then, your monitor manual should state the optimal resolution.

---

### Post by nandemonai on 2009-04-23
> **ghostu said:**
> The refresh rate that it shows is 60Hz which should be fine.  The problem is that when I maximize a window, the right side of that window is now cut off.  Thus, I only see a part of the scrollbars.

Very strange.

There should be an auto adjust function on your monitor (that's assuming you have a supported resolution running).

---

### Post by ghostu on 2009-04-23
> **nandemonai said:**
> There should be an auto adjust function on your monitor (that's assuming you have a supported resolution running).

LOL, you win!  That's exactly what the problem was.  Thanks so much!

btw... any of you guys know if KVM switches work well with Ubuntu?

---

