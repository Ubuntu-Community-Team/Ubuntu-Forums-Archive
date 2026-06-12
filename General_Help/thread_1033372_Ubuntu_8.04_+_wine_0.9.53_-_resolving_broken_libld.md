---
title: "Ubuntu 8.04 + wine 0.9.53 - resolving broken libldap2 dependency"
date: 2009-01-07
forum: General Help
---

### Post by EvilChest on 2009-01-07
Hello.

I'm running ubuntu 8.04, and I have following problem:
I have windows software that right now works on wine-0.9.53 only. Wine 0.9.53 isn't available for 8.04 from ubuntu repositories, so I installed package for ubuntu 6 (0.9.53~winehq0~ubuntu~6.10). Package is pinned down according to [_*those instructions*_](http://www.linuxquestions.org/questions/ubuntu-63/installing-old-wine-version-with-apt-getsynaptic-on-ubuntu-8.04-675226/). Now there is a problem.

wine 0.9.53 package for ubuntu6 depends on libldap2 package which is unavailable for 8.04 and is replaced by libldap package. Because of this system see package as broken (although it works fine) and fails to do automatic update. System wants to remove package and can't do it, because it is pinned down. 
In synaptic within properties of wine-0.9.53 package libldap2 is bold (as I undersrtand it, this means unsatisfied dependency).
"sudo apt-get install libldap2" tells me that libldap2 package is not avilable, but alternatives are "slapd" and "libldap-2.4.2". Those packages are already installed, but apparently they doesn't resolve broken dependency in wine-0.9.53. 

I'd like to fix that problem using package manager (I know I can recompile from source, etc). How can I do that? Upgrading to latest wine version is not an option. Is there a way to remove libldap2 from dependencies of installed wine-0.9.53 package, or replace it with valid dependency on libldap > 2? Or can I somehow tell the system that libldap package is the same as libldap2? 

Thanks for your time.

P.S. Originally I wanted to replace distribution with something else, but apparently there will be a free space problem, and this will require too much time. So I decided to fix the problem after all.

---

### Post by EvilChest on 2009-01-18
[[color=red]rant[/color]]
There was no reply within last 11 days neither here, nor on linuxquestions.org. 
This is very disappointing. I expected Ubuntu community to be more knowledgeable/experienced, since the problem isn't incredibly difficult, although it effectively disabled entire automatic update system. So much for being "user-friendly distro", I guess.
[/[color=red]rant[/color]]

Anyway, I was able to fix this problem.

In situation like this (when you have broken dependency, and installing missing dependency is not possible), the only solution is to create virtual package (which is also called "dummy package" or "meta package") - i.e. empty package that tells system that it provides missing dependency.

In my case (required libldap2 >= 2.1.17-1):
1) go to any directory
2) mkdir libldap2/DEBIAN
3) vim libldap2/DEBIAN/control . Or use any other texteditor.
4) in file enter text:
```

Section: otherosfs
Package: libldap2
Priority: optional
Description: libldap2 dummy package
 This package provides dpkg with the information that
 there is a libldap2 installed
 .
version: 2.1.18
maintainer: evilchest<evilchest@example.net>
architecture: i386



```
syntax of "control" file is explained somewhere on the web or in manpages.
5) save file, exit vim (or any text editor).
6) "sudo dpkg -b libldap2"  (this will create package libldap2.deb)
7) "sudo dpkg -i libldap2.deb"

Done. Now package manager won't complain about missing dependency anymore.

I really think that there should be easier way to do that (some kind of "package aliases" in synaptic, or anywhere else), but it looks like there isn't.

---

### Post by Slim Odds on 2009-01-18
> **EvilChest said:**
> [[COLOR=red]rant[/COLOR]]
There was no reply within last 11 days neither here, nor on linuxquestions.org. 
This is very disappointing. I expected Ubuntu community to be more knowledgeable/experienced, since the problem isn't incredibly difficult, although it effectively disabled entire automatic update system. So much for being "user-friendly distro", I guess.
[/[COLOR=red]rant[/COLOR]]

