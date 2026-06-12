---
title: "Gnome/XFCE vs. KDE fonts"
date: 2005-06-04
forum: Desktop Environments
---

### Post by skoal on 2005-06-04
Howdy,

I just installed KDE and it's slicker than a used car salesman.  I'm pretty damn impressed to say the least.  The only thing which irritates me in KDE is the seeming lack of control over AA/hinting that Gnome and XFCE offers.  I have some screenies posted below to demonstrate.

* I do not use AA, neither in Gnome or XFCE.

1. How do I use hinting in KDE?

I uncheck the "Use anti-aliasing for fonts" (AA) setting in Control Center > Appearance & Themes > Fonts, but when I do, I can no longer use the "configure" button right next to it which has the hinting options I need.

2. Is there something I need to change in my /etc/fonts/local.conf file so that KDE can gimme back control?

Here's the relevant snippage from mine:
> <match target="font">
    <edit name="autohint" mode="assign">
      <bool>false</bool>
    </edit>
  </match>
[...]
<match target="pattern">
                <edit name="dpi" mode="assign"><double>96</double></edit>
</match>

With those settings, Gnome/XFCE fonts look the same.  What does KDE need to give me control over my fonts like those 2 do?

thanks.

---

### Post by brent on 2005-06-05
> I uncheck the "Use anti-aliasing for fonts" (AA) setting in Control Center > Appearance & Themes > Fonts, but when I do, I can no longer use the "configure" button right next to it which has the hinting options I need. I think anti-aliasing for fonts and sub-pixel hinting are the same thing. I think it also goes by the name of ClearType in Windows and sub-pixel rendering in Mac. It all does the same thing.

> 2. Is there something I need to change in my /etc/fonts/local.conf file so that KDE can gimme back control? 
This is KDE. We don't edit text files in KDE!  :grin: Just enable anti-aliasing and select your hinting.

---

### Post by skoal on 2005-06-05
Thanks for the info Brent.  AA really is an eye burner for me and I only use hinting.  It's strange but it seems like some of the fonts get crisper with a different color of background.  That led me to believe I had some weird funky transparency bleeding through but I checked all those options and it was all off by default (since I never touched em to begin with).  I'll have to filly dally around with it some more...

---

