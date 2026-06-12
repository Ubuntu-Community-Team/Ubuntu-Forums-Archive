---
title: "Problem running perl scripts"
date: 2009-04-02
forum: General Help
---

### Post by darkfeline on 2009-04-02
I have problems running my perl scripts by double-clicking.  Running from terminal "perl program.pl" works, but double-clicking and clicking run does not.  Allow to be run as executable in properties is checked.  My program is headed with #!/usr/bin/perl.  I can run bash scripts by double-click and run, but not perl ones for some reason.  Can someone help?

I did some tests and here's what happened:
My perl scripts:
don't run via double-click>run or double-click>run in terminal
do run through terminal

Test very simple perl script:
doesn't run via dclick>run but it works through dclick>run in terminal

Test very simple python script:
same as the simple perl

Allow executing as program is check for all of them, and the #! are present as the first line in all of them as well.

---

### Post by darkfeline on 2009-04-03
Never mind, I fixed it.  I copied the entire script into a new file, and now it works.  I'm guessing it might be a windows/linux incompatibility issue, since my scripts were originally written on a windows, and I just moved the files over to my ubuntu.

---

