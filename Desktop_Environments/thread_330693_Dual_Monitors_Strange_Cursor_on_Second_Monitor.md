---
title: "Dual Monitors Strange Cursor on Second Monitor"
date: 2007-01-03
forum: Desktop Environments
---

### Post by gdboling on 2007-01-03
I followed the directions given here:

[http://ubuntuforums.org/showthread.php?t=301951&highlight=xubuntu+monitors](http://ubuntuforums.org/showthread.php?t=301951&highlight=xubuntu+monitors)

And they worked great.  I have my laptop screen as main and a CRT as the default to the right.  The problem is that my mouse cursor on the second screen is a box with colored lines.  I noticed someone had the same problem in the linked thread but was never given an answer that solved the problem.  Has anyone had experience with this and able to solve it?

I have a Radeon 9800 Mobile on a Dell XPS.  Thanks.

Gregg

---

### Post by kEinstein on 2007-01-04
Du you have 'fglrx' installed and running properly? If YES, you should go for this thread on ATi and [BigDesktop]("http://ubuntuforums.org/showthread.php?t=301941"). Otherwise, if you use 'radeon' or 'ati' driver and don't require 3D support, use [MergedFB]("http://www.ubuntuforums.org/showthread.php?p=1773710") based on open-source drivers.
I experienced the same issue both using xinerama and dual-head. The scrambled cursor is a known ATi Bug if I am not mistaken. Among others, I have posted my solution in one of these threads.
[original thread]("http://ubuntuforums.org/showthread.php?t=273213")
[also try this one]("http://ubuntuforums.org/showthread.php?t=273934")
[finally, BigDesktop is also discussed here]("http://ubuntuforums.org/showthread.php?p=1951908#post1951908") including a list of potential solutions on your issue.

---

