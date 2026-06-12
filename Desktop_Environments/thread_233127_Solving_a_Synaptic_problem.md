---
title: "Solving a Synaptic problem"
date: 2006-08-09
forum: Desktop Environments
---

### Post by geovino on 2006-08-09
Synaptic has not been working. I keep getting this error:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

When I run it it does not complete. How can I get it to run? I've been using this command:

$ sudo dpkg --config -a

Please help.

---

### Post by loserboy on 2006-08-09
are you using


$ sudo dpkg --config -a

or

$ dpkg --configure -a


I've had that happen before, like when i lose connection using automatix or something, i just copy the command and run it and it works everytime

---

### Post by geovino on 2006-08-09
$ sudo dpkg --config -a

But it just hangs and never finishes up. It's very frustrating. 

I'm trying it again... I haven't had this much trouble with Synaptic since I dumped Mepis! Overall I think Ubuntu is better, but so far I haven't been able to get any live streaming or DVD to play! These should be installed by default.

I'll try anything to get this OS to function properly. Thanks

---

### Post by maniacmusician on 2006-08-09
try doing sudo dpkg --configure -a like the error said to. if that doesn't work, then I think there is a purge option that just gets rid of the broken package and has you download it again. I forget the commang though..

---

### Post by geovino on 2006-08-09
I've tried that command many times and it doesn't work.

Does anyone know how to purge it?

---

### Post by maniacmusician on 2006-08-09
are you getting the error because there is a package selected and downloaded but not installed? someone in another thread was having their dpkg --configure -a hang up while trying to set up a downloaded package. if this is the case, you can probably go into synaptic, find the package and unselect it.

---

### Post by geovino on 2006-08-09
I can't get into Synaptic until this problem is solved.

---

