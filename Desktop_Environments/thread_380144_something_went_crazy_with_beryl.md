---
title: "something went crazy with beryl"
date: 2007-03-09
forum: Desktop Environments
---

### Post by progrockusa on 2007-03-09
ok i don't know what happend but i accidently hit control alt and F9 didn't know how to get back so i just hit reset (yes i'm a stupid noob) but now beryl won't load up and show the fancy stuff
anyways i thought i'd try to install nvidia drivers again since my resolution was screwed up again when i restarted 
so when i get to this point sudo aptitude install nvidia-glx it's not even downloading at 1 kbps   what is wrong?

---

### Post by Kateikyoushi on 2007-03-09
Does it install despite not downloading ? Because the package might be on your system from the previous install so can be installed without redwnloading.

---

### Post by K.Mandla on 2007-03-09
(Shifted to Desktop Environments. ;) )

---

### Post by aidanr on 2007-03-09
> **progrockusa said:**
> i accidently hit control alt and F9 didn't know how to get back so i just hit reset

hitting ctrl+alt+F6 will take you back to the desktop (although recently for me switching between tty's with beryl running causes a black screen upon switching back, so i have to killall beryl first)

also if you do need to hard reboot, this is the safe way to do it [http://en.wikipedia.org/wiki/Magic_SysRq_key](http://en.wikipedia.org/wiki/Magic_SysRq_key)

have you tried running beryl-manager from a terminal, and if so does it give any error?

you might also want to run a filesystem check on the next bootup, see [here]("http://ubuntuforums.org/showthread.php?t=77771")

---

