---
title: "Speed of OO under windows and Ubuntu"
date: 2006-10-01
forum: Desktop Environments
---

### Post by davegahan on 2006-10-01
Openoffice seems terribly slow when I run Ubuntu. The same document, 85 pages, scrolls much, much faster under Openoffice in windows and does not cause me to wait for OO to catch its breath. A new dual core 2Ghz with 1GB RAM did not made any difference ! 

Should I go back to Windows ?

---

### Post by Crooksey on 2006-10-01
You probaly have a startup program on XP that loads the OO libaries, if you leave ir running for a while it should be fine.

---

### Post by ajgreeny on 2006-10-01
Just for interest, how long does it take for OOo to open on your machine?  I don't find it any different on ubuntu to windows on mine, a sempron 2400+ with 1Gb of ram.  On both OSs it takes 5 seconds to start from cold, and a little quicker if it's run before in the session.  The actual document opening of large multipage docs isn't something I have any real experience of, but some of the complicated ones I have are no quicker in windows than ubuntu.

You can put a launcher in your startup for the following application:-
ooffice -quickstart -nologo -nodefault
which will speed things up considerably at first start of OOo.

---

### Post by eeefresh on 2006-10-01
These tweaks helped me speed up OO considerably.

[http://openoffice.blogs.com/openoffice/2006/04/optimizing_open.html]("http://openoffice.blogs.com/openoffice/2006/04/optimizing_open.html")

---

### Post by brucevangeorge on 2006-10-01
Whenever I used OO it worked awesome for me. No hiccups.

Do you have the right kernel installed on your system? I see that you have a dualcore. Do you have the SMP kernel?


Also, what about running programs? Some of them could eat away at cycles and memory.





I used OO on an athlon 1800+ (1.5Ghz) and 512MB ram. Worked great for me. As quick as M$ Word if not better.

---

### Post by lawina on 2006-10-01
It takes me 5 secs to open OO in my P4 2.4GHZ 512MB laptop.
Isnt that normal?

---

### Post by lawina on 2006-10-01
However i also like to add, the delay depends on the type of the word doc you are trying to open.

---

### Post by davegahan on 2006-10-02
It is a .odt document of 65 pages, over 100 footnotes. The issue is not the startup time of OO, which I adressed, but the time the program eats CPU cycles reformatting and the very slow scrolling. The Windows version (There I uses 2.0.3 versus 2.0.2) is just much much faster in day to day usage.

---

