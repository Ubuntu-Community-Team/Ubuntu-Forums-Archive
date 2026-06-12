---
title: "how to install qutemol?"
date: 2011-11-21
forum: Education &amp; Science
---

### Post by Morpholinux on 2011-11-21
I want to install Qutemol [http://qutemol.sourceforge.net/]("http://qutemol.sourceforge.net/")
I found a deb package here [http://pkgs.org/download/qutemol]("http://pkgs.org/download/qutemol") but clicking on it starts Ubuntu Software Centre saying that "Dependency is not satisfiable: libwxbase2.8-0 (>= 2.8.12.1)"

How can I "upgrade" libwxbase? Is it safe to do that?

Searching a bit more on google, I found that the package is (will be? ) published in ubuntu precise, but it seems all builds have failed
[https://launchpad.net/ubuntu/precise/+source/qutemol/0.4.1~cvs20081111-1]("https://launchpad.net/ubuntu/precise/+source/qutemol/0.4.1~cvs20081111-1") 
any help will be extremely appreciated!

---

### Post by crazy bird on 2011-11-22
First of all, which version of Ubuntu are you running? Just a tip: next time when you post a question, please provide us with more info like the version of Ubuntu you're using or if you're using Kubuntu or Xubuntu... 
 
 
> Ubuntu Software Centre saying that "Dependency is not satisfiable: libwxbase2.8-0 (>= 2.8.12.1)"
This message means that the version already installed or required is older then needed by the program. Most likely you have version 2.8.0 in your repositories. The program needs at least version 2.8.12. 
 
>  How can I "upgrade" libwxbase? Is it safe to do that?
It is safe. However, upgrading a package migth lead into upgrading packages which are depending on the libwxbase package. So those package migth be upgraded as well. But normally it should give any problems. I never had any issues related to upgrading certain packages.
 
 
>  Searching a bit more on google, I found that the package is (will be? ) published in ubuntu precise, but it seems all builds have failed
[https://launchpad.net/ubuntu/precise/+source/qutemol/0.4.1~cvs20081111-1](https://launchpad.net/ubuntu/precise/+source/qutemol/0.4.1~cvs20081111-1) 
any help will be extremely appreciated!
 
I only can provide you with this link:
[http://packages.ubuntu.com/search?keywords=libwxbase&searchon=names&suite=all&section=all](http://packages.ubuntu.com/search?keywords=libwxbase&searchon=names&suite=all&section=all)
As you can see, there are only older versions available then you need (pls correct me if i'm wrong). 
 
You migth be lucky when you use the backport PPA, but no succes guaranteed ofcourse! 
 
But first provide us the info about your Ubuntu version.

---

### Post by Morpholinux on 2011-11-22
Ubuntu 11.10 (sorry about that)
And yes, that's part of the problem, those are stable versions so are a bit older (at least that is what I understand)

---

### Post by Morpholinux on 2011-11-27
[http://lightnir.blogspot.com/2008/09/cute-molecules.html]("http://lightnir.blogspot.com/2008/09/cute-molecules.html")
[http://cupnet.net/ambient-occlusion-pymol/#comment-331]("http://cupnet.net/ambient-occlusion-pymol/#comment-331")

Ok, the best I found were those links

hope it helps somebody at sometime

---

