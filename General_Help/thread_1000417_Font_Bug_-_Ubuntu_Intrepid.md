---
title: "Font Bug - Ubuntu Intrepid"
date: 2008-12-02
forum: General Help
---

### Post by LepeKaname on 2008-12-02
[SOLVED] Hi everyone,

I installed Ubuntu Intrepid in my wife's computer. Everything runs smoothly except for some weird font problem. 

I'm posting 4 screenshots of the problem. It seems that has to be something related to the rendering. I tried with different configurations at  Appearance -> Fonts -> Rendering but it doesn't fix anything. However, when I select "Monochrome" many other texts also get really bad. You can see how, when I select "Best shape" (as well as the other options) the problem disappears. The opera, word (wine), firefox screenshots are with the "Best shape" selection. So, If someone of you have had this problem or know where I can search for more information (besides google...) I will really appreciate. 

Thank you.

P.S. I also tried with or with-out compiz, but nothing...

---

### Post by LepeKaname on 2008-12-02
Ok I found why it is happening... 

The problem of the blanked menus in opera was because of compiz, even I deactivate it. I had to disable it from the xorg.conf (Composite:Disabled) in order to show them correct. 

[http://ubuntuforums.org/showthread.php?t=977745](http://ubuntuforums.org/showthread.php?t=977745)

The other garbaged text was fixed changing the video driver from nvidia to vesa. Of course it is not what I want but at least I know now where to look at. 

I will post here if I find a solution.

Bye

---

### Post by LepeKaname on 2008-12-02
I followed this recommendations and finally my problem was fixed!! 
:):):):):):):):)

[http://www.nvnews.net/vbulletin/showthread.php?t=122695](http://www.nvnews.net/vbulletin/showthread.php?t=122695)

---

### Post by carloshiga on 2009-01-29
I followed the instructions in

[http://www.nvnews.net/vbulletin/showthread.php?t=122695](http://www.nvnews.net/vbulletin/showthread.php?t=122695)

and it fixed the problem for OpenOffice but my aMSN still have the problem. Any idea?

---

