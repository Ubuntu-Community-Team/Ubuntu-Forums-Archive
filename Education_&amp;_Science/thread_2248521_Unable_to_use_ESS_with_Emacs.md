---
title: "Unable to use ESS with Emacs"
date: 2014-10-15
forum: Education &amp; Science
---

### Post by LYXDhE3 on 2014-10-15
Can someone please help me to get the ESS add-on to work with Emacs? I tried purging and re-installing both of them, but I still don't get those buttons in my Emacs  (R, S, and the run buttons, etc.). I only get a buffer named ESS that says this:
```

 [ess-site.el]: ess-customize-alist=nil 
[ess-site.el _2_]: ess-customize-alist=nil 
(S): ess-s-versions-create making M-x defuns for 
 
(R): ess-r-versions-create making M-x defuns for
```

I'm using version 24.
Thanks in advance.

---

### Post by cortman on 2014-10-15
I can only help you with installing emacs and the ESS addon. I have no familiarity with R or any related statistics language.
Emacs as you know can be installed correctly with

```
sudo apt-get install emacs
```

For installing ESS, I used the instructions on this page: [http://ess.r-project.org/Manual/ess.html#Installation](http://ess.r-project.org/Manual/ess.html#Installation)
I downloaded the current version tarball here: [http://ess.r-project.org/index.php?Section=download](http://ess.r-project.org/index.php?Section=download)
You can unpack it with Archive Manager.
I then followed steps 2,3, and 4 (in that order) from the installation help page. When the make and make install commands complete, be sure they completed without any errors. 
I was able to load ESS in Emacs with

```
M-x S
```

This was all done in a virtual machine running Linux Mint 16, and Emacs 24.3.1.

---

### Post by LYXDhE3 on 2014-10-20
Thanks for the reply. Do you know why I'm having problems already at step 2?
```
laur@snowflake:~$ cd /usr/share/ess
laur@snowflake:/usr/share/ess$ make
make: *** No targets specified and no makefile found.  Stop.
```

I'm using Ubuntu version 14.04, 46-bit. Emacs v. 24.3.1.
Cheers!

---

### Post by cortman on 2014-10-22
> **LYXDhE3 said:**
> Thanks for the reply. Do you know why I'm having problems already at step 2?
```
laur@snowflake:~$ cd /usr/share/ess
laur@snowflake:/usr/share/ess$ make
make: *** No targets specified and no makefile found.  Stop.
```

I'm using Ubuntu version 14.04, 46-bit. Emacs v. 24.3.1.
Cheers!

It looks like you're moving to the wrong directory. You want to unpack the tarball, then move to that directory, which is likely in your ~/Downloads folder.

```
cd ~/Downloads/ess-14.09
```

---

### Post by LYXDhE3 on 2014-11-04
It's not in my Downloads folder either. I have something called
[FONT=lucida console]Downloads/ess_13.09-1-1_all.deb[/FONT]
but I don't think that's it either. I tried
```
laur@snowflake:~/Downloads$ whereis ess
ess: /usr/share/ess

```
And still, it says no makefile found when I try that directory. Where else could it be?
I used [FONT=lucida console]sudo apt-get install ess  [/FONT]because I'm not really sure how to manually unpack a tarball. :confused:

---

### Post by LYXDhE3 on 2014-11-24
Well, it randomly started working now. :)

---

