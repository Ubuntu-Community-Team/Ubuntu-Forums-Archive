---
title: "transferring files via ethernet"
date: 2009-07-09
forum: Desktop Environments
---

### Post by raymondvillain on 2009-07-09
Have 2 desktop machines, both running Jaunty, and each one is on the same network.

I need to copy files off of one and onto the other.  Not exactly a backup, but all the directories and files in the /home folder of machine 1 need to be stored somewhere on machine 2.

About 60 gigabytes of stuff needs to come across the ethernet cables.

I thought it would be easy since, using Nautilus, I can see each machine from the other by selecting "Places>network" and clicking on the icons.

But even if I use "gksudo Nautilus" I keep getting stonewalled with permissions etc.

I've even copied the contents of the /home directory into another location and have set share permissions on this second folder.

What is the best way to go about this mundane ordinary sort of file transfer?

Is there a way to use the terminal window to access another machine on the same network?

---

### Post by csabo2 on 2009-07-09
You could try using SCP. 

[http://www.computerhope.com/unix/scp.htm](http://www.computerhope.com/unix/scp.htm)

---

