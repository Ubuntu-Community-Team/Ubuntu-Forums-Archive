---
title: "Hard disk bussy / swapping"
date: 2006-01-15
forum: General Help
---

### Post by Kjell on 2006-01-15
When I use some applications like QCAD or other video editing application the hard disk can start to swap like - for ever 

The system is hardly useable, the muse pointer is vey difficult to use (harly moves)
I can see that usage of swap space is 100 % and also the processor.

The system is almost loocked up, for over 1 hour - I need to quit every work with Ctrl-Alt-backspace.

What can I do ? 

My swap space is accoring to memmory configuration - when partion the hard drive during installation.

---

### Post by schilcha on 2006-01-15
You can try adding swap-space, but it will not increase the performance of your system. The only thing that'll help is adding some/alot RAM.

---

### Post by Kjell on 2006-01-15
Hej,

 I have 512mb - you recond that I need more ?

---

### Post by dcstar on 2006-01-15
[QUOTE=Kjell]Hej,

 I have 512mb - you recond that I need more ?[/QUOTE]
You need as much as the resources your applications require. If you use memory-hungry applications (like video editing), you need more.

Also ensure that your hard disk is running in DMA mode, this can improve performance significantly.

---

### Post by schilcha on 2006-01-15
It depends, what you want to do... 
There are applications that cannot ever have enough ram. As soon as ram is exhausted, things are getting slow. 

Anyways, you can also have a look at the memory requirements of the processes running. Try "top" (press "M" to sort by memory-usage) in a terminal or use the Gnome System Monitor. You'll see what occupies your memory.

---

### Post by Kjell on 2006-01-15
Hej,
Thanks . I'll try using top the next time.. to see the wich application is taking the most load.

Or I'll just shut-down the application (qcad) and then restart it - to drain the memory and refresh it !  every 20 minutes or so 

I gues the problem is the dynamic memmory swaping, that the system can't drain old and used data to fill with new. 

I gues this has to to with the application (qcad) 

//Kjell

---

