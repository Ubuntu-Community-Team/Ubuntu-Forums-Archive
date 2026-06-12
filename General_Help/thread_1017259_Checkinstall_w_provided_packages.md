---
title: "Checkinstall w/ provided packages?"
date: 2008-12-20
forum: General Help
---

### Post by macaholic on 2008-12-20
Greetings all,
Here is my predicament, I currently have some simple scripts that update various programs from their respected git repositories, builds them, and then installs them using checkinstall. Most of these prgrams are not a problem, wine, webkit, or compiz fusion for example. However, ffmpeg has been more quarrelsome. The problem being that when built and installed from the source, ffmpeg provides various libraries, i.e. libavformat, libswscale etc. Now the reason this is a problem is that aptitude does not like this one bit, since the dependencies are being resolved without a proper package installation, so it labels the packages as "broken". Here is the question I pose, as far as I can tell, this problem can be averted by having the ffmpeg package tell dpkg that it is "providing" the other packages that it is really providing, but i cannot figure out a way to do this. If anyone else would have any other suggestions, I would love to hear them.
Thanks for the help.

---

### Post by FakeOutdoorsman on 2008-12-21
I use the following:
```
sudo checkinstall --fstrans=no --install=yes --pkgname=ffmpeg --pkgversion "3:0.svn`date +%Y%m%d`-12ubuntu3"
```
This follows the Ubuntu naming conventions, but uses the current date.  Seems to make aptitude and other package managers happy (and keeps them griping about ffmpeg "updates" to the repo version), at least with my setup.  More info: [HOWTO: Compile the latest ffmpeg and x264 from source](http://ubuntuforums.org/showthread.php?t=786095)

---

### Post by macaholic on 2008-12-21
Hmm, I appreciate your help, and I am now using the proper naming conventions for ffmpeg as well as x264, however aptitude is still getting mad at me when I try to install things that require the ffmpeg libraries, i.e. libswscale, such as the following, ```
E: /var/cache/apt/archives/libavutil49_3%3a0.svn20080206-12ubuntu3_amd64.deb: trying to overwrite `/usr/lib/libavutil.so.49', which is also in package ffmpeg
```
The program in question, vlc, still works perfectly since the proper library files are all there and working, but aptitude labels them as broken, and thus this creates a whole slew of problems. So if anyone would have any further ideas for possible resolution on this issue, I would love to hear your thoughts. Thanks again.

---

### Post by FakeOutdoorsman on 2008-12-21
I'm slightly confused.  I understand that you've compiled and installed ffmpeg.  When you attempt to install vlc player from git, it causes aptitude to give the above error?

---

### Post by macaholic on 2008-12-22
Sorry I wasn't clear, it's when I try to install anything from the repositories that requires the ffmpeg library it gets mad, the programs still work, but it lists broken packages.

---

### Post by macaholic on 2008-12-27
Bump? Anyone?

---

### Post by macaholic on 2009-01-10
bumpp

---

