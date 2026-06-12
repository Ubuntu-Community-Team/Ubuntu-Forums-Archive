---
title: "C compiler?"
date: 2006-03-01
forum: Desktop Environments
---

### Post by harley on 2006-03-01
i was trying to install a new virsion of bison after i typed ./configure and it started to run it gave an error no acceptable C compiler found in $PATH am i running the wrong virsion? or do i need a C compiler?

---

### Post by Perfect Storm on 2006-03-01
Did you have install Basic Compilers?

```
sudo apt-get install build-essential
```

---

### Post by harley on 2006-03-01
ok now it run for a bit then a new error says GNU M4 1.4 is required.. how do i install this?

---

### Post by Perfect Storm on 2006-03-01
```
sudo apt-get install m4
```

---

### Post by harley on 2006-03-01
how do i fix a error that says termcap support not found?

---

### Post by Perfect Storm on 2006-03-01
Can you please post the terminal output.

---

### Post by harley on 2006-03-01
ok i got that error fixed but now i am getting this



root@hada:~# sudo apt-get install linux-source-2.6.12
Reading package lists... Done
Building dependency tree... Done
linux-source-2.6.12 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@hada:~# cd /home/harley
root@hada:/home/harley# ls
asterisk            bison    libpri                             zaptel
asterisk-perl-0.08  Desktop  quick_install_zaptel_asterisk.pdf
root@hada:/home/harley# cd zaptel
root@hada:/home/harley/zaptel# make
ZAPTELVERSION="1.2.4" build_tools/make_version_h > version.h.tmp
if cmp -s version.h.tmp version.h ; then echo; else \
        mv version.h.tmp version.h ; \
fi

rm -f version.h.tmp

You do not appear to have the sources for the 2.6.12-10-386 kernel installed.
make: *** [linux26] Error 1
root@hada:/home/harley/zaptel#

im trying to make zaptel it says i do not appear to have the sources for  the 2.6.12-10-386 kernel installed.

---

### Post by Perfect Storm on 2006-03-01
Do you have its headers and image installed? linux-headers-2.6.12-10-386 linux-image-2.6.12-10-386

---

### Post by harley on 2006-03-01
whats the code to install them?

---

### Post by harley on 2006-03-01
i got it :) thanks:)

---

