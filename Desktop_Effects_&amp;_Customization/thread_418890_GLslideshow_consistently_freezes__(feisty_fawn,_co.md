---
title: "GLslideshow consistently freezes  (feisty fawn, compiz)"
date: 2007-04-22
forum: Desktop Effects &amp; Customization
---

### Post by jeremyrain on 2007-04-22
I'm only posting this because I am unable to even diagnose this problem since I can't get GLslideshow to give me any debug information and I'm hoping someone else is experiencing the same thing.

Upgrading to Feisty Fawn has been great. It took about 2-4 hours to undo some things that I had changed in 6.10 so that everything in FF would work properly, but it's been nothing if not stable and beautiful since then.

However...

Now that I've got a 3D accelerated desktop, I wanted to use GLslideshow as a screensaver. I managed to get it working and even using my image directories off one of my NTFS partition. 
Everything seemingly works, except... it crashes. the screensaver will show several pictures, behave normally, and then it will just freeze on a picture just before it was to fade out into the next picture. -debug does not work for me ( not quite sure why). Nothing else crashes, compiz works fine, just the screensaver crashes, and seemingly at random. Sometimes it crashes on the first picture, sometimes it will go for quite a while. any ideas?

---

### Post by Toadmund on 2007-04-29
Hmmm, I've been noticing that when I leave and come back I also have a frozen screensaver.
It's a new one for me. Mine is set to random.

ATI xpress 200.

Add that one to my WSOD or my Vertical Stripe Lines of Death problem.
What I would like to know is if the developers are looking into this freeze issue, seems quite common with Feisty.

---

### Post by SendDerek on 2007-08-26
I hadn't caught this thread before, but I would like to say that I have the exact same problem.  Would be nice if it worked!  It's my favorite screensaver!

---

### Post by SendDerek on 2007-10-14
I was hoping that this problem was taken care of in Gutsy with the new version of gnome and compiz and everything, but nope.  I reported it as a bug.  Here is the page:

[https://bugs.launchpad.net/ubuntu/+source/gnome-screensaver/+bug/152531](https://bugs.launchpad.net/ubuntu/+source/gnome-screensaver/+bug/152531)

If anybody has any suggestions, let me (let us) know please!

Thanks in advance.

---

### Post by allstar1971 on 2007-11-25
I have been having the same problem as well. I have found my screensaver freezes everytime no matter what I use. I was using the floating gnome feet and it froze. My fav is the slideshow as well.

---

### Post by rich.roadrunner on 2008-05-31
**Bump**

Doesn't seem like this problem has gone away. The thing is is worked fine on Ubuntu/Xubuntu Feisty (64bit), but on fresh install of Gutsy it freezes exactly as described above. Randomly freezes, sometimes soon, sometimes after many images. Not 100% sure but I think sometimes it's come back to life after a long long pause. Can nobody make any sense of this?

Can anyone tell us how to generate some useful debug info that we can post here as I can guarantee reproduction of this bug, from Launchpad it seemed like people were having difficulty reproducing this?


A bit of a fatal problem at this point, but otherwise this is one of my favourite aps on Linux and better than Google's Windows-only screensaver in it's flexibility: if anyone's interested I've strung some ugly little scripts together with zenity to select desired folder to show, and also one to scroll through a folder in order (point .xscreensaver to a symbolic link in an otherwise empty folder ...). Now all I need is that giant flat screen TV to link to and I'm happy.

---

