---
title: "firefox crashing and unstable"
date: 2005-12-20
forum: General Help
---

### Post by funkymonkey on 2005-12-20
Firefox crashes unexpectedly in Ubuntu.  It doesn't seem to be correlated to a particular website (i.e. it's not repeatable just by going to website X) nor an interval of time.  Occasionally, the program will crash before it even loads, in between me clicking on the icon and the window actually appearing.  I've searched these forums and tried several of the fixes, but the problem keeps coming back.

I'm on a Sony Vaio FS660.  The networking components seem to work fine, which is actually the reason I had ubuntu recommended to me.  I was having a problem like this under my old Windows 2000 install, where programs would simply close themselves.

I'm under a tight time constraint, so this has gotten very frustrating very quickly.  Any help is appreciated! :)

---

### Post by Rackerz on 2005-12-20
Ok, go into the Terminal and type 'firefox' when it crashes you should usually see something in the console, that something is the errors. Paste them here.

---

### Post by aysiu on 2005-12-20
You may have a corrupt profile. Try this:
[http://www.ubuntuforums.org/showthread.php?t=103930](http://www.ubuntuforums.org/showthread.php?t=103930)

---

### Post by Sebby on 2005-12-20
Is it Firefox 1.5? If so, I was experiencing the same problems, and found that it was one of the plugins (haven't put my finger on which one yet). I've cured it by backing up bookmarks then just deleting the .mozilla folder from my home directory, giving me a clean start.

---

### Post by funkymonkey on 2005-12-21
After I posted last night, Firefox worked fine all evening.  When I got up this morning I was able to cause some problems.  First it crashed while trying to load a plugin to play mpeg files (I haven't installed any additional decoders), and then it started with the usual trouble.  Here's one of the messages from the console:

funkymonkey@ubuntu:~$ firefox
*** glibc detected *** corrupted double-linked list: 0x085f4110 ***
Killed

I immediately typed "firefox" into the console to get it back, and I got this:

funkymonkey@ubuntu:~$ firefox
Segmentation fault

in between this I got a weird bug that happens occasionally when all the desktop windows go blank or get a weird zig-zag pattern, and can only be fixed by switching resolutions, but that's for another post :)

Thanks!

edit: it just gave me another segmentation fault as I tried to post this; luckily it went through *whew*

---

