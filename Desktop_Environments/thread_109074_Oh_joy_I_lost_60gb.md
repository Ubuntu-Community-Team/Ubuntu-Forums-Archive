---
title: "Oh joy I lost 60gb"
date: 2005-12-27
forum: Desktop Environments
---

### Post by Sp@z on 2005-12-27
I am so down on Linux right now. I have asked for help in these forums and got very little, I guess I pissed someone off. I followed the rules, I searched for answers BEFORE posting new ones, If I found the answer I posted in that thread not a new one. The xserver would not load, I tried everything I could to fix it, I goggled I posted I did everything right. As it ended up I had to reformat my whole system, which in itself is ok. But now the partition where linux was is not seen by windows or partition magic and Gpart would not work until xerser was working again. How am I going to recover 63 gb iof it is not seen? I tried most of the answers and advice here but to no avail. If I can regain my lost disk space I will forever leave linux to the ppl who know what they are doing. I loved linux, but I am a gamer who has NO OTHER ESCAPE. I installed an nvidia driver 8178 and all my issues began. I need seriouse help to regain my space, if it isn't seen in partition magic how am I to do this?

---

### Post by icarius on 2005-12-27
Have you tried reinstalling partition magic? It worked for me when this happened not too long ago.

---

### Post by soulestream on 2005-12-27
You could boot up a live cd, the run cfdisk. delete the linux partitions and save. Paritition magic(or windows) should then see it as "unpartitioned space"


soule

---

### Post by jjross on 2005-12-27
I had a problem recently that had some of the same symtoms as you described.  It was my hard drive beginning to fail,no fault of ubuntu or windows, it was just the hard drive was old and it was failing,
could not see linux partition and partition magic could not see it either.
If you are experiencing any other odd behavior I would make sure you have all of your data backed up. Good Luck

---

### Post by Sp@z on 2005-12-27
Thank you for the replies. I know this hard drive is still in good shape, I am having no other issues with it at all. I am going to try the live cd option maybe that will help. And yes I have reinstalled partition magic, but it didn't work. Please keep the ideas coming in case the live cd doesn't work.

---

### Post by anil_robo on 2005-12-27
If nothing else works, you can try the following trick:

1. Back up all your data - write it in a CD, or put it somewhere on the internet. Just get it off your hard disk.
2. Now we'll recover the entire hard disk. Boot with Ubuntu Install CD.
3. Order it to erase entire Hard Disk.
4. It will delete whatever partitions you may be having (revealed/concealed) and use the entire diskspace for Ubuntu. 
5. Don't proceed with installation. Simply power off after you've erased the entire HD and are ready to install Ubuntu. Reboot with Install CD again.
6. The install CD partitioner will show you the disk space - you should see all the disk space recovered in one single partition. Now you can do the partitioning again manually, and your space is recovered! :)

---

### Post by Sp@z on 2005-12-27
wow it worked!!!!!!!!!!!! OMG OMG OMG!!!! Thank you all so much. Imma take a break for a few days and maybe try Ubuntu again. All because of video drivers and more than likely total user ignorance!!!!!! Thank you again!

---

