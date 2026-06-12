---
title: "GTK1 font madness"
date: 2006-05-24
forum: Desktop Environments
---

### Post by rifter on 2006-05-24
I've been hitting the wall on this problem for awhile, and, well, it would seem that it's one of those Linux problems that are tiny enough they should be simple to fix but require digging into deep abstract theory just to figure out a cure.
I had noticed that whereas most GTK applications in Ubuntu have decent enough fonts, certain types of applications have incredibly nasty font rendering.  After awhile I figured out that this is because those were gtk1 applications.  I never had that problem with any other distribution.  The fonts might not have been pretty for some people but they were readable, whether I was dealing with a straight X11 application, GTK1 or GTK2.  
What happens, as demonstrated in the attached screenshot, is that any GTK1 application will show the fonts with improper spacing, such that the words are all mushed together.  I tried a number of solutions to this problem, including trying to use gtk-theme-switch to mess with the fonts.  gtk-theme-switch always shows the fonts just fine whether I use switch or switch2, but does not fix the problem.  It clearly has something to do with what fonts are available to/used by applications, but I haven't quite dug at how to properly fix that.
I tried the instructions in this howto: [http://ubuntuforums.org/showthread.php?t=20976](http://ubuntuforums.org/showthread.php?t=20976)
and they seemed to work in that once I did that the gtk1 apps had nicer fonts.  But the cure was worse than the disease because now firefox started crashing whenever it was asked to print something.  I probably did something wrong there... the thing is that I am pretty advanced at LInux anywhere else, but I never really delved into the font problem beyond making sure that fonts were in the right path.  Usually when I come across a HOWTO like the one above I try to figure out why the instructions do what they do and how to apply that knowledge, but this time it's too esoteric to get at first glance, and it's unclear where to go to get better information.  I have upgraded many of the things I used to use to gtk2 versions, but there's stuff that remains in gtk1-land, and regardless of this I would like to figure out this problem.
Any help would be appreciated.  If there's some documentation that will help, or something simple that can fix this, it woudl be great to have a clue here.  Of course this is one of those things maybe future releases could just have fixed ...
One of the things I like about Ubuntu is how much of the system "just works."  With every other distribution I have 5000 things to fix once they're installed and it takes weeks or months.  I know how to fix them or can figure it out, but that's kind of the problem.. the more time we spend fixing our computer the less time we spend using it.  That's one thing the Ubuntu people seem to understand, which is awesome.  Thanks for your time.

---

### Post by rifter on 2006-05-24
Didn't get the attachment right.. it was my first attempt at posting here...
Here it is.

---

### Post by rifter on 2006-05-24
One more thing.. I undid all the steps I did from the HOWTO, so the printing problem is fixed, but the font problem, of course, is back.

---

