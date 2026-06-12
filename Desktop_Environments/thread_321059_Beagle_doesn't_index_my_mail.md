---
title: "Beagle doesn't index my mail"
date: 2006-12-18
forum: Desktop Environments
---

### Post by bro on 2006-12-18
I installed Beagle some time ago. It nicely indexed my evolution mail. Evolution doesn't do it for me though so I switched to Thunderbird and deleted (moved inbox) my Evolution mail. 
I have two problems. 

1. Beagle still finding the Evolution mail and suggests to open it in Evolution, which then fails. 
2. Beagle often want to open an email with Firefox. Which is silly in the first place, but Firefox also doesn't read mail so it gives me an error. 

I used the 'exercise the dog' for a while (which completely overtakes one (of two) processors). It's weeks ago so (re)indexing should've finished anyway. How do I (re)configure Beagle to forget the program Evolution ever existed and to open my mail in my mail program? (Thunderbird).

---

### Post by zanglang on 2006-12-19
Try adding "--deny-backend EvolutionMail" as startup parameters for beagled (or i think you could change .beagle/config/daemon.xml as well, but there doesn't seem to be any instructions on changing it). You might have to delete any old Evolution indexes too, i think.

Not quite sure about Thunderbird though (mine doesn't work very well, too), but try checking .beagle/Log/current-Beagle for any errors with its backend perhaps?

---

### Post by bro on 2007-01-03
I completely removed and re-installed beagle. It is now not indexing Evolution anymore. 

It says the Thunderbird backend is installed. 
However... it's not indexing it. 

This link: [http://beagle-project.org/Troubleshooting]("http://beagle-project.org/Troubleshooting")
says (bottom of the page) I might have two thunderbirds installed, but I don't. 

Does anybody have a solution for indexing Thunderbird mail? 

Please?

---

