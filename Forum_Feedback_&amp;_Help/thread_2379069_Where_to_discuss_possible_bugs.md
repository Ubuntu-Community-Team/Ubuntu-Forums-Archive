---
title: "Where to discuss possible bugs"
date: 2017-11-30
forum: Forum Feedback &amp; Help
---

### Post by sprinterdriver on 2017-11-30
Hi.

I have bought an old Acer Aspire and decided to install Ubuntu Mate 17.10. It works just fine, but there is some possible bugs I want to report.
I know where to file a bug report, but I doubt that I can search for the relevant bugs (because most of those that report bugs is many levels above me in technical details), so in order to avoid "spamming" with duplicated bugs - are there places to discuss possible bugs on this foru, to get advice about filing bug reports, or so I can get to know if there is already a bug report.

I have seen some other forums (Inkscape) that have a separate sub forum where only bugs are discussed.

---

### Post by ian-weisser on 2017-11-30
EDIT: Withdrawn.

---

### Post by QIII on 2017-11-30
Hello!

Helping with issues is well within the scope of what we do here.  Reporting bugs and relaying messages to the developers at Canonical are not.

If you have a problem, ask for support in finding a solution.  If it turns out to be an apparent bug, file a bug report in launchpad via ubuntu-bug.

---

### Post by mörgæs on 2017-12-01
Thank you for your interest in reporting bugs.

We would all be happy if you would help testing 18.04. In the [development forum]("https://ubuntuforums.org/forumdisplay.php?f=427") people find, discuss, try to reproduce and finally report bugs and they could always use more volunteers. 

See also here:
[https://ubuntuforums.org/showthread.php?t=1011078](https://ubuntuforums.org/showthread.php?t=1011078)

---

### Post by sprinterdriver on 2017-12-02
Ok, so there is a forum for that.

Think I stick to 17.10 at least this week and next, as I do have some work that I cannot effort to loose, but after that I'll consider testing 18.04 because then I'll only use the computer for my own purpose.

Can I upgrade from 17.10 to 18.04, or is it best to just do a clean install?

---

### Post by sprinterdriver on 2017-12-03
I have another question regarding filing bug reports when using ubuntu Mate. Seems like there is a separate place in launchpad to file bugs for Ubuntu Mate. I assume every bug I found should be filed under bugs.launchpad.net/ubuntu-mate and not under bugs.launchpad.net/ubuntu.

But - when I run the command _ubuntu-bug password-gorilla_, I get redirected to bugs.launchpad.net/ubuntu/+source/password-gorilla/+filebug/<long-id-string-here>. Is it ok to file bug this way, or should I always use the url at launchpad for Ubuntu Mate?

---

### Post by ian-weisser on 2017-12-03
If the problem is with Password Gorilla, then file the bug against that application.
If the problem is with the Ubuntu Mate GUI, then file the bug against Ubuntu Mate.
If the problem is with ....well, you get the idea.

Ubuntu, including Ubuntu Mate, is an assembly of tens of thousands of software packages from many thousand upstream projects. It's best to file a bug against the package that provides the buggy code...as best you can determine.

Sometimes, it's not easy to determine which package is best. Then it's best to show us how we can reproduce the error on our systems (you need that in your bug report anyway), and we can advise you an the best package(s).

---

### Post by mörgæs on 2017-12-04
> **sprinterdriver said:**
> 
Can I upgrade from 17.10 to 18.04, or is it best to just do a clean install?

I would keep 17.10 as it is with daily updates (no upgrades) until support runs out. Install 18.04 in a dual boot.

Forget about bugs found in 17.10 and older releases as nobody is going to pay attention. However, if you can reproduce the bug in 18.04 it's valuable information.

> **ian-weisser said:**
> Sometimes, it's not easy to determine which package is best. Then it's best to show us how we can reproduce the error on our systems (you need that in your bug report anyway)

+1
Yes, please discuss your findings in the development forum before reporting. A high quality bug report is likely to carry more impact.

---

