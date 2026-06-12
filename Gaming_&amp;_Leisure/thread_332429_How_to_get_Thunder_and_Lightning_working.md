---
title: "How to get Thunder and Lightning working"
date: 2007-01-06
forum: Gaming &amp; Leisure
---

### Post by j.miller565 on 2007-01-06
I've installed everything for it and it won't start, so can someone tell me how to get it working please

---

### Post by hikaricore on 2007-01-06
Really vague there, never heard of it.. is this a windows game running through wine or a native linux game?  Provide more info if you would like some help.  Error output from a terminal would be a good start.

---

### Post by j.miller565 on 2007-01-06
it's a native game and it's on the Ubuntu Native Gaming List in the arena. I'll try post the link to you as soon as the site is back up. oh yea he's the official site [http://tnlgame.net](http://tnlgame.net) but i can never get in

---

### Post by j.miller565 on 2007-01-10
I figured out how to install it now. btw here's the link to the Ubuntu gaming site on Thunder and Lightning. [http://doc.gwos.org/index.php/Thunder_%26_Lightning](http://doc.gwos.org/index.php/Thunder_%26_Lightning)

---

### Post by dr_psikick on 2007-02-10
> **j.miller565 said:**
> I figured out how to install it now. btw here's the link to the Ubuntu gaming site on Thunder and Lightning. [http://doc.gwos.org/index.php/Thunder_%26_Lightning](http://doc.gwos.org/index.php/Thunder_%26_Lightning)

Can you share how did you installed it? That would be great, thaks.

---

### Post by 16777216 on 2007-07-12
I too am having problems with this game 
I receive this error
```
Initializing SoundMan... OpenAL (ALC) Error 40961: ALC_INVALID_DEVICE
```

---

### Post by cogadh on 2007-07-13
Create a text file in your home directory called ".openalrc" (make sure you include the period). Put this single line in the file:
```
(define devices '(oss))
```
Save the file and launch the game, it should work fine now.

---

### Post by ChrisNZ on 2007-07-15
> **j.miller565 said:**
> I've installed everything for it and it won't start, so can someone tell me how to get it working please

I too have a similar problem. After installing the game and selecting it from the menu, the terminal; window appears breifly to see ... looking for bin/bin...? Then screen goes blank and system escapes from the current session and wants me to log back in!

Sorry that all i have. :(

TIA

ChrisNZ

---

### Post by Daveth on 2007-07-16
yes, it crashes with me too. The log file says it requires libalut.so.0 - there is a Red Hat rpm which one could Alien I guess, but it seems to come with a whole host of dependencies:

[http://rpmfind.net/linux/RPM/dag/redhat/el5/i386/freealut-1.1.0-1.el5.rf.i386.html](http://rpmfind.net/linux/RPM/dag/redhat/el5/i386/freealut-1.1.0-1.el5.rf.i386.html)

so I'm a bit loathe to do it. 

Anyone else had this problem and solved it, or know about these libraries?

---

### Post by cogadh on 2007-07-16
Don't do the RPM, install the libalut0 package:
```
sudo apt-get install libalut0
```
Almost forgot, its in the Universe repositories, you may need to enable them to get it.

---

### Post by Daveth on 2007-07-16
um, gives

Unpacking libalut0 (from .../libalut0_1.0.1-1_i386.deb) ...
Errors were encountered while processing:
 /var/cache/apt/archives/libopenal0a_1%3a0.0.8-3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

in terminal. Not sure what error code 1 is.

---

### Post by cogadh on 2007-07-16
Not sure on that one myself, it installed flawlessly for me.

---

### Post by Daveth on 2007-07-16
did you use their autopackage then, or compiled from source? The rpm conversion seems to throw up a host of lost dependencies- just removed that so file as it was killing off synaptic.

---

### Post by cogadh on 2007-07-16
I used the autopackage.

---

### Post by Daveth on 2007-07-16
OK, many thanks. I think I will uninstall and try the autopackage- but tomorrow, as time for bed here!

---

### Post by Daveth on 2007-07-19
Just to put this issue to bed, it installed fine with the provided autopackage, only providing the error reported earlier in the post and solved using the same fix. Just got to find out how to fly now!

---

