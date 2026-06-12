---
title: "KDE Fonts -- Looking Weak"
date: 2009-11-03
forum: Desktop Environments
---

### Post by HDave on 2009-11-03
Long time user of the Gnome desktop here.  With KDE 4.3's new ability to have different icons/wallpaper per desktop, I thought I'd give it a try.  So far I really like KDE, except that the font rendering is really awful.  I don't know if this is because I have both the KDE and Gnome desktop's installed.

I enabled anti-aliasing and bumped up the default font sizes, but still they look thin and weak and hard to read.  Does everyone on KDE use the DejaVu fonts or is there something better?  Or another setting I missed?

Thanks for any help, I'd love to stick with KDE, but as it is, it's giving me a headache (for real)....

---

### Post by mrboojive on 2009-11-03
There are some advanced settings for configuring the anti-aliasing, like subpixel rendering. Did you try those? If you go to System Settings > Appearance > Fonts and choose a specific DPI, then you can click "Configure" to tweak the settings.

Personally, I think the Liberation fonts look good on KDE:```
sudo apt-get install ttf-liberation
```

---

### Post by HDave on 2009-11-03
Thanks -- I found the liberation fonts nice too...though in Karmic I didn't need to install anything.

After a TON of playing around I found that I can get DejaVu to look semi-decent at 10pt size with anti-aliasing, RGB subpixel rendering, and "slight" hinting.

I say "semi-decent" because when I log out of KDE and log into Gnome, my brain just goes "aaahhhhhhhhh".   Which is too bad, because I am LOVING these plasma widgets, etc.

---

### Post by loose222 on 2010-08-10
Those same graphics display quite well in windows. I've  tested this. My post was not a knock on linux or codeweavers. Just real  life experiences. The review sounded alot more like a press release than  a real review. I use Mandrake, it has a great utility to set up a  scanner. I bought a scanner based on the fact the it was listed in the  utility. But when I went to install it a dialog came up that said this  scanner is not supported in mandrake linux. That pissed me off! The  mandrake site listed that scanner (curiously removed shortly after a  terse email from me), it's not working in any sane implementation! What  I'm trying to say here is I want a little more truth in advertising!                   

==============[U]
[orlando real estate](http://www.***********.com)
[Real Estate Forum](http://forum.propertysold.ca)

[/U][]("http://www.***********.com")

---

### Post by meijer.o on 2010-08-11
try this,

rename in /etc/fonts/conf.d (as root)

10-antialias.conf  
10-hinting.conf
10-hinting-slight.conf

to filename.conf to e.g filename.bak

for me fonts of kde apps in gnome, including google earth become much better after renaming these files. Let me know if it helps,

Otto Meijer

---

