---
title: "Resolution not sharp like in Windows"
date: 2007-02-07
forum: Desktop Environments
---

### Post by sokre on 2007-02-07
I am a beginner, have Ubuntu 6.1 since 5 days ago... my first Linux.
I have Toshiba Satellite 1955-S803 laptop with Geforce4 440GO (64MB - this is not shared)
I had problem with low resolution, managed to get it to 1240x1024, also have latest nvidia drivers. 
3D is enabled - checked in terminal... 
(also I have Nvidia logo upon start)

Problem:
Picture on my 16" LCD is somewhat different than in Windows XP.
It was hard to notice it at first, since I had 1024x768 and when I got 1240x1024, 
it look so much better, but after a while i noticed it...
I ll best describe it in Firefox on Ubuntu 6.1.
Everything is streched - letters, new tab button, pages...
It looks not as near as good like in windows.
My eyes hurt after some time.
When I open [www.google.hr](www.google.hr)  those 3 small circles 
(under search bar in the middle of page)
look like i have drawn them by hand when I was drunk.
- just to describe it best.
I doubt it has much to do with fonts, maybe little with font smoothing, 
but there must be some other explanation.

1. Does your Firefox looks same (I mean picture quality) in ubuntu as in windows?
   I hope I do not have to leave it this way.
2. Can someone tell me what to do to fix this?

PS
I am beginner, but I am comfortable with terminal, exiting X, starting it....
Just to know what are you dealing with.

---

### Post by sokre on 2007-02-07
This is what I am talking about

---

### Post by sokre on 2007-02-07
And this is how it looks in windows xp

---

### Post by damvcoool on 2007-02-07
I think that's only the theme, if change your Desktop Theme or/and your Firefox theme it would look much better

---

### Post by liljoe76 on 2007-02-07
to me it looks like font issues.. i had 2 tabs open swapping back and forth. the icons look the same res, but the ubuntu fonts are larger, bolder and fuzzier. 
i know i ended up changing all my fonts to berylium, 11+ points on a 1280x800.

---

### Post by sokre on 2007-02-07
I ll try to change theme or font, but I doubt it is it.

---

### Post by mcduck on 2007-02-07
If those radio buttons are what you are talking about then that's a 'feature' of linux version of Firefox. In short, it's not using buttons and widgets from Gnome, instead it has some really really old and ugly widgets of it's own. But you can replace them with nicer ones:

```
wget http://users.tkk.fi/~otsaloma/art/firefox-form-widgets.tar.gz
tar -xvzf firefox-form-widgets.tar.gz
sudo cp /usr/lib/mozilla-firefox/res/forms.css /usr/lib/mozilla-firefox/res/forms.css.bak
cat firefox-form-widgets/res/forms-extra.css | sudo tee --append /usr/lib/mozilla-firefox/res/forms.css > /dev/null
sudo cp -r firefox-form-widgets/res/form-widgets /usr/lib/mozilla-firefox/res
rm -rf firefox-form-widgets
```
After that restart Firefox and now you have smooth looking widgets.

Rest of the difference is definitely because of different font and font settings..

---

### Post by sokre on 2007-02-08
Thanks!!!
look great!

---

### Post by sokre on 2007-02-08
Although it is only one part solved.
Do you see "Opens a new tab" button.
Notice how it is streched much more than in windows.
I am pleased with this solution, but if someone knows why is it so...

Thanks again!

---

### Post by Lster on 2007-02-08
I dunno... but I have a similar problem, that you may also have.

I have a widescreen (1280 x 800) screen for my laptop. On Windows, it uses the correct (native) resolution. Ubuntu, however, uses the 1024 x 768 resolution and the graphics card stretches it to fullscreen.

For me, I only have the vesa drivers, so, cant select a resolution of 1280 x 800. You may, however, be able to select your correct resolution and this may fix the problem.

Hope it helps,
Lster

---

### Post by gottria on 2007-02-08
Lster, do a search for your problem, try 915 patch. I had the same problem. You probley have the Intel 915 series graphics card.

---

### Post by Lster on 2007-02-08
Actually i have ATI x1400, but you are right... Ill search :).

---

### Post by MaX on 2007-02-08
> **Lster said:**
> Actually i have ATI x1400, but you are right... Ill search :).

Also check if cleartype or subpixelhint is turned on. That helps on LCD's.

---

### Post by elephant007 on 2007-03-18
let's see, radio buttons or using a big ole virus for an operating system...
yeah, I'll stick with the "ugly" radio buttons.
  Glad to know that someone was able to resolve the problem though...
btw, I'm never going back to a Microsoft OS.

---

