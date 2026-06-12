---
title: "Request: Asterisk 1.2"
date: 2005-11-18
forum: Closed Requests
---

### Post by hagen00 on 2005-11-18
Asterisk 1.2 was released on 17-11-2005.

Any chance this could be added to the backports?

[http://www.asterisk.org/]("http://www.asterisk.org/")

---

### Post by langals on 2005-11-21
Hi

I would also very much like Asterisk 1.2 to be added to the repository.

langals

---

### Post by jdong on 2005-11-21
asterisk | 1:1.2.0.dfsg-3 |      unstable | source, i386
  asterisk | 1:1.0.9.dfsg-1 |        breezy | source, i386
  asterisk | 1:1.2.0.dfsg-3 |        dapper | source, i386


Approved :)

---

### Post by jdong on 2005-11-21
Build failure, unmeetable dependencies.

---

### Post by langals on 2005-11-22
Hi jdong

Would it be possible to elaborate a bit on what the problem is with 1.2.0 on Ubuntu. Is it not possible to build 1.2.0 for Ubuntu? If not, then is it possible to install it from source?

Many thanks

langals

---

### Post by hagen00 on 2005-11-22
Hi Jdong

I'm also having problems with installing Asterisk 1.2. I'm running Hoary but it seems that even Breezy does not meet all the dependencies needed for Asterisk 1.2. Is it at all possible to install Asterisk 1.2 (from source or the .deb package from debian) on Ubuntu?

It is critical that i get this installed and am considering moving to Debian Sarge, where i believe it is possible to install Asterisk 1.2. I really like Ubuntu, but will I have to move to Debian now?

Thanks

hagen

---

### Post by jdong on 2005-11-22
[QUOTE=langals]Hi jdong

Would it be possible to elaborate a bit on what the problem is with 1.2.0 on Ubuntu. Is it not possible to build 1.2.0 for Ubuntu? If not, then is it possible to install it from source?

Many thanks

langals[/QUOTE]
If you're really desperate, I guess you can use ubp-build.py to build this and its dependencies from source...

---

### Post by andrius on 2005-11-30
Wen it is going to happen? What conditions it need to fulfil?

---

### Post by jdong on 2005-11-30
jdong@shuttle:~$ sudo apt-get build-dep -sV asterisk
Reading package lists... Done
Building dependency tree... Done
E: Build-Depends dependency for asterisk cannot be satisfied because no available versions of package libpri-dev can satisfy version requirements


---

As of now, no build is possible.

---

### Post by andrius on 2005-11-30
[QUOTE=jdong]jdong@shuttle:~$ sudo apt-get build-dep -sV asterisk
Reading package lists... Done
Building dependency tree... Done
E: Build-Depends dependency for asterisk cannot be satisfied because no available versions of package libpri-dev can satisfy version requirements


---

As of now, no build is possible.[/QUOTE]

should we ask to backport libpri-dev as well? :)

---

### Post by jdong on 2005-11-30
Libraries may not be backported unless they are not present in the current stable version in the first place (i.e. if they added a new libsomething package to Dapper)

---

### Post by andrius on 2005-11-30
[QUOTE=jdong]Libraries may not be backported unless they are not present in the current stable version in the first place (i.e. if they added a new libsomething package to Dapper)[/QUOTE]

Many thanks for your answers, and sorry, but still, can we do something about that or we will not have asterisk 1.2 in breezy system and will need to wait another half year?

---

### Post by jdong on 2005-11-30
We will not have it in official Backports... With ubp-build.py, you can probably work around it and make asterisk packages for yourself to some level of usability.

---

### Post by andrius on 2005-12-02
I installed asterisk on breezy from dapper and no other libraries or upgrades required. Does that mean correct dependancy tree and stable running? Still then hard to understand why the rules are so strict even on ubuntu :)

---

### Post by Xceptiona1 on 2005-12-22
What did you do to get Asterisk working on Ubuntu?

*EDIT* I found this post and will attempt it tonight.
[http://ubuntuforums.org/showthread.php?t=22462&](http://ubuntuforums.org/showthread.php?t=22462&)

---

### Post by muppetmaster on 2006-01-03
Any progress on this?  And getting it to v1.2.1 ([http://www.asterisk.org)?](http://www.asterisk.org)?)

---

### Post by DenOK on 2006-01-12
Hi all!

Sorry if this is not right place but, I've used Asterisk before and then I switched to Kubuntu, I'm not an expert in Linux so I gave up building it from sources (there even wasn't "make" by default!)

Them I did this way:
> 
*EDIT* I found this post and will attempt it tonight.
[http://ubuntuforums.org/showthread.php?t=22462&](http://ubuntuforums.org/showthread.php?t=22462&)


and installed packages with Adept, after downloading it reported an error about missing or broken package, I don't remember exactly.

But anyway Asterisk was reported as installed but of course not working!

*It launches only under root then write warning and quits*:( 

And I don't need new user "asterisk" to work. How to avoid this?

I'll be very thankfull if someone give me any advice on how to install Asterisk on Kubuntu.

---

### Post by andrius on 2006-02-01
I think dependency on mgp123 is broken as asterisk depends exactly on mpg132, not on wrapper to mpg123 from mpg321. I have sent bug report to ubuntu, but it looks like nobody noticed it.

---

### Post by gordatron on 2006-06-27
New to linux i have been struggling to install asterisk, through as many ways as been discussed here (though being a newbie who knows what mistakes i am making!), none of them seem to work, so for the moment i am going to have to try Debian?

Please add it to the repository, i am really liking ubuntu.

---

