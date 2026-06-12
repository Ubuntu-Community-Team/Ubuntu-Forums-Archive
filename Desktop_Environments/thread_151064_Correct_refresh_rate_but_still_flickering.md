---
title: "Correct refresh rate but still flickering"
date: 2006-03-27
forum: Desktop Environments
---

### Post by julian_II on 2006-03-27
I've searched the forums but not found any info. Being quite new to linux, it took me a while to figure out how to change the refresh rate for my 21" CRT. Apperently i had to edit xorg.conf. I tried different ways of doing this (scanranges, modlines), and finally succeeded in running Ubuntu at 1280x1024@85 Hz... I find it strange that something as basic as a proper refresh rate for a CRT-monitor is not supported out of the box, but wth. However, after changing the refresh rate, the image is still somewhat 'flickery', and that results in a headache after a while. I can't understand why this is the case, w2k runs at the same resolution and refresh rate, but no flickering! I've had this same problem with another monitor (a 19"), and an older version of Debian. I'd love to finally switch to linux, but not when it gives me headaches! Please help!

---

### Post by IYY on 2006-03-27
Looks like your HorizSync and VertRefresh aren't correct. Did you check what they should be in your monitor's manual, or settings (my Samsung monitor has a button that displays this information when clicked)?

---

### Post by julian_II on 2006-03-27
Thanks for the reply. Yes, i checked the online documentation for my monitor, i added those values to my xorg.conf. I might be doing something wrong in that respect tho, since i am quite new to linux. When i add values to that ,conf-file that i make up, X won't show up on my monitor because the values are out of range. Using the values specified by the manual of my Dell D1626HT monitor, does not solve the problem. The image is still flickering. Someone in a bar told me it could be a problem with my sync buffer or something, i'll try and look into that.

Edit: and does someone know how to stop firefox from going back and forwards through pages when i use the scroll-wheel, it's driving me nuts. I just want to use the scroll-wheel to scroll up and down a page.

---

