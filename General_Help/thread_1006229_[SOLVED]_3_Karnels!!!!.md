---
title: "[SOLVED] 3 Karnels!!!!"
date: 2008-12-09
forum: General Help
---

### Post by azmo35 on 2008-12-09
Hello,I migrate wubi to a real partition and I would like to ask,it would be safe to delete the 2 karnels i have 1st 2.6.24-19 generic and recovery mode 2sd 2.6.24-21 generic and recovery mode if is safe and possible how i do that,many thanks AZMO.

---

### Post by albinootje on 2008-12-09
As long as you keep the kernel you are currently using it is fine to do that. Check that with : uname -a

---

### Post by azmo35 on 2008-12-09
Thanks for the reply the code returned linux azmo-laptop 2.6.24-22-generic,but the question is how to remove them safely.Many thanks AZMO.

---

### Post by azmo35 on 2008-12-11
Hi,is there anyone can help me please):P

---

### Post by Jammanuser on 2008-12-11
> **azmo35 said:**
> Hello,I migrate wubi to a real partition and I would like to ask,it would be safe to delete the 2 karnels i have 1st 2.6.24-19 generic and recovery mode 2sd 2.6.24-21 generic and recovery mode if is safe and possible how i do that,many thanks AZMO.

Its safe to remove Wubi after moving ur Wubi install to a dedicated partition! ;)

Cheers! ):P

-Jam Man

:guitar:

---

### Post by azmo35 on 2008-12-11
Hello but what I ask is about the 3 karnels,not wubi :lolflag:

---

### Post by Jammanuser on 2008-12-11
> **azmo35 said:**
> Hello but what I ask is about the 3 karnels,not wubi :lolflag:

The kernels should be automatically removed when uninstalling Wubi...if i understand ur question right! ;)

Cheers! ):P

-Jam Man

:guitar:

EDIT: if u need detailed instructions on how to uninstall Wubi...i can help u with that as well! Cheers! :D

---

### Post by azmo35 on 2008-12-11
You understand me very well and is what i'm asking because i have the 3 so is it or not safe delete the old ones and how,thanks.

---

### Post by Jammanuser on 2008-12-11
> **azmo35 said:**
> You understand me very well and is what i'm asking because i have the 3 so is it or not safe delete the old ones and how,thanks.

hmm...i'm not exactly sure what u mean because the way u phrased ur last sentence! ;) if ur still asking how to delete the 3 kernels...well, i think i already answered that in my above posts! ^^ :lolflag: 

however, if u truly understood what i was saying, and was simply saying thanks...ur welcome! :popcorn:

Cheers! ):P

-Jam Man

:guitar:

---

### Post by jocko on 2008-12-11
Yes, it's perfectly safe to remove the extra kernels, as long as you leave the newest one installed..
Just open up synaptic, search for "linux-image" and mark them for complete removal.

---

### Post by azmo35 on 2008-12-11
well you are talking about wubi and i'm talking about real install which left me with 3 karnels, so what i ask it is safe delete the previous 2 and how,thanks.

---

### Post by Jammanuser on 2008-12-11
> **azmo35 said:**
> well you are talking about wubi and i'm talking about real install which left me with 3 karnels, so what i ask it is safe delete the previous 2 and how,thanks.

ahh...ok! i understand now what ur thinking! ;)

ok...so let me lay this one out for u then: When u move Wubi to a dedicated partition, u can boot later into Windows, and uninstall Wubi...this will of course remove the kernels associated with Wubi itself...and leave u with only the kernel that the **real** install of Ubuntu uses! :D

If u still do not understand this...then i'll try to explain it better in clearer terms! :guitar:

Cheers! ):P

-Jam Man

:lolflag:

---

### Post by jocko on 2008-12-11
> **azmo35 said:**
> well you are talking about wubi and i'm talking about real install which left me with 3 karnels, so what i ask it is safe delete the previous 2 and how,thanks.
Do exactly what I told you... uninstall the extra kernels with synaptic. I'm not talking about wubi...

---

### Post by Jammanuser on 2008-12-11
> **jocko said:**
> Do exactly what I told you... uninstall the extra kernels with synaptic. I'm not talking about wubi...

Thanks, Jocko...but i believe he addressed that one to me! ;)

Cheers! ):P

Jam Man

:guitar:

---

### Post by Jammanuser on 2008-12-11
Yes, azmo...u can also delete the kernels using synaptic too, like Jocko said!

either way will work fine...and if u want to keep the Wubi install for some reason, then do what Jocko told u. ;)

Cheers! ):P

Jamman

:guitar:

---

### Post by azmo35 on 2008-12-11
> **jocko said:**
> Yes, it's perfectly safe to remove the extra kernels, as long as you leave the newest one installed..
Just open up synaptic, search for "linux-image" and mark them for complete removal.

Sorry jocko i miss your post i did what you instruct me and worked,thanks a lot and to you jam man for trying help,AZMO.

---

### Post by Jammanuser on 2008-12-11
> **azmo35 said:**
> Sorry jocko i miss your post i did what you instruct me and worked,thanks a lot and to you jam man for trying help,AZMO.

Glad to hear it...and no problem! :D
I'm glad i could help! XD

And now i'm off to work on my own problems... :guitar:

Cheers! ):P

JAMMAN

---

