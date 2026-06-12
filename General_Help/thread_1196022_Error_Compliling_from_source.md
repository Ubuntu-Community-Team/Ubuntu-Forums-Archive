---
title: "Error Compliling from source"
date: 2009-06-24
forum: General Help
---

### Post by pi.theta on 2009-06-24
I just tried installing GetEz, a GUI meant for wget on Ubuntu Jaunty. Its available only in source form so had no option other than follow the manual installation method by compiling.

First I ran ./autogen.sh as instructed in the readme. It completed whatever it had to do successfully

Then on running ./configure I got an error as follows:


```
checking for PACKAGE... configure: error: Package requirements (gtk+-2.0 >= 2.0.0) were not met:

No package 'gtk+-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables PACKAGE_CFLAGS
and PACKAGE_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```

Can anyone help me with what to do. I would be very grateful.

---

### Post by oldos2er on 2009-06-24
Look in the README or INSTALL files for a list of dependencies. If you can't find it there, sometimes you can find such a thing on the web site where you downloaded the source code.

 "No package 'gtk+-2.0' found" means you should look for a -dev package for gtk, my guess would be for libgtk2.0-dev. Try installing that and see if you get a little further.

 Here's some more info on compiling: [https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

---

### Post by nice_like_rice on 2009-06-24
oldos2er's right - 

[http://ubuntuforums.org/showthread.php?p=46719](http://ubuntuforums.org/showthread.php?p=46719)

it's libgtk2.0-dev

---

### Post by JacobSteelsmith on 2009-06-24
I think "sudo apt-get install libgtk2.0-0" at a command line should do it.

---

