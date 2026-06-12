---
title: "Help updating graphics driver (Intel G45 Express Chipset)"
date: 2009-05-24
forum: General Help
---

### Post by Venter127 on 2009-05-24
Recently, Ive been trying to get my graphics drivers updated for my Intel G45 Express Chipset card, but it seems like its just been one problem after another. The drivers I need are third-party, so they need to be added through the use of repositories. I found the website that gives me the repository code ([http://intellinuxgraphics.org/download.html](http://intellinuxgraphics.org/download.html)), But, thanks to my very limited knowledge of repositories Im having a hard time trying to figure out how to install it. Every time I try to add the code it gives me for the repository, It doesnt let me add it. My guess as to why it doesnt work is because it uses some kind of file extension ive never seen before. Whenever Ive seen a repository being added, they always typed "deb" in front of the address, whereas all the code I see on the website has "git" in front of it. 

Also, there are 4 drivers listed there, and my guess is that I need all of them, but If you know otherwise, please let me know.

It might eliminate alot of frustration/confusion someone checked the site of the drivers, and showed me how to to get it to run. Also, Im fairley new to linux, so please keep all instructions very simple and easy to understand and follow.

Any help would be greatly appreciated.

---

### Post by aphirst on 2009-05-26
The "git" protocol allows people to get their hands on bleeding-edge source code, rather than precompiled packages. As such it won't work in apt.

[This thread](http://ubuntuforums.org/showthread.php?t=1130582) covers in a fair deal of depth how to try to resolve Intel graphics issues in Ubuntu; to the best of my knowledge it should get you to a decent state in a relatively short amount of time.

Let us know how it turns out, users reporting back the results is probably the best thing the Intel Driver devs could hope for right now. :P

---

### Post by Venter127 on 2009-05-26
It sounds like it would help me, but Im getting errors with _Step 1_ (I open the xorg conf. file and nothing is there), and half of the explanations I cant understand for the life of me. I need a more down-to-earth explanation of how to get it to work.

---

### Post by Venter127 on 2009-05-27
Never mind problem solved. They still dont run as fast as they should, but It took me forever to figure this one, so I think ill take a short break before I tackle any other problems.

Thanks for the help.

---

