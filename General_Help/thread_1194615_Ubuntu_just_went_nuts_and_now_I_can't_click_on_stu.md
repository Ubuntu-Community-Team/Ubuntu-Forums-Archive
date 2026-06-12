---
title: "Ubuntu just went nuts and now I can't click on stuff"
date: 2009-06-22
forum: General Help
---

### Post by metalf8801 on 2009-06-22
Well Ubuntu just went nuts and I have next to no idea as to why 

here's what I do know 
I'm running Ubuntu 9.04 and its up to date 
I had firefox, Pidgin, and Miro player open.  I had just watch a video on Miro and I trying to open a new one then all of a sudden the mouse stopped working popperly well it looks like its work (it moves around the screen just fine) but it wont click on most things and if I hold it over something on the taskbar (um I don't know the right name for it if there is one please tell me) the preview of the program is at the top of the screen not just above it like it used to be.  
I can click on one icon on the toolbar that is at the top of the screen but after that I can't click on a different one. I can use the mouse to go though the means that are at the top of the screen but I have to use key commands to open the mean 
 
If I open firefox I can't click on anything.  

key commands seem to be working just fine.   

If this happened in windows I would think I had a virus could that be the case here?  I know there are a handful of virus for Linux.  


Please help
Thanks 
Dan

---

### Post by metalf8801 on 2009-06-23
ok I don't know why but its working now even though it didn't start to work the first time I rebooted the computer.  I still wish I knew why this had happened.

---

### Post by Celauran on 2009-06-23
Hard to say since it's after the fact and you appear to have rebooted more than once. My first guess would be high resource usage. You said 'key commands' seemed to be working fine, so if you experience something similar in the future, you might want to run the top command in a console to see if anything is eating up your CPU cycles.

---

### Post by QIII on 2009-06-23
I agree with the poster above.  First thing to do is top.

If you don't see anything surprising there, you may have to consider hardware.  I don't know how old your 'puter is or what its specs are.  (That might be helpful -- especially if you are using an Intel graphics card and Compiz...)

If you shut down and rebooted immediately and still had the same problem, but shut down again and rebooted after some period of time, it could indicate that something is getting hot.

You can add a processor temp monitor to your panel and watch that to look for a hot processor (which might happen anyway if your processor is getting slammed in top.)

You may also want to do a memtest.

Check that your video card is well seated in the socket (if you don't have integrated video.)  Do the same for your memory.  Check that the keyboard and monitor connections are good.

Rule out hardware failure.

---

