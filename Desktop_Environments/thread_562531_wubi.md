---
title: "wubi"
date: 2007-09-28
forum: Desktop Environments
---

### Post by benner on 2007-09-28
i installed edubuntu on 5 machines in my classroom and it appears that wubi is not ready for prime time.  these machines are so slow that it is ridiculous.  i hyped edubuntu in my school to the students and the other teachers and then decided to try the wubi installer when initial reports were really positive.  these machines are pentium 4's with 512MB of RAM.  next to them i have a PIII with only 192MB of RAM and it runs almost twice as fast.  It has a native installation.  I did some reading and there are a lot of others who claim the same problems.  now i lost a week getting these machines set up exactly as i wanted and i have to do it all over again.  i know it is still in beta but for anyone wanting to install ubuntu on a windows machine, you may want to second guess wubi.  from what i read, it will take a lot more than bug fixes to get it up to speed.

---

### Post by trippinnik on 2007-09-29
I recommend taking a look at this article: [http://www.freesoftwaremagazine.com/articles/linux_terminal_server?page=0%2C2](http://www.freesoftwaremagazine.com/articles/linux_terminal_server?page=0%2C2).  I think your problem maybe the power of the server.  Since you have P4s with 512 MB of Ram using this type of system doesn't utilize their memory or processing power.  
I think for your configuration, local installs with an automounted /home directory on an NFS share.  This way you can have the centralized backup, and settings that the LTS gives you, but actually use the processing power on each of the systems.  
As for speeding up your install process you could do one install, use Partimage to save the image (probably to the NFS server), then use partimage again and image the computers from that.  That is as long as they are identical machines. 
Let me know how it goes, I'm pretty interested in this stuff, but don't get to do it anymore.

---

### Post by trippinnik on 2007-09-29
Sorry, I misunderstood.  Are you not allowed to modify the partitions to dual boot?  What are you using these machines for?

---

### Post by trippinnik on 2007-09-29
Apparently there's a way to change it to a native install [http://wubi-installer.org/faq.php](http://wubi-installer.org/faq.php)

---

### Post by evilmnky204 on 2007-09-29
I use Wubi, it isn't slow on my PC at all, I'm running an AMD 64 3400+, 1 GB of ram, and an ATI x1650 Pro (hopefully will be supported soon :( )

---

### Post by benner on 2007-09-30
it is a bank of 5 machines in the back of a grade 2 classroom.  last year, i had linux running exclusively but the machines were a bit older.  this year, i had 5 newer machines put in.  i am not an admin on the network in the school.  just a classroom teacher.  i tried installing from desktop cd's with a couple of different copies i had but the cd-roms in them were having trouble reading the copies.  the drives are pretty flimsy on these machines.  anyways, the machines already have 2000 on them so i thought i would leave it, at least for a while.  i didn't feel like downloading a third image or buying another bunch of blanks from a different manufacturer with a different colour coating etc... when i read a post about wubi on desktoplinux or something like that.  so i ran it and it installed like a charm.  but after a week with them i found that the performance was pretty crappy.  they ran windows 2000 way faster and the little p3 next to them with a native ubuntu install was also way faster.  literally, it would take 3-5 minutes for openoffice to start up, even after i deselected the java in the tools menu.  after googling and some reading, i found a lot of posts about wubi being slow and some technical reasons why so i just thought i would post here as a caution to anyone who is thinking about trying it.  i plan to go back and find a disk that the cd-roms can read an do a regular install from its own partition.  anyone who still wants to try it, good luck.

---

