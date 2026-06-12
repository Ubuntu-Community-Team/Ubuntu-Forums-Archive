---
title: "Jumpy and erratic cursor"
date: 2005-11-27
forum: Desktop Environments
---

### Post by oneTime on 2005-11-27
I'm running Ubuntu Breezy Badger 5.10 (GNOME) with kernel 2.6.12-10-386 on a Sony VAIO VGN-A190 laptop with an Intel Pentium M processor 1.70GHz using a touchpad. The cursor frequently jumps back on the same line or up and back to a any previous portion of the text, when typing in gedit and FireFox1.07. Even in a Terminal window. The cursor also frequently leaves whatever application I'm using. Most of the time I'm unable to type a simple search string in Google without having to retrieve the cursor!

I've had this problem with Ubuntu Hoary 5.04 (GNOME and KUBUNTU). I combed the web and found this thread posted on 2004-Nov-28:

[http://ubuntuforums.org/search.php?searchid=2689261](http://ubuntuforums.org/search.php?searchid=2689261)

Disabling powernowd and/or acpi with rcconf didn't help with 5.04. A fellow user thought it was a kernel bug. That a higher 2.6 kernel (as from 2.6.10) should solve it. So while with Hoary I downloaded and compiled kernel 2.6.13 from kernel.org. It didn't solve my problem. Another user pointed to frequency scaling. That it happens each time the processor changes frequency.

I'm confident it isn't a hardware problem because the cursor isn't erratic in this other comparatively inferior operating system that Sony (they dislike Linux users) forced me to take with the box. Here I am with an almost perfect installation that I cannot use because of an erratic cursor. 

My touchpad works just fine though I cannot scroll up and down with it. Breezy Badger 5.10(GNOME) supported my 1900x1200 screen (graphics by ATI mobility Radeon 9700) out of the box.

Did I miss any disturbing lines in my dmesg? 
Please,

[COLOR=Blue][COLOR=Black]$[/COLOR]  bzip2 -d dmesg.bz2[/COLOR]

the attachment if you'll like to take a look at my dmesg.

If you have a solution, please treat me like a newbie and thanks for your time!

OneTime in Bamenda(if you like to know).
_______________________________________________
Being new to Linux doesn't necessarily make you a newbie, especially if you've always been with Unix.

---

