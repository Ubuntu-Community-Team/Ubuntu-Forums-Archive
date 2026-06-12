---
title: "Firefox Hijacked by http://www.arizona.edu/"
date: 2006-01-03
forum: Desktop Environments
---

### Post by syklitengutt on 2006-01-03
when I open a link trough thunderbird or gaim or whatever I always open this page:
[http://www.arizona.edu/](http://www.arizona.edu/)

cant find a way to fix this...
Any ideas?

---

### Post by GrumpyBob on 2006-01-03
[QUOTE=syklitengutt]when I open a link trough thunderbird or gaim or whatever I always open this page:
[http://www.arizona.edu/](http://www.arizona.edu/)

cant find a way to fix this...
Any ideas?[/QUOTE]

I made a launcher for firefox, and it had this property.
I edited the start command to remove "%u", and it no longer does this, and just opens up the pages I defined.

Robert

---

### Post by JamesNorris on 2006-01-03
the % switch tells firefox to open a certain page, if you take a look at the command you're using to launch fx, you might find that it has a % switch, try entering whatever follows the % in the firefox location bar, it's likely that the arizona.edu page is the result of a google "I'm feeling lucky" search on the input from the % switch.

---

### Post by carlosqueso on 2006-01-03
Yup....that's what firefox brings up for "u" in the location bar.   One interesting one is that "s" brings up McDonalds.  Maybe if I get absurdly bored, I'll figure out the ABC's of firefox.

---

### Post by syklitengutt on 2006-01-03
ok... so now I removed the %u.
But now whenewer I open a link from gaim or thunderbird it just opens a new window and display the FF google page. 
The only google extension I have is Customize Google...

---

### Post by canadianwriterman on 2006-01-03
I had the same problem. Read through this thread. There's a link to the permanent solution:

[http://www.ubuntuforums.org/showthread.php?t=96414](http://www.ubuntuforums.org/showthread.php?t=96414)

---

### Post by syklitengutt on 2006-01-03
tnx...
this fixed it canadianwriterman!
tnx so much... it has been innoing me for weeks.

---

### Post by anil_robo on 2006-03-05
[quote=syklitengutt]when I open a link trough thunderbird or gaim or whatever I always open this page:
[http://www.arizona.edu/]("http://www.arizona.edu/")

cant find a way to fix this...
Any ideas?[/quote]

I got exactly the same problem since yesterday. I installed gdesklets and was launching Firefox from there. I had the firefox in my system menu already (like everyone else) so I right clicked on it, and selected "add to panel". Then from panel I dragged and dropped it on the gdesklets launcher bar. Thus the link was made "firefox %u". Since typing "u" in google and clicking "I'm feeling lucky" takes me to [www.arizona.edu](www.arizona.edu) - I was always landing up at that page.

And I kept cursing the maker of the theme I installed 3 days back!!! I have even sent him a message at his personal email!! Looks like it's time to undo a lot of damage!!! :(

**This is NOT humanity to others**!!! I urge Ubuntu developers to look into this matter PLEASE!

---

