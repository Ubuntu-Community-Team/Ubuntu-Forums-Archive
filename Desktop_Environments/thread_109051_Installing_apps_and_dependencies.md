---
title: "Installing apps and dependencies"
date: 2005-12-27
forum: Desktop Environments
---

### Post by willy-i-am on 2005-12-27
Hello all, I use gentoo, but I have my family hooked up with Breezy, and we're all generally happy that way.  However I have never used the apt-get package management system before and am wondering about a few things.

First, How do you install certain programs without suppoort for other given programs?

For example I found [this]("http://http://forums.gentoo.org/viewtopic-t-396150-highlight-ipod+video.html") script (4th post down) on the gentoo forums.  Its suppose to convert videos for use with the fifth generation ipods.  If you read the script, it uses the command 'mp4creator' near the bottom.  For what I have researched, to get the mp4creator command, i need to install mpeg4ip, which sadly can not be installed with apt-get (if it can be, please let me know).  

Alas, it must be installed the old fashioned way with make install and such.  Now when I ./bootstrap it it gives this errror:

> Error - we have detected a version of faac that has libmp4v2 support and no copy of mpeg4ip-config. This means faac was built with faad2 and the libraries will be incompatible.

So the big questions are: 
A. How do i install faac without mp4v2 support
B. Or can this mp4creator comman be attaind some other way

Thanks in advance for any help
-Willy

---

