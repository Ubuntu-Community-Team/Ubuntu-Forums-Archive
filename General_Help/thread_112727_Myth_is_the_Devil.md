---
title: "Myth is the Devil"
date: 2006-01-04
forum: General Help
---

### Post by Tal on 2006-01-04
ok. So I really love it, but it just hurts me sometimes.

I'm trying to get MythTv installed on BB with Firewire support. I'm using a 6200 STB, and as I've read, this should be easily done. The "apt-get install mythtv" packages that are installed as per the excellent how-to do not have firewire support built in. I tried downloading the source for .18.1 of Mythtv, but cannot figure out how to get the ./configure to show firewire support YES. I have all the 1394 packages installed from source so that they are the newest, etc.

I also tried installing SVN and pulling down the latest Myth packages from there. The ./configure works great, and I can set firewire support and other options easily. However, When I go to compile this, I get a ton of errors. Evidently the required packages aren't installed by default in Breezy.

I tried to install them as the errors came up, and apt-get'ed about a hundred million packages. I finally get stuck on one that appears to be xvmc related even though I've tried the ./configure with and without xvmc enabled. 

I'm going crazy here. Any thoughts on how I could get this running? Anyone have a precompiled version with FW enabled? Anyone have .19 compiled? What am I doing wrong? thanks in advance!  -Tal

---

### Post by zoiks on 2006-01-04
[I]"Evidently the required packages aren't installed by default in Breezy."
[/I]
Development packages no doubt.

*I tried to install them as the errors came up, and apt-get'ed about a hundred million packages. I finally get stuck on one that appears to be xvmc related even though I've tried the ./configure with and without xvmc enabled.*

*I'm going crazy here. Any thoughts on how I could get this running? Anyone have a precompiled version with FW enabled? Anyone have .19 compiled? What am I doing wrong? thanks in advance! -Tal*
  	
I may not be that helpful, but here are my humble opinions:

1) Compiling myth can be a real pain.  It needs a lot of stuff to work right, and it can be quite confusing.  Just wait till it's time to compile mythplugins!  Make sure you aren't using Qt4, as I'm pretty sure it needs Qt3.  Make sure the -dev versions of these packages are installed, and double-check that the versions you're using are compatible with myth 0.18.1.

2) The errors you're getting about xvmc might either be red herrings (errors from something else that only appear to be xvmc related) or a bug in the makefiles, or possibly an unmet dependency that another package has.  See if you can read the errors and find out if it's actually related to another package.

3) You might just have to do a make distclean or make clean before compiling, due to some confusion possible when there are errors and a lot of re-configuring.

4) By all means, post questions to the mythtv-users mailing list

[http://www.mythtv.org/mailman/listinfo/mythtv-users/](http://www.mythtv.org/mailman/listinfo/mythtv-users/)

It is a very active mailing list, with a lot of helpful people responding.  (Of course, put your ./configure line in there, along with version, and the relevant error messages.)

5) Try checking the buglists here:  [http://svn.mythtv.org/trac/](http://svn.mythtv.org/trac/)

FWIW, my configuration line for 0.18.1 looked like this

./configure --disable-distcc --disable-altivec --enable-lirc --enable-ivtv --enable-xv

I don't use anything related to xvmc or firewire, so..  I'm not brave enough to try 0.19 yet, which is a very major rewrite of the user interface code.  ;)


Edit: One more thing: you can check the mythtv-users archives at
[http://www.gossamer-threads.com/lists](http://www.gossamer-threads.com/lists)

---

### Post by Tal on 2006-01-05
I joined the MythTV list. I'm doing a plain ./configure with the .18.1 source, and tried --enable-firewire and a few other combos to no avail. I'll keep at it. This is sure frustrating.

---

### Post by zoiks on 2006-01-25
So, how did it work out with the firewire+myth stuff?

---

### Post by ashembers on 2006-02-20
I feel your pain Tal!

I have been working at capturing from my Scientific Atlanta SA3250 cable box. I can do it with Windows MCE drivers that happen to work on XP - the capture does work, AND I can even use an XP command line utility to tell the 3250 to change channels, so Lirc isn't even needed. How cool is that!?!?!? However, in Breezy, I cannot get anything but timeouts, blackscreens, and program hanging with Myth. 

My question is, at this point, how to I tell if Breezy is even aware that a firewire device exists or that the appropriate firewire modules are in fact loaded?

Thanks in advance!

---

### Post by xinix on 2006-02-20
Try the debs in Christian Marillat's repository (go here to get the locations [http://debian.video.free.fr/](http://debian.video.free.fr/) ).  I managed to totally F* my system yesterday. With the help of these packages I was running mythtv 0.19 in about 3 hours after formating my root partition (trust me it was the easiest way to fix things).   These packages require you to install versions of some stuff in the Dapper repository.  Try to use as many as possible from breezy fist.  After my own personal experiences while messing with Dapper packages. I'm only sticking to the few I needed to get mythtv installed.   I noticed that the 1394 packages were amongst the dependencies. So, I'm going to guess that it's built into the mythtv install.  One thing about these packages is that you need to create a directory called mythtv in /etc ( ie /etc/mythtv).  For some reason it doesn't create the directory but tries to put a file in it and fails.

---

