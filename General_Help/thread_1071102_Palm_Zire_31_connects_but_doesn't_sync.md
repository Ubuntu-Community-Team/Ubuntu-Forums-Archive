---
title: "Palm Zire 31 connects but doesn't sync"
date: 2009-02-15
forum: General Help
---

### Post by EI51 on 2009-02-15
Hello all, my Palm Zire 31 gives off a connection signal when I go to sync it but it doesn't bring any data over. It picked up the name of the PDA but that was about the only info that was transferred. Any ideas?

---

### Post by darlpmc on 2009-02-16
One issue that I ran into (8.04), was that the 'visor' module that handles the palm USB attachment isn't loaded.   

   modprobe visor 

(possibly via sudo) 
seems to solve that part of the problem.

You then can either start gpilotd-control-applet , or jpilot . 


The other issue that I noticed after that was that, with jpilot, I need to start the pilot syncing before I start the sync in jpilot.

---

### Post by EI51 on 2009-02-17
Thanks for the help.  I'll have to give that a try.  I've read many posts on the problems that people have had with Palms in 8.10.  I wasn't getting any connection or any sign on the computer talk to the Zire 31 until I ran an update.  But like I said now it beeps but doesn't download any info between the two.  I looked at one how to and it said to sync the Palm using the Tools menu in Evolution. The only problem is there is no Tools drop down menu in Evolution. Weird.  Anyway, I'm sure I'll figure it out.  Anybody else got an ideas/expeiences/help?  Thanks again.

---

### Post by EI51 on 2009-02-17
Well, never mind.  I got it to work!! Boy do I feel kinda silly but I want to post this so if other people have the same problem they might try this.  All I had to do, was quite simply, enable all the conduits that I wanted to xfer from the computer and PDA and visa versa. So there you have another hurdle solved.  Thanks again.

---

