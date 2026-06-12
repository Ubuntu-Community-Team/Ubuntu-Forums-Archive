---
title: "splash screen problem"
date: 2009-12-11
forum: Desktop Environments
---

### Post by colinireland on 2009-12-11
Hello,

I have a slight problem with my splash screen. I'm using 9.10 and tried to install some sort of fancy finger print scanner splash screen a while ago. Thought it would look cool. It didn't work. I was left with what I can only describe as what looks like an analogue TV test signal (just showing a range of colours, shapes etc. The monitors equivalent of a printers test page I suppose.) The small progress bar is shown at this point along with any disk checking info.

I would like to go back to just displaying text. I have downloaded StartUp-Manager. I have unchecked "Show Boot Splash" and checked "Show text during boot" but still no change.

The system is running fine otherwise.

If anyone can point me in the right direction it would be a great help

Cheers
Colin

---

### Post by avajesh on 2009-12-12
edit the menu.lst file in /boot/grub directory.
edit the menu item ending with words "quiet splash" ,delete the two words, append the word "verbose".

---

