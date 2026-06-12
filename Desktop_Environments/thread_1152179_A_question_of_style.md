---
title: "A question of style"
date: 2009-05-07
forum: Desktop Environments
---

### Post by Spritegeezer on 2009-05-07
I am gently moving my systems to Ubuntu from Microsoft.  My last task is to move the data (about 32 Gig in approx 8500 files in 850 folders.)  Could someone point me to source of info for migrating this data.  It's primarily pdf, excel and word files.  I hate the thought of moving it file by file and I'm still clueless when it comes to file structures in Linux.  I'd like to automate the process because the data is constantly being updated.  Preferably I'd like to do it over a weekend so I'm not helpless come Monday morning.  I'd like to organize the data so someone not familiar with the organization of the system wouldn't necessarily say "what was this fool thinking" when first seeing it.  I don't expect a tutorial just point me to a "how to" if one exists.

---

### Post by doas777 on 2009-05-07
well, for the most part the user end of the filesystems are indistinguishable from each other.
if you drag all your folders onto a DVD or across a network share, you can copy them straight onto the ubuntu hdd. all you really have to do is transport them and paste 'em in.

perhaps i'm missing a nuance or two to your quandry, so please let us know if that answer makes no sense to you.

there isn't really a convention for how to store your data. just organize it as thou dost seest fit. the conventions come in when your storing data in your root directory (/usr is for shared user libraries whereas /proc is not, etc). I would recomend you do not store your data on the same partition as your OS (and your /home likely should be on a seperate partition as well)

---

### Post by jaffa_nz on 2009-05-07
kia ora

if its on the same network, just present a share? or you could simply drag and drop in nautilus, or from the windows end.

Think you need to provide more information mate, what you are asking for 'in spirit of your statement' sounds as simple as a drag and drop.  I'm assuming that since youre asking that its more complicated than that?

Where is the data? what connectivity do you have between win data and linux data? does it need to change i mean can it remain on ntfs? is it on external disk?  

cheers

---

### Post by Spritegeezer on 2009-05-07
The problem is the machine with the data is under the influence of Vista.  Vista doesn't even like to talk with XP never mind Ubuntu.  I guess I'll just put it on an external drive and copy it over.  I guess I was just over thinking the problem.

---

