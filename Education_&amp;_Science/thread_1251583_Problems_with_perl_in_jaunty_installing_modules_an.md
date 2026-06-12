---
title: "Problems with perl in jaunty: installing modules and x device."
date: 2009-08-27
forum: Education &amp; Science
---

### Post by rene8 on 2009-08-27
Hi;

I have a problem installing perl modules. I'm kind of new with perl, but things have not been nice between Ubuntu and Perl since de beginning.

Since many useful modules are not in the ubuntu repositories (any of them), I'm using cpan.

Nevertheless, modules refuse to be installed. It happend at first with PDL::GSL::CDF; then, just to test, I tried installing PGPLOT - it happened again.

The error message is simply 'NOT OK', or 'will not install'.

I've checked the dependencies, and I have the required dependencies for both.

I also tried building a debian package for the modules (using dh-make-perl) and then installing it, but it encounters the same errors. When trying to use the option '--notest' (as suggested in a Debian forum thread about perl, [-here-]("http://www.debian-administration.org/articles/78") ) it still performs the tests and says exactly one of the two previous error messages.

This is not the first problem I have found with perl in Ubuntu... for example, my X devices in perl don't work properly: xwin simply says 'Can't load device' (when it actually worked well in the very first perl script I ever made, but never worked again), and xcairo makes 'ghost' plots - when trying to plot anything using xcairo, it opens the device and draws the box, but plots nothing; if plotting in several subpages, it does this with only one subpage... this is not a script problem since changing the device (to, say, a ps device), it plots everything perfectly.

I'm starting to think that perl doesn't like Ubuntu... or the other way around :S.

I'll appreciate a lot if anyone can help.
Than you very much in advance.

---

### Post by unutbu on 2009-08-28
Did you install build-essential *before* installing modules using CPAN? See [http://ubuntuforums.org/showthread.php?t=240923&page=2](http://ubuntuforums.org/showthread.php?t=240923&page=2) and in particular, [http://ubuntuforums.org/showpost.php?p=4741806&postcount=15](http://ubuntuforums.org/showpost.php?p=4741806&postcount=15)

---

### Post by rene8 on 2009-08-28
Oh, wow; this actually worked!

I DID have build-essential installed prior to cpan, but it turned out there were some libs that build-essential uses that were not upgraded. This was the whole trouble.

I also had to remove the whole .cpan directory, and re-configure cpan (does it ok automatically ;) ), but after that, (and using root privileges) I was able to install the deared module.

I REALLY searched the forum for information about this, and the thread you pointed me to never showed! How come you found this apparently so easyly?

Thank you VERY much!!

---

### Post by unutbu on 2009-08-28
At first, I too had trouble using CPAN with Ubuntu. Fortunately for me, this thread happened to be active on the forum at around the same time. 

I'm glad it worked for you.

---

### Post by rene8 on 2009-08-28
Ah ok!
Yes, thak you!

I'm still worried about the X device not working properly. But I don't know if that is really a problem between perl and my system or with my graphics card, since it is an ATI and it does have unresolved graphical issues (even with the propietary driver).

If anyone knows a about X, some help on this matter would be nice too ;).

---

### Post by unutbu on 2009-08-28
You may want to post a question in the Programming Talk subforum: [http://ubuntuforums.org/forumdisplay.php?f=39](http://ubuntuforums.org/forumdisplay.php?f=39)

It could help also if you can post simple example code that exhibits the problem.

---

### Post by rene8 on 2009-08-28
Never mind... I found the problem with the xwin device. It was so simple that I don't know why I never thought of it before.

It simply was that I was specifiying a filename (as for other devices, such as ps) also when using xwin, and that prevented xwin from loading itself.

The problem with xcairo remains, but having xwin working, it becomes a minor issue.

Thank you!

---

