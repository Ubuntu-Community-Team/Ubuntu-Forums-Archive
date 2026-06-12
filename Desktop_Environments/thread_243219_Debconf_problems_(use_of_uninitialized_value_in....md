---
title: "Debconf problems (use of uninitialized value in...)"
date: 2006-08-24
forum: Desktop Environments
---

### Post by cypher35 on 2006-08-24
i've been running into a lot of these problems lately, and i have no idea how to diagnose them...

> Use of uninitialized value in join or string at /usr/share/perl5/Debconf/DbDriver/Stack.pm line 104, <GEN1> line 4.
Use of uninitialized value in join or string at /usr/share/perl5/Debconf/DbDriver/Stack.pm line 104, <GEN1> line 8.
Use of uninitialized value in join or string at /usr/share/perl5/Debconf/DbDriver/Stack.pm line 104, <GEN1> line 12.
Use of uninitialized value in join or string at /usr/share/perl5/Debconf/DbDriver/Stack.pm line 104, <GEN1> line 19.
Use of uninitialized value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 83.
Use of uninitialized value in concatenation (.) or string at /usr/share/perl5/Debconf/Format/822.pm line 84.
Use of uninitialized value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 83.
Use of uninitialized value in concatenation (.) or string at /usr/share/perl5/Debconf/Format/822.pm line 84.
Use of uninitialized value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 83.
Use of uninitialized value in concatenation (.) or string at /usr/share/perl5/Debconf/Format/822.pm line 84.
Use of uninitialized value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 83.
Use of uninitialized value in concatenation (.) or string at /usr/share/perl5/Debconf/Format/822.pm line 84.


this type of error (and by type i mean "Use of uninitialized value in ___ ...") was first encountered while trying to run *'sudo dpkg-reconfigure xserver-xorg'* which refused to generate an xorg.conf for me, and I just recently ran into it again while *apt-get*ing 'cvs'.

Is this a problem with debconf?  What exactly is debconf?
Could this be a problem with my paticular version of Perl or something?

---

