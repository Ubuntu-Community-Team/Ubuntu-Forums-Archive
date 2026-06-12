---
title: "help with fonts..."
date: 2006-07-03
forum: Desktop Environments
---

### Post by eradicator_006 on 2006-07-03
I really need some help with fonts.  I've followed every font guide I can find and my fonts look horrible.  I have all the ms ttf fonts installed and working fine.  I have tahoma installed from my xp machine and it works.  I set gnome to use tahoma for everything.  I set amsn to use tahoma.  I turned off anti-aliasing and disabled autohinting in /etc/fonts/local.conf.  The fonts in amsn look great.  The same fonts look awful in gnome and firefox.  I don't want to use anti aliasing because I can't stand the gray dots around the fonts edges.  They are way too noticable.  Any way, here is a screen shot of my gnome menu and the amsn menu.  

[IMG]http://www.hermies.net/fonts.jpg[/IMG]

I want everything to look like the amsn menu.  How do I achieve this?  I did turn off anti aliasing and hinting in gnome preferences too.  Here is my /etc/fonts/local.conf

<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
<match target="font">
<edit name="autohint" mode="assign">
<bool>false</bool>
</edit>
<edit name="antialias" mode="assign">
<bool>false</bool>
</edit>
</match>
</fontconfig>

---

