---
title: "using old hard drives"
date: 2008-12-27
forum: General Help
---

### Post by jesse c on 2008-12-27
I have several old working desktops having xp,xp pro, xp business that have no really important files needing saving but dont want to throw out and i have a newer Vista/Ubuntu dual boot machine that is my daily user.Question-can i pull out any old hard drive and put it in an internal drive spot and somehow create a triple boot machine? Will ubuntu or vista be able to recognize/use an old installed OS?Can i make an external drive and use the os on any old drive?

---

### Post by pietjanjaap on 2008-12-27
Will ubuntu or vista be able to recognize/use an old installed OS?Can i make an external drive and use the os on any old drive?

What do you mean bij this?

---

### Post by sigurnjak on 2008-12-27
Just moving xp drive to a new hardware could give you some problems with activation or even being able to boot into xp assuming you are moving it to a different machine. On the other hand if you do need any data from them you could put them in , format them and use them for extra storage . If you format them to linux fs you can use this to get to them from MS  [http://www.fs-driver.org/](http://www.fs-driver.org/)   .

One thing i did on the old machine with 6/10/40 gig hd was to set up 10gig root/6gig swap/40gig/home  then tinker with swapiness  to my liking . Also there are some really funky ways to set up you partitions for /var and some other system folders on separate hds  for stability and server needs . 

I say  experiment and read up on creative ways of using spare hard drives .

One more thing to save your xp is create disk image and convert it to a .vdi or .vm and use it in vbox or vm .

Good luck!

P.S. useful links

[http://forumubuntusoftware.info/viewtopic.php?f=43&t=1939](http://forumubuntusoftware.info/viewtopic.php?f=43&t=1939)

[http://ubuntuforums.org/showthread.php?t=1010931](http://ubuntuforums.org/showthread.php?t=1010931)

---

### Post by Iowan on 2008-12-27
I presume you realize there may be cabling/jumper issues to contend with?  You can use a "master" disk as a secondary", but may need to move a jumper (maybe on both drives).

---

