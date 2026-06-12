---
title: "Shutdown splash screen problems!"
date: 2006-08-23
forum: Desktop Environments
---

### Post by fo0b4er on 2006-08-23
I have a problem with my shutdown splash screen that I hope someone can help me with.  I use Xubuntu with the i686 kernel (which could be the cause of the problem based on other posts I've read).  When I click shutdown the screen shows the tty1 terminal for most of the shutdown process.  Typing with the keyboard does nothing so I can't give commands or switch back with CTRL-ALT-F7 :(.  The splash screen is only shown for the last ~5 seconds before the computer powers off.  My problem is similar to what is mentioned here:
[http://www.ubuntuforums.org/showthread.php?p=969664#post969664](http://www.ubuntuforums.org/showthread.php?p=969664#post969664)
except that I do not even see the text version of the splash screen, I just see tty1 (and I use Xubuntu, not Kubuntu).  Does anyone know what I can do to see the splash screen for the whole process?  I would try this:
[https://launchpad.net/distros/ubuntu/+source/kdebase/+bug/34821/comments/11](https://launchpad.net/distros/ubuntu/+source/kdebase/+bug/34821/comments/11)
except I don't really understand how to do it (this is my first week with Xubuntu, but I'm a fast learner! :)).

PS: the computer would not power off at all before I followed the instructions here:
[http://www.ubuntuforums.org/showthread.php?p=1090643#post1090643](http://www.ubuntuforums.org/showthread.php?p=1090643#post1090643)

---

### Post by fo0b4er on 2006-08-30
Come on can't someone out there help me? :-k

---

### Post by fo0b4er on 2006-09-04
I have found a solution to my problem.  I followed the instructions at this site:
[http://www.mail-archive.com/kubuntu-bugs@lists.ubuntu.com/msg05794.html](http://www.mail-archive.com/kubuntu-bugs@lists.ubuntu.com/msg05794.html)
But, since I use gdm and I didn't know how to stop it from running usplash, I just did the /etc/rc[06].d/K00usplash_down part.  This worked the first time I shutdown the computer, but after that it would just flash on, then go to tty1 as before, then re-appear for the last few seconds.  I then started playing around with the file /etc/init.d/usplash.  I found that commenting out the two lines "chvt 1" worked almost perfectly.  I do not have any idea why.  Usplash now starts up at shutdown (and reboot) and runs until when it used to start before.  At that point the screen flashes and the list restarts but at least usplash keeps going :D.  Also, now at startup there are a few seconds between when usplash exits and gdm starts when I can see plain text.  This did not happen before my changes.  Could somebody explain to me what my changes did and why they caused these other two minor problems?

---

### Post by fo0b4er on 2006-10-28
After upgrading to xubuntu edgy I had another splash screen problem (this time with the bootsplash) that I thought readers of this thread might want to know about.  I have posted a description of the problem and a solution at [http://ubuntuforums.org/showthread.php?t=287204](http://ubuntuforums.org/showthread.php?t=287204).

---