[[COLOR=Red]anti-rant[/COLOR]]
It never ceases to amaze me how cranky people get when their **FREE** resource doesn't live up to their expectations. Perhaps you should use the Microsoft OS. I hear that their **FREE** support is fantastic.
[[COLOR=Red]/anti-rant[COLOR=Black]][/COLOR][/COLOR]

So... how did this get broken in the first place? Since Ubuntu's package management system deals with dependencies just fine.

Also, why aren't you using the latest version of WINE? Version 1.0 is in the hardy-update repository.

---

### Post by EvilChest on 2009-01-18
> **Slim Odds said:**
> [[COLOR=Red]anti-rant[/COLOR]]
It never ceases to amaze me how cranky people get when their **FREE** 
resource doesn't live up to their expectations. Perhaps you should use the Microsoft OS. I hear that their **FREE** support is fantastic.
[[COLOR=Red]/anti-rant[COLOR=Black]][/COLOR][/COLOR]

Save your sarcasm. I'm using slackware linux, and Mac OS or Windows are not for me. Ubuntu is installed on my parents' computer. I hoped they will learn it because it is said to be easy. I was wrong, though, so I'm still the one maintaing that machine. 
[size=1]
Problem with similar complexity gets solved on slackware forum within hour. If it is too basic, you get RTFM reply which points in the right direction. If it is too complex, you normally get a suggestion for the direction of further ivestigation. To get help user has to provide detailed description of the problem, google, and do some man reading. For example "ubuntu broken dependency" doesn't give anything useful - mentions of few similar problems, including one thread on this forum, without solution. 
Gee, even mention of "virtual/meta/dummy package" or right "FM" would help, since I've spent too much time being stuck with wrong idea.
Initially I assumed that dpkg/apt-get/synaptic should have some way to specify that one package is another package. I.e. if you can't install libldap2 on ubuntu, you get list of suggested replacements. But you can't tell package manager that replacement is equivalent to required package. I.e. you can't specify that libldap == libldap2. I accidentally solved the problem when I found mention of metapackages, which led to virtual packages, which led to dummy packages, which led to debian instruction for building packages (which doesn't work on ubuntu, by the way), which allowed to figure out how to make empty debian package on ubuntu.
[/size]
By the way, I also could magically disappear without explaining a way to solve that. 


> **Slim Odds said:**
> 
So... how did this get broken in the first place?

It is explained in my first post. Besides, there are also instructions on how to fix this or similar problem.
> **EvilChest said:**
> 
I have windows software that right now works on wine-0.9.53 only.

[color=red]Wine 0.9.53 isn't available[/color] for 8.04 from ubuntu repositories, so [color=red]I installed package for ubuntu 6[/color] (0.9.53~winehq0~ubuntu~6.10).

[color=red]Package is pinned down[/color] according to [_*those instructions*_](http://www.linuxquestions.org/questions/ubuntu-63/installing-old-wine-version-with-apt-getsynaptic-on-ubuntu-8.04-675226/)


> **Slim Odds said:**
> 
Also, why aren't you using the latest version of WINE? Version 1.0 is in the hardy-update repository.
This is also explained in my first post.
> **EvilChest said:**
> 
I have windows software that right now [color=red]works on wine-0.9.53 only.[/color]


Question was asked on linuxquestions first, I didn't receive reply, then I decided this would be better place due to the larger user base.

---

### Post by gjoellee on 2009-01-18
You havent thought of getting the latest stable version, v.1.0.1 ?

---

### Post by EvilChest on 2009-01-18
> **gjoellee said:**
> You havent thought of getting the latest stable version, v.1.0.1 ?
Latest stable wine is 1.1.13. Released yesterday. The bug that was introduced in 0.9.54 wasn't fixed for a long time, and I doubt it will be fixed right now. I've tried using default wine package (it was 1.1.11 or something at the moment) before installing 0.9.54 package, the problem kept happening. But since I've found out how to deal with broken dependencies, I might try it within few days.

P.S. Guys, maybe I did get a bit too emotional in the 2nd..3rd reply (because it isn't first time something like this happens), but there is really nothing left to discuss. Problem is solved, system works, and solution is posted, and as I said before, upgrading wine is not an option. So thread can be safely closed. Or it can be left open - in hopes that someone will have similar problem and will post questions here.

---

