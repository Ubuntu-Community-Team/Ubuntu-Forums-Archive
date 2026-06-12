---
title: "Tovid python dependency error"
date: 2006-02-25
forum: Desktop Environments
---

### Post by th3james on 2006-02-25
Hi

I am trying to install tovid from this repos:

deb [http://packages.kirya.net](http://packages.kirya.net) unstable main contrib non-free
deb-src [http://packages.kirya.net](http://packages.kirya.net) unstable main contrib non-free

but when i try to install them, it gives this dependency error:

The following packages have unmet dependencies:
  tovid: Depends: mencoder-586 but it is not going to be installed or
                  mencoder-k6 but it is not going to be installed or
                  mencoder
         Depends: normalize-audio but it is not going to be installed
         Depends: python (< 2.4) but 2.4.2-0ubuntu2 is to be installed

I believe this is because my version of python is too recent?
Is there anyway i can force this to install, and if so, will it work?

Thanks in advance
James

---

### Post by taurus on 2006-02-25
Or you can download the source at [http://tovid.sourceforge.net/](http://tovid.sourceforge.net/) and build it yourself...  Make sure you have installed build-essential first before you compile it,

sudo apt-get install build-essential

---

### Post by th3james on 2006-02-25
Ok, tried installing from source, but when i run ./setup.sh, it fails with this error:

Installing the python libararies...
running install
error: invalid Python installation: unable to open /usr/lib/python2.4/config/Mak efile (No such file or directory)
Could not install the python libraries!
Try "su -c './setup'"

---

### Post by az on 2006-02-25
[http://ubuntuforums.org/showpost.php?p=706750&postcount=14](http://ubuntuforums.org/showpost.php?p=706750&postcount=14)

---

### Post by tenjin1 on 2006-03-04
Had got this same error too. 

I did sudo apt-get install python-wxgtk2.4
then sudo apt-get install python-dev

and worked like magik!

---

### Post by siucdude on 2006-03-05
try downloading this program "devede"  look it up its new and easy.  

thanks

---

### Post by jtpratt on 2006-03-16
I had the same problem and I can confirm that the earlier post with this works:

I did sudo apt-get install python-wxgtk2.4
then sudo apt-get install python-dev

I also documented this and other video conversion items on my Ubuntu guide to converting video in linux page:
[http://smorgasbord.net/convert_video_linux]("http://smorgasbord.net/convert_video_linuxvv")

---

