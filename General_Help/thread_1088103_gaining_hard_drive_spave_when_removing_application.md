---
title: "gaining hard drive spave when removing applications?"
date: 2009-03-05
forum: General Help
---

### Post by sansa dude on 2009-03-05
i just installed a fresh install if xubuntu from an alternate cd to a 6gb hard drive once that was installed i checked and it said i have 3.4gb free disk space. then i went into the add/remove applications and removed alot of applications that were mostly all the programs that can be uninstalled and were not system tools then i checked how much space i have it said 3.3gb left. i don't get it any ideas? i haven't installed any updates. so i don't know whats going on. any ideas?

---

### Post by izizzle on 2009-03-05
Perhaps a restart of the system would reallocate space?

---

### Post by sansa dude on 2009-03-05
no it still says 3.3 GiB left

---

### Post by dcstar on 2009-03-05
> **sansa dude said:**
> i just installed a fresh install if xubuntu from an alternate cd to a 6gb hard drive once that was installed i checked and it said i have 3.4gb free disk space. then i went into the add/remove applications and removed a lot of applications that were mostly all the programs that can be uninstalled and were not system tools then i checked how much space i have it said 3.3gb left. i don't get it any ideas? i haven't installed any updates. so i don't know whats going on. any ideas?

One of the features of Linux is that the inherent structure means that resources are shared - there are many (many) shared program libraries installed that multitudes of individual programs use, but the programs themselves can actually have a (relatively) small amount of code.

Because these libraries are shared, unless the uninstall process **knows** with 100% certainty that a program it is uninstalling can have the libraries it uses uninstalled, then it cannot remove those libraries.

You can run tools to find "orphaned" libraries, but there is always a risk that you may mistakenly remove something that is actually needed and cause yourself problems.

---

### Post by mcduck on 2009-03-05
Try running "sudo apt-get clean" to remove apt's cached package files,a nd perhaps "sudo apt-get autoremove" to remove any unnecessary dependencies.

If that doesn't free your space it's quite likely that the programs you uninstalled simply didn't take that much space.. ;)

Also, you can use "du -f " to check the disk usage to try to find out where your disk space is being used. Run it in / first, then if any directory seems to be using a lot of space move there and run the command again. Continue until you've found what's eating your space.

---

### Post by mb_webguy on 2009-03-05
You might want to take a look at [this]("http://maketecheasier.com/8-ways-to-maintain-a-clean-lean-ubuntu-machine/2008/10/07").

Also, have you emptied your trash lately?  Files deleted to the trash still take up drive space.

---

### Post by sansa dude on 2009-03-05
> **mb_webguy said:**
> You might want to take a look at [this]("http://maketecheasier.com/8-ways-to-maintain-a-clean-lean-ubuntu-machine/2008/10/07").

Also, have you emptied your trash lately?  Files deleted to the trash still take up drive space.

that list is awesome! thanks for the help!

---

### Post by sansa dude on 2009-03-05
i found out that on my desktop computer which is ubuntu, virtual box was taking up 25.1 gb! ive only got a 80 gb hard drive( 74. something usable memory) so there is my problem right there! same kind of deal with my laptop which is the one on xubuntu which it uses 2.4gb

---

### Post by Slim Odds on 2009-03-05
> **sansa dude said:**
> i found out that on my desktop computer which is ubuntu, virtual box was taking up 25.1 gb! ive only got a 80 gb hard drive( 74. something usable memory) so there is my problem right there! same kind of deal with my laptop which is the one on xubuntu which it uses 2.4gb

VirtualBox only uses the space you tell it to.

---

### Post by sansa dude on 2009-03-05
either way i uninstalled it on both of my computers when i removed the file from my desktop then reebooted it said i have used like 6gb so that was a bonus and it saved about 2-3gb on my laptop

---

