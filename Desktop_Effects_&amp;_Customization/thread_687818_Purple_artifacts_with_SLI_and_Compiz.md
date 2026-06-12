---
title: "Purple artifacts with SLI and Compiz"
date: 2008-02-04
forum: Desktop Effects &amp; Customization
---

### Post by eznet on 2008-02-04
Hello again Ubuntu Forums,
So here I am again with a bit of a problem, though nothing major. 

When using Compiz with 2 nVidia 8200GT cards in SLI under Gutsy, I have artifacts rendered to screen when rotating the cube.  These artifacts come in the way of horizontal purple bars. Everything else with Compiz seems to work fine, but when I attempt the cube rotate or to bring up run (Alt+F2) I get odd purple lines on the screen.

I attempted to record the artifacts using GTKRecordMyDesktop, but the artifacts do no show up on the video or in screen shots – it is just as clean and perfect as can be.
Any ideas?

[IMG]http://farm3.static.flickr.com/2319/2243134168_4f80a970c0.jpg[/IMG]

-Matt

---

### Post by eznet on 2008-02-04
Wow.  Ok... So it was a quick fix... I changed “Option “SLI” “AFR”” to “Option “SLI” “SFR”” in my xorg.conf and everything looks fine... I swear I tried that without success, but it succeeded this time so I will take it :)

Thanks to all who helped :)

-Matt

---

