---
title: "can't change font rendering to Subpixel smoothing"
date: 2009-07-29
forum: Desktop Environments
---

### Post by kaiwan on 2009-07-29
Hi! 

I have ubuntu jaunty, and I installed Kde 4.3 rc2. After that my fonts went ugly, like skinny. 

I tried to change qt3 and qt4 setting, but no change, I removed every KDE package and rested Gnome to factory settings and nothing.

I trided to change Font Rendering to Subpixel smoothing -> Full in gnome-appearance-properties but I can not. I am attaching the picture:
[http://ubuntuforums.org/attachment.php?attachmentid=122823&stc=1&d=1248876467]("http://ubuntuforums.org/attachment.php?attachmentid=122823&stc=1&d=1248876467")

What can I do to make my fonts nice as before?

---

### Post by kaiwan on 2009-07-29
Fixed it like this:

[HTML]<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
  <match target="font">
    <edit name="autohint" mode="assign">
      <bool>true</bool>
    </edit>
  </match>
</fontconfig>[/HTML]

Copy and paste the text above into a text file, and save it in your home directory as .fonts.conf (note the first period, this file will be hidden). Log out for the changes to take effect. 

Reference: [http://tombuntu.com/index.php/2008/10/15/tweak-your-font-rendering-for-better-appearance/]("http://tombuntu.com/index.php/2008/10/15/tweak-your-font-rendering-for-better-appearance/")

---

