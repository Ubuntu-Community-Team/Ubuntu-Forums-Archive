---
title: "SDL games won't quit"
date: 2010-05-19
forum: Gaming &amp; Leisure
---

### Post by Sylos on 2010-05-19
Hello there. I have a (reasonably old) Fujitsu laptop running ubuntu Karmic and I have been having some trouble with SDL games such as Pingus. The games run fine but when it comes to ending the game the X wont get rid o the window, neither will Crtl + C. Not even the System Monitor "End Process" will get rid of the window.

I have looked through the forums and I know SDL has some issues on Karmic but  most of it seems to be sound related. I cant seem to find anything relating to this.

Any insights would be gratefully received.

---

### Post by achase79 on 2010-05-19
use top to list processes type "k" for the kill command and type "1" for the send.

---

### Post by Sylos on 2010-05-19
Thanks for the post. Using Ctrl K in the System Monitor worked to kill it.

Any ideas as to the reason for it hanging in the first place?

Many Thanks

---

### Post by del_diablo on 2010-05-19
> **achase79 said:**
> use top to list processes type "k" for the kill command and type "1" for the send.

Why on earth would you do that?
[URL="http://en.wikipedia.org/wiki/Htop_(Unix)"]```
htop
```[/URL]
[IMG]http://upload.wikimedia.org/wikipedia/commons/b/b1/Htop.png[/IMG]

Install htop and kill it.

---

### Post by Sylos on 2010-05-24
Thanks for the input on how to kill the process (obvoiusly that has been very useful) but the idea was to try and resolve why this is happening in the first place. 

Any ideas?

---

### Post by portets on 2010-05-24
for me, karmic was the same way. every single SDL application crashed and froze on exit. except for sometimes, usually after a reboot things worked for a few minutes.

i really, ***really ***recommend upgrading to ubuntu 10.04.

i haven't had a _single_ SDL issue since the upgrade. (actually, fresh install)

---

### Post by Sylos on 2010-05-25
Cheers man, I suppose thats the best way forward. I can do it on my laptop but on my desktop I spent ages fiddling around to get games like Unreal Tournament to work (i'd hate to go through that again!).

Thanks for the info....

---

