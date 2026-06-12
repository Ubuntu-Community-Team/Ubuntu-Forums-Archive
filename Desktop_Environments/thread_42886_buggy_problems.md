---
title: "buggy problems"
date: 2005-06-19
forum: Desktop Environments
---

### Post by mr.me on 2005-06-19
Hi I have been having some problems with ubuntu 5.04(gnome):

1.firefox and epiphany web browsers both freeze well loading pages and some times just quit,It doesent happen all the time just anuff to be really anoying.

2.I cant look at the properties of some file formats(ogg,mp3,and maybe more)the folder or desktop just freezes,if its in a folder I can just hit the exit button,and the "program did not respond"window will popup and I hit ok and everything will unfreeze,if its on the desktop,I have to reset.

Im useing a athlon 2800 xp processor with 512mb of ram,ATI 9800pro 128mb graphics card,and a 200gb hardrive...and some other specs Im too lazy to type :grin: ,I did recently install ATI drivers,and compleatly update averything on ubuntu,and install a bunch of programes and libs,do any of you guys no what couuld be wrong?

thanks

---

### Post by Knome_fan on 2005-06-20
Hi,

1. That's a tough one to say something about if you don't have more information. Do they have problems with certain sites, do they have problems with sites using for example flash?
Also, did you try running them from a terminal, so you might get some output about what is wrong?

2. This is a known problem.
[https://bugzilla.ubuntu.com/show_bug.cgi?id=8076](https://bugzilla.ubuntu.com/show_bug.cgi?id=8076)
[http://www.ubuntuforums.org/showthread.php?t=37553&highlight=nautilus+xine](http://www.ubuntuforums.org/showthread.php?t=37553&highlight=nautilus+xine)

I think your best option would be to temporarily install totem-gstreamer again, do the changes you want to do and then go back to totem-xine.
And instead of resetting your machine, try to change to a console (Ctrl+Alt+F1), log in and kill nautilus from there. (killall nautilus should do the trick)

---

### Post by mr.me on 2005-06-20
^^^^uninstalling totem-xine fixed the problem...thank you very much \\:D/  :grin: .

And about the web browser question,I dont know It might be a flash problem,I never have any problems using "google",but sites like "torrent spy" and "how stuff works" have lots of bugs(the bugs I listed in my first post),you said somthing about running from terminal...how do you do that,I know that must be a stupid noob question...but hey Im a noob :grin: .

thanks

---

### Post by mr.me on 2005-06-20
never mind,I switched my flash libs/plugins,and every thing works fine now...I think

---

