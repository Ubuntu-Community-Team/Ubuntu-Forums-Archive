---
title: "xfig woes continue"
date: 2006-01-18
forum: Desktop Environments
---

### Post by hollowhead on 2006-01-18
Thanks everyone for the help with my previous post I copied the athena libs to /usr/lib and xfig loads.  However, xfig is unusble and hangs hopefully due to the following problem which is reported when it loads and if you try to import anything.  The message is;

"Either you have a very old app-defaults file installed (Fig),
or there is none installed at all.
You should install the correct version or you may lose some features.
This may be done with "make install" in the xfig source directory."

Also in the term I use to run xfig

"Warning: Missing charsets in String to FontSet conversion
Warning: Cannot convert string "-*-times-medium-r-normal--16-*-*-*-*-*-*-*,-*-*-medium-r-normal--16-*-*-*-*-*-*-*,*--16-*" to type FontSet
Warning: Missing charsets in String to FontSet conversion
Warning: Unable to load any usable fontset
Warning: Missing charsets in String to FontSet conversion
Warning: Cannot convert string "-*-times-medium-r-normal--16-*-*-*-*-*-*-*,-*-*-medium-r-normal--16-*-*-*-*-*-*-*,-*-*-*-r-*--16-*-*-*-*-*-*-*" to type FontSet
Warning: Missing charsets in String to FontSet conversion
Warning: Unable to load any usable fontset
Warning: Missing charsets in String to FontSet conversion
Warning: Cannot convert string "-*-times-bold-r-normal--16-*-*-*-*-*-*-*,-*-*-bold-r-normal--16-*-*-*-*-*-*-*,-*-*-*-r-*--16-*-*-*-*-*-*-*" to type FontSet
Warning: Missing charsets in String to FontSet conversion
Warning: Unable to load any usable fontset
Warning: Missing charsets in String to FontSet conversion
Warning: Unable to load any usable fontset"

I googled the first problem and know it involves moving the app-defaults file and setting up a symbolic link.  However, the setups are all slightly different from mine and the solutions given vary.  I was hoping someone has had this problem on breezy and can help.  Sorry its a long post. Ta in advance.

---

### Post by hollowhead on 2006-01-19
Solved it myself here as a complete reference for future forum users here is the answer.  Apologies -n my defence google threw up about 6 different ways of doing solving the problem. I started with the easiest first.

xfig won't load -copy athena widget libs into /usr/lib

error messages below copy "Fig" and "Fig-color" to
/usr/lib/X11/app-defaults).  This solves the programme hanging and the font error given below -all I have to do is work out how to use it!

As wider for general point can I make a request for "dapper drake" that stuff in the official repositories works out of the box.  A surprising anmount of stuff I've downloaded is incomplete and doesn't work fully ie openoffice help files weren't with distro and when downloaded have bits missing (internal links I think), KDars is the same -the help file is missing and the GCC version shipped has come up as an issue many times on this forum.  Just my 2cents worth of a moan but I think a valid point.

---

