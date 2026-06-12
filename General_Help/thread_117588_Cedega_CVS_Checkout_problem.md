---
title: "Cedega: CVS Checkout problem"
date: 2006-01-15
forum: General Help
---

### Post by Deus- on 2006-01-15
I can't finish the installation of my CVS Cedega because after making a profile and trying to install it stops to the CVS Checkout part and aborts the whole thing :confused:
Here's the detailed description of the installation:

1) sh WineCVS.sh     to start the installation
2) Create the profile number 1, cvscedega_head
3) I run the existing profile
4) Then comes the last part:

WineCVS.sh - Progress(u) : Green is current

   0 = Uninstall
   1 = Cleanup
   2 = CVS checkout           <<-----------Stops here
   3 = Configure
   4 = Make depend
   5 = Make
   6 = Make install
   7 = Finish up

-------------------------------------------

Checking out CVS ... May take a while


    TIP: You can find an applications database on this page:
    appdb.winehq.com
    Copy by marking with mouse, and middle-click in browser.


What the heck is wrong with this? :cry:


I work as the root when doing this and have downloaded the WineCVS.sh to the /root folder

I've tried this trick without a result (I have gcc 3.4):
sudo unlink /usr/bin/gcc
sudo ln -sf /usr/bin/gcc-3.4 /usr/bin/gcc
(now do the compile of cedega)

Also I have tried this:
CC=gcc-3.4
export CC

---

### Post by slaykristian on 2008-06-07
I have the same problem!!!
Has anybody found the solution?
It can be a problem of CVS package? :confused:

Thanks in advance

---

