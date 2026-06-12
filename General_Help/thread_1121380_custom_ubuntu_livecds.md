---
title: "custom ubuntu livecds?"
date: 2009-04-10
forum: General Help
---

### Post by Meow27 on 2009-04-10
hi, i wanna know if ubuntu's iso can be tampered with so i can remove open office from it. i want to do this so i can 
(a) burn the iso on a cd-rw
(b) so i dont have to go over removing it and reinstalling it with a new one (when the new one comes out)

i think slax users will understand me when im asking this question. ill state it again. is there a special file that is distributed or something that takes DEBs and burns them into a new disk image or whatever and make a livecd out of it..

its hard for me to explain, [http://www.slax.org/build.php](http://www.slax.org/build.php) . in the tar here, there is a script that burns everything into an iso. im wondering if there is something similar for ubuntu 

(note: im very redundant in this post cause i dont know how to properly phrase my point. if i need to do more explaining, please point it out to me)

---

### Post by crazypeppo on 2009-04-10
[http://en.wikipedia.org/wiki/Remastersys](http://en.wikipedia.org/wiki/Remastersys)

Check this out...I think it is what you want!

---

### Post by crazypeppo on 2009-04-10
[http://ubuntuforums.org/showthread.php?t=1073838](http://ubuntuforums.org/showthread.php?t=1073838)

Here's a thread in the forums.. "How to Remastersys"

---

### Post by Meow27 on 2009-04-10
i think this is what i want, thanks!

ill post if i succeed

---

### Post by Meow27 on 2009-04-10
from what i understand, this software requires the host's OS to make the image of that brand of OS

its a little too much for me, i need something simpler that takes an iso and edits it, i dont want to risk my own os in the process.....

---

### Post by crazypeppo on 2009-04-11
Hmm...I think I understand what you want:

Create an iso. disk to use for fresh installs w/o open office. I accomplished this by removing open office in synaptic package manager and following the remastersys. It never had any "risk", well all computing is a risk. It copied my current os with the things I wanted on it or off of it to my new iso. disk.

You could also "generate a package download script" in synaptic uder the file tab this is an option. you could save your current setup to an iso. so when you install a new system  it will load all the packages you have on yours.

---

