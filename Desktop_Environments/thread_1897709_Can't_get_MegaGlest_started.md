---
title: "Can't get MegaGlest started"
date: 2011-12-19
forum: Desktop Environments
---

### Post by aarsalankhalid on 2011-12-19
Hey

Previously I was using ubuntu 11.04 on which I had installed megaglest. And everything was running smoothly. 
And now, a couple of weeks ago I did a clean installation of 11.10 and when I try running megaglest from terminal, it gives me the following error: 
```

./megaglest: error while loading shared libraries: libopenal.so.0: cannot open shared object file: No such file or directory

```
Now I did a check and in /usr/lib, there is such a file/directory. 

What do I have to do in this regard? 
I tried searching forums for a solution, and all I understand is that some symbolic link is missing probably. but those were for 64 bit and I am using 32 bit.

Best

---

### Post by tomreyn on 2012-11-04
Hi aarsalankhalid,

I'm a bit ;-) late to reply, but I guess it can still help you and others.

It's a while ago, but I think this issue was fixed or worked around  in a newer MegaGlest release. The latest stable release, 3.6.0.3, is  available since January this year so shortly after oyu posted. Please  give it a try, and if it still does not work for you please also try the latest 3.7.0 beta (or stable, if it is available by then) release.

If you're using the Ubuntu package and problems persist, please file a bug report at
[https://bugs.launchpad.net/ubuntu/+s...glest/+filebug]("https://bugs.launchpad.net/ubuntu/+source/megaglest/+filebug")

You may also try to use the upstream installer (non-packaged, installs   into your home directory) or install manually from archive files, both these variants are available at [http://megaglest.org](http://megaglest.org)

Hope this helps,

Tom

---

