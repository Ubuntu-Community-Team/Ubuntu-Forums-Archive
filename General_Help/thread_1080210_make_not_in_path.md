---
title: "make not in path"
date: 2009-02-25
forum: General Help
---

### Post by 7raTEYdCql on 2009-02-25
I am trying to install qt from source.

I have the configure and when i run ./configure i get the error that make is not in your path.

---

### Post by 7raTEYdCql on 2009-02-25
Due to frustration i added '/' to path and i am still getting the same error. 

Any recommendations????

---

### Post by geirha on 2009-02-25
It probably means make is not installed (which it isn't by default). Install the package [build-essential](apt:build-essential) and make will be installed along with c and c++ compilers and a few other essentials for building software from source.

---

### Post by Joeb454 on 2009-02-25
I'd suggest removing / from your path. Mainly because there's nothing in / that can be run :)

And as suggested above, have you installed build-essential ```
sudo apt-get build-essential
```

You can also click the link in the above post to install it :)

---

### Post by 7raTEYdCql on 2009-02-25
build-essential is installed

root@mehrzad-laptop:/home/mehrzad/Downloads/qt-x11-opensource-src-4.4.3# apt-get install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
The following packages were automatically installed and are no longer required:
  libarts1c2a kdelibs4c2a gputils-doc gputils kdelibs-data liblualib50 libusb-dev libavahi-qt3-1 gputils-common lesstif2 liblua50
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@mehrzad-laptop:/home/mehrzad/Downloads/qt-x11-opensource-src-4.4.3# 



I still get the error.

---

### Post by 7raTEYdCql on 2009-02-25
Yes and i did realise the uselessness of /. I have removed it.

---

### Post by geirha on 2009-02-25
```

which make   # This should output /usr/bin/make
# If not, check that /usr/bin is in $PATH
echo $PATH 

```

---

### Post by 7raTEYdCql on 2009-02-25
mehrzad@mehrzad-laptop:~$ which make
/usr/bin/make
mehrzad@mehrzad-laptop:~$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/opt/real/RealPlayer
mehrzad@mehrzad-laptop:~$

---

### Post by ibuclaw on 2009-02-25
Could you post the output of ./configure in your next post, just incase you missed something in the output?

Regards
Iain

---

