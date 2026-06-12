---
title: "Frets on Fire is way to slow!!"
date: 2008-04-08
forum: Gaming &amp; Leisure
---

### Post by dragonblade on 2008-04-08
I downloaded it from add/remove programs.
Why i it so slow?

---

### Post by dragonblade on 2008-04-08
bump

---

### Post by AnRa on 2008-04-08
Try using the one from the official site, it works as it should. ;)

---

### Post by Crafty Kisses on 2008-04-08
> **dragonblade said:**
> I downloaded it from add/remove programs.
Why i it so slow?

What are your system specs?

---

### Post by Ozor Mox on 2008-04-09
It runs far too slow on my computer too. I've tried the version in Synaptic, and the one off the website. It's slightly faster with proper ATI drivers installed for my card, but still not really playable.

---

### Post by christooss on 2008-06-11
I found that most problems can be solved with reducing graphic goodies in games such as audience and disablin AA.

I found out that Dual Core machines are bad for running FoF.

---

### Post by DoktorSeven on 2008-06-12
Get 1.2.451 from [the Sourceforge page](http://sourceforge.net/project/showfiles.php?group_id=182199); new version and the one in the repos are a bit slow.  Some of the graphic mods might help a bit as well (check some FoF fan sites for some) as they can be lighter and make things faster.

---

### Post by doorknob60 on 2008-06-12
The version from the repositories is slow because it's compiled without cxfreeze, because cxfreeze isn't in the repositories. The binary from the site is compiled with cxfreeze, and it goes a *lot* faster. I'm not sure why this hasn't been fixed though...

---

### Post by diwas on 2008-06-17
I cannot even start the game...wat is the problem? Is it my graphics card?

---

### Post by fif on 2008-06-17
Same problem here. I used to run version 1.2.451 under 7.10. I upgraded to 8.04 and installed the catalyst drivers for my ATI 9600 pro and it is now way way too slow.
May be comes from the ATI drivers (changed from fglrx to catalyst).
Need to check further.

---

### Post by fif on 2008-06-17
By the way compiz is off and I have the same slow behavior with the latest version downloaded from the official FoF website.

---

### Post by DoktorSeven on 2008-06-17
> **fif said:**
> By the way compiz is off and I have the same slow behavior with the latest version downloaded from the official FoF website.

Make sure your graphics drivers are up and working (run **glxinfo | grep direct** from a terminal, you should get "direct rendering: Yes").  Also, the *latest* version from their site is a bit slow as well, go to the link I gave above ([http://sourceforge.net/project/showfiles.php?group_id=182199](http://sourceforge.net/project/showfiles.php?group_id=182199)) and download the PREVIOUS version.  That one works the best for me.  And play with the settings and plugins as well, there are some that will reduce the graphics intensity and speed things up.

---

### Post by fif on 2008-06-20
Thanks very much for the hint.
I tried to have direct rendering working with the catalyst drivers but I have not been successful. Finally I removed the ATI drivers with Envy and got direct rendering to work with Mesa drivers, what fixed my slowness issue.
I do not intend to go any deeper in the Catalyst use for the current time being.
Now is rock time again! :guitar:

Thanks again.

---

