---
title: "xwine worse than wine"
date: 2005-11-16
forum: Desktop Environments
---

### Post by chrsjav on 2005-11-16
Hello,

I installed xwine and wine via synaptic.  Then when I launch xwine and use it to execute the Acrobat Professional installer, I get a 'Segmentation fault' crash.  But if I just use wine thru the command line, the Adobe installer revs up until it finally says "This program cannot be installed on this operating system".... So I was wondering if wine has the same option xwine has of specifying your operating system.  
"wine --help" has nothing.

Thanks for your help.

My first post,
Chris

---

### Post by rdario on 2005-11-16
[QUOTE=chrsjav]Hello,

I installed xwine and wine via synaptic.  Then when I launch xwine and use it to execute the Acrobat Professional installer, I get a 'Segmentation fault' crash.  But if I just use wine thru the command line, the Adobe installer revs up until it finally says "This program cannot be installed on this operating system".... So I was wondering if wine has the same option xwine has of specifying your operating system.  
"wine --help" has nothing.

Thanks for your help.

My first post,
Chris[/QUOTE]

try with crossover
[http://www.codeweavers.com/products/cxoffice/]("http://www.codeweavers.com/products/cxoffice/")

---

### Post by darknuala on 2005-11-16
If you don't want to shell out the bucks for crossover, try looking at the wine config file, and see what the default os is set to.  I think it usually defaults to win98, but i've found changing that option makes all the difference with some apps.  DVDShrink worked best under winnt, while Photoshop 7 worked best under winxp.

---

### Post by dcstar on 2005-11-16
[QUOTE=chrsjav]Hello,

I installed xwine and wine via synaptic.  Then when I launch xwine and use it to execute the Acrobat Professional installer, I get a 'Segmentation fault' crash.  But if I just use wine thru the command line, the Adobe installer revs up until it finally says "This program cannot be installed on this operating system".... So I was wondering if wine has the same option xwine has of specifying your operating system.  
"wine --help" has nothing.

Thanks for your help.

My first post,
Chris[/QUOTE]
Try "winecfg" from your user terminal.

---

### Post by chrsjav on 2005-11-17
Thank you david, winecfg is what I was looking for, though now the installer says I have to install IE 5.5... so i'll look into crossover. Thanks!

---

