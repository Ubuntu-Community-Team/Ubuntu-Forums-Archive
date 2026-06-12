---
title: "Ubuntu for scientific/educational usage"
date: 2009-04-28
forum: General Help
---

### Post by francescogro on 2009-04-28
Hi, I'm not sure if I'm posting in the right section.
I'm an engineering student, and I loved to use Ubuntu... till I found some difficulties in using programs for the university.
For example, I needed Freefem++ (a PDE solving tool) but the package on the repositories was years old.
I tried to compile it personally, and I found that since 8.10 the support for fortran 77 is dropped! Alas, fortran 77 is still used in a lot of mathematical libraries!
Ok, I compiled without F77; but when I upgraded to 9.04 I found the app didn't work any more. There was a linear algebra library missing; and other libraries missing.
Now, I understand I can't pretend every application out in the web to be already in the repos, but still I feel Ubuntu is letting down those who would like to use it for scientific and school reasons.
Now I changed to Fedora, whose support for scientific usage is better; I'm a bit sad, though, because I like Ubuntu, and I think its approach to usability and user satisfaction is the right way!
I think if Ubuntu seek to become a really complete OS, it cannot leave behind bits like fortran and so on..

---

### Post by mb_webguy on 2009-04-28
On one hand, I can fully understand your frustration that you were having to jump through hoops to get a program you need to work.  It can be quite annoying getting legacy programs installed when neither it nor the legacy libraries can be found in the repositories.

On the other hand, Ubuntu is a community effort.  The packages in the repos are there because someone wanted them there, and the ones that aren't there *aren't* because few users need it, and none of those who do have taken the initiative to package the software (according to accepted standards) or at least requested that it be included (through the proper channels).

And the repositories *do* actually contain support for Fortran 77.  The gfortran compiler will compile Fortran 95 code as well as *most* Fortran 77 code.  And if you absolutely need g77, you could download debs for it and its dependencies [here]("https://launchpad.net/ubuntu/intrepid/i386/g77-3.4/3.4.6-6ubuntu3").  They're technically for Intrepid, but you should still be able to install and use them.

---

### Post by francescogro on 2009-04-29
Well, I know Ubuntu is a community; I also know I haven't the skill to create and mantain a package.
But I happen not to know what are the "proper channels" to request a package, and I'm very interested in them :D 
In fact one of the purposes of this post, apart from letting out my frustration, was precisely to find out if I could suggest a package update :-)

---

### Post by mb_webguy on 2009-04-29
To request a package be added to the repos, create a Launchpad account and file a bug report requesting the package be added.

[Here]("http://bobbo.me.uk/index.php/howto-request-a-package-for-ubuntu/")'s an article walking you through it step by step.

Unfortunately, because of Ubuntu's release schedule, even if your request is granted, the software won't be added to the repos until the next release.  On the bright side, now's a great time to request software additions for 9.10.

---

### Post by francescogro on 2009-04-30
Well, thank you very much- I just filed the packaging request!

---

