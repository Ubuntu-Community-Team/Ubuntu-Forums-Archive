---
title: "How do I change the size of THIS text?"
date: 2007-03-25
forum: Desktop Effects &amp; Customization
---

### Post by pinche on 2007-03-25
Ever since switching to beryl, all of the text (pointed to by green arrows) seemed to go a few notches larger.  I don't like that, and I want to make it smaller.  I can't find any settings to change it.  

[IMG]https://webspace.utexas.edu/cer64/myspace/Screenshot.png?uniq=-2akaa9[/IMG]

---

### Post by ThrobbingBrain66 on 2007-03-25
I believe you can find what you need under System > Preferences > Fonts

---

### Post by pinche on 2007-03-25
> **ThrobbingBrain66 said:**
> I believe you can find what you need under System > Preferences > Fonts

Tried that, and it didn't fix anything.

---

### Post by jakev383 on 2007-03-25
> **pinche said:**
> Ever since switching to beryl, all of the text (pointed to by green arrows) seemed to go a few notches larger.  I don't like that, and I want to make it smaller.  I can't find any settings to change it.  



Right click Beryl, select Emerald Theme Manager. The font sizes are controlled by what theme you're using in Emerald. You can also edit the theme and change the size. It just takes a little looking and testing - the good thing is that your changes will be instantaneous, so you can see what your change did quickly.

---

### Post by ThrobbingBrain66 on 2007-03-25
Alright, try this now:

sudo dpkg-reconfigure fontconfig-config

---

### Post by ThrobbingBrain66 on 2007-03-25
> **jakev383 said:**
> Right click Beryl, select Emerald Theme Manager. The font sizes are controlled by what theme you're using in Emerald. You can also edit the theme and change the size. It just takes a little looking and testing - the good thing is that your changes will be instantaneous, so you can see what your change did quickly.

I've never seen options for changing font size in beryl.  You can change the size of the window border fonts, but nothing else...unless I've just missed the option.

I just played with the font settings in System > Preferences > fonts and they change for me (I'm using Beryl as well).  I'd reconfigure the fonts like I suggested in the previous post.  Maybe it's just the screenshot, but your fonts look horrible.  A reconfigure could do you some good:)

---

### Post by pinche on 2007-03-25
> **ThrobbingBrain66 said:**
> Alright, try this now:

sudo dpkg-reconfigure fontconfig-config

This didn't help much either.  

> Right click Beryl, select Emerald Theme Manager. The font sizes are controlled by what theme you're using in Emerald. You can also edit the theme and change the size. It just takes a little looking and testing - the good thing is that your changes will be instantaneous, so you can see what your change did quickly.

I've spent some time trying to fix it by modifying the theme, but I guess I'll take another look.

---

### Post by ThrobbingBrain66 on 2007-03-25
Do you have an LCD screen?  
Have you tried changing your font rendering to "sub-pixel smoothing" in that same fonts menu we were in before?  Then go into 'details...' to change things even further.  Within the details menu, I have smoothing set to subpixel,  hinting set to full and subpixel order set to RGB.  Personally, I think my fonts look great.

[[IMG]http://img147.imageshack.us/img147/3138/screenshotfv4.th.png[/IMG]](http://img147.imageshack.us/my.php?image=screenshotfv4.png)

---

### Post by pinche on 2007-03-25
> **ThrobbingBrain66 said:**
> Do you have an LCD screen?  
Have you tried changing your font rendering to "sub-pixel smoothing" in that same fonts menu we were in before?  Then go into 'details...' to change things even further.  Within the details menu, I have smoothing set to subpixel,  hinting set to full and subpixel order set to RGB.  Personally, I think my fonts look great.

[[IMG]http://img147.imageshack.us/img147/3138/screenshotfv4.th.png[/IMG]](http://img147.imageshack.us/my.php?image=screenshotfv4.png)

Yeah, I've tried that already.

---

