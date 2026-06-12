---
title: "Xorg Question - Refresh rate low in games but normal on desktop."
date: 2005-06-29
forum: Desktop Environments
---

### Post by smack on 2005-06-29
I've been trying to get my games to run with high refresh rates for some time. On the desktop(gnome) I can do 1600x1200@100Hz but when I start up some games(example: postal, tribes2) my refresh rate defaults to 60Hz. Postal runs at a native res of 1280x960 but I can set my tribes2 to any resolution. 

Here is my xorg.conf file.
[http://smack.gotdns.org/text/ubuntuforums/05-06-29/xorg.conf](http://smack.gotdns.org/text/ubuntuforums/05-06-29/xorg.conf)

and here is my xorg startup log.
[http://smack.gotdns.org/text/ubuntuforums/05-06-29/Xorg.0.log](http://smack.gotdns.org/text/ubuntuforums/05-06-29/Xorg.0.log)


I had to manually enter modelines in to my xorg.conf file to get 100Hz working on my desktop. In my screen section I had to set some of my modes to (example: "1600x1200_100.00" ) to get my comp to start up with that mode by default. There are a couple '_100.00' appended to some of my modes which I know I don't need but I was just experimenting.

I've read all through the man page for xorg.conf and done a ton of searching on the ubuntuforums. Any help would be much appreciated I got to play some games soon ](*,) !

*edit* I noticed that quake3 starts up fine at 100Hz. It might be something specific to postal and tribes2?

---

