---
title: "openttd installation"
date: 2005-07-03
forum: Gaming &amp; Leisure
---

### Post by yccheok on 2005-07-03
does anyone noe where i can use synaptic package manager to get a openttd - an open source transport tycoon deluxe? 

i try to get the debian file from the openttd homepage, however, i get the following error while trying to perform the installation:

yccheok@ubuntu:~/Downloads$ sudo dpkg -i openttd_0.4.0.1-2_i386.deb
Selecting previously deselected package openttd.
(Reading database ... 67543 files and directories currently installed.)
Unpacking openttd (from openttd_0.4.0.1-2_i386.deb) ...
dpkg: dependency problems prevent configuration of openttd:
 openttd depends on libc6 (>= 2.3.2.ds1-21); however:
  Version of libc6 on system is 2.3.2.ds1-20ubuntu13.
dpkg: error processing openttd (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 openttd

any suggestion?

thanks

cheok

---

### Post by bjorne on 2005-11-06
Hi!
My first post here, and I use it to bring up a really old thread... Sorry for that :( 

But I wanted to say that OpenTTD works great under Breezy, and I hope there is more TTD-crazy Ubuntuusers than me out there?

Here are some links that may be useful if you want to get OpenTTD working:

Latest .deb package from [http://sourceforge.net/projects/openttd/](http://sourceforge.net/projects/openttd/)
[http://prdownloads.sourceforge.net/openttd/openttd_0.4.0.1-2_i386.deb?download](http://prdownloads.sourceforge.net/openttd/openttd_0.4.0.1-2_i386.deb?download)
Install with ```
dpkg -i openttd_0.4.0.1-2_i386.deb
```

Original TTD for DOS/Windows from 
[http://download.transporttycoon.net](http://download.transporttycoon.net) 
I used the DOS version, smaller DL ;)

Info regarding what files you need to copy from the original game
[http://wiki.openttd.com/index.php/Compiling_on_Linux](http://wiki.openttd.com/index.php/Compiling_on_Linux)

The info from the last link wasn't correct in my case, maybe I did something strange?
The files where named TRGC.GRF insted of trgcr.grf, TRGH.GRF insted of trghr.grf, and so on.
And they were supposed to be copied to /usr/share/games/openttd/data/, nothing else.
And all names shold be in lower case! I didn't change the names to end with an r, the worked fine anyway.

Now it's time to enjoy! :p 

```
/usr/games/openttd
```

Happy gaming, all nostalgic tycoons!

//Bjorne
(Sorry for the bad english, not used to write it, only reading :D )

---

### Post by NiceGuy on 2006-01-07
Fantastic, I'd forgotten about that game! Thanks a lot for the how-to. :grin:

ps. I downloaded the 'windows version' and the files listed at [http://wiki.openttd.com/index.php/Compiling_on_Linux]("http://wiki.openttd.com/index.php/Compiling_on_Linux") were the correct ones for me.

---

