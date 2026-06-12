---
title: "Ubuntu 9.04 - doesn't it have Gparted?"
date: 2009-05-25
forum: General Help
---

### Post by andyd2k on 2009-05-25
I booted up Ubuntu Live through USB but I didn't see Gparted anywhere or in system tools.  System tools wasn't even in the apps menu - I had to check through add / remove

---

### Post by ctrlmd on 2009-05-25
> **andyd2k said:**
> I booted up Ubuntu Live through USB but I didn't see Gparted anywhere or in system tools.  System tools wasn't even in the apps menu - I had to check through add / remove

go to terminal and write 

Gparted

or System >> Administration >> Partition Editor

---

### Post by fooman on 2009-05-25
sorry ignore this

---

### Post by andyd2k on 2009-05-25
that worked - thanks!

---

### Post by sgosnell on 2009-05-25
It's on the System/Administration menu, as Partition Editor.

---

### Post by fogster74 on 2009-05-30
Hey guys,

I just did a clean install of Ubuntu 9.04 and was suprised to find no partition editor on the System Menu; I tried launching gparted from the terminal but got a 'not found error'. No problem, I thought, I'll add it in synaptic - yep, you've guessed it, no sign of it in Synaptic... really odd.

I got it installed through the terminal using 

```
sudo apt-get install gparted
```

So all is good and well. But any idea why I couldn't see it in Synaptic?

---

### Post by louieb on 2009-05-30
Even thought Gparted on the live CD. It is not included in a hard drive install. Been that way since release 5.04.

Don't know why it did not show up in Synaptic - :twisted: guess your computer just had a burp.

---

