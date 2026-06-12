---
title: "Mex files in octave"
date: 2008-08-22
forum: Education &amp; Science
---

### Post by janne_ph on 2008-08-22
Hi, 

I'm not that familiar with octave or for that instance ubuntu.

I've installed octave on Ubuntu 8.04, but the mex file support does not seem to be installed. If i just start octave 3.0.0 which is the version I get when i run "apt-get install ubuntu" and enter the command "mex" I just get an error message saying the following.

octave:1> mex
sh: /usr/bin/mkoctfile-3.0.0: not found
warning: unable to find mkoctfile in expected location: `/usr/bin/mkoctfile-3.0.0'
warning: mkoctfile exited with failure status

Why is this? The version I work with on my Redhat system at work works fine.

I dont want to compile octave from source, but if there is no other way I guess I have to.

Please help me with this problem. 

// Niklas

---

### Post by hubie on 2008-08-23
Did you install octave-forge?

---

### Post by janne_ph on 2008-08-23
No. How do I install that?

---

### Post by ad_267 on 2008-08-23
octave-forge isn't available in the 8.04 repositories for some reason. There's a bug filed about this but nothing has been done. It could be because the most recent octave is now 3.0.

You may be able to download the package you need from the ibex packages:
[http://packages.ubuntu.com/intrepid/math/](http://packages.ubuntu.com/intrepid/math/)

Or you might have to get it from the Octave website: [http://octave.sourceforge.net/packages.html](http://octave.sourceforge.net/packages.html)

---

### Post by janne_ph on 2008-08-24
Thanks for the answers. I've looked through the Octave-forge packages, but I cant find anything related to mex or oct file compilation.

Shouldn't the mex file compilation come with the standard octave installation?

Regards 

Niklas

---

### Post by ad_267 on 2008-08-24
Ok yeah I just tried on my octave and I get 
```
basename: missing operand
Try `basename --help' for more information.

```

so looks like it's working for me.

You need the octave3.0-headers package (assuming you have octave3.0)

---

### Post by janne_ph on 2008-08-24
Wonderful! Many thanks, that solved my problems.

---

