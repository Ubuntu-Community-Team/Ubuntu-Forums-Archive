---
title: "Installing GMP"
date: 2006-09-10
forum: Desktop Environments
---

### Post by Hydrargyri on 2006-09-10
Hello! I'm trying to install GMP ([http://swox.com/gmp/](http://swox.com/gmp/)) and I'm having a little problem. Specifically...

"checking for suitable m4... configure: error: No usable m4 in $PATH or /usr/5bin (see config.log for reasons)."

That's the last line I get after typing in "./configure" when I'm in the gmp-4.2.1 directory. I checked the log, and its a whole lot of gibberish to me.

Could any of you kind folks give me a hint to install GMP?

Thanks! :)

---

### Post by hfriedrich on 2007-08-23
sudo apt-get install m4

---

### Post by co30cl on 2008-06-30
I'm having the same problem (No usable m4) when trying to configure (install) GMP.  If I try "sudo apt-get install m4" I get the error "Couldn't find package m4" and if I try "sudo aptitude install build-essential m4" I'm again told it couldn't find the package.  Help?

---

