---
title: "diffrent usplash (kubuntu vs. ubuntu)"
date: 2006-09-15
forum: Desktop Environments
---

### Post by rackne on 2006-09-15
k so... i've installed kde just to see what's it like. didnt like it much so i got rid off it but i was really surprised to see that my ubuntu splash screen changed into kubuntu#-o i wanted to change it, did some research on google and got this:
sudo update-alternatives --config usplash-artwork.so
and this as well
sudo dpkg-reconfigure linux-image-`uname -r
the first commaned worked just fine however the second one gave an error that looked like this:
Package `linux-image-' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: linux-image- is not installed.

So, my question is how on earth change that kubuntu splash back into the default one?

---

### Post by Ramses de Norre on 2006-09-15
It should work when you have a kernel installed..
Copy this over EXACTLY: ```
sudo dpkg-reconfigure linux-image-`uname -r`
```

---

### Post by rackne on 2006-09-15
thanks a lot. i'll give it a go. :D

---

