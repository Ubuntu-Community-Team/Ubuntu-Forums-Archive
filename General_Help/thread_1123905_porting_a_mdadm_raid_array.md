---
title: "porting a mdadm raid array"
date: 2009-04-12
forum: General Help
---

### Post by xixer on 2009-04-12
hello, i'm wondering if a mdadm raid array can be ported between different systems/installs?

i currently have ubuntu installed on its own HDD, and i have some other HDDs set up in a raid-5 array.

i want to reinstall Ubuntu, without losing the raid-5 array; can i remount it after reinstalling without any problems, or is there anything special that needs to be done?

thanks in advance

---

### Post by fjgaude on 2009-04-13
No problem... when you re-install just make sure you don't have any old mdadm.conf file on the boot drive. After the new OS install, install mdadm, and then run this command:

```
sudo mdadm --assemble --scan
```

That way a new mdadm.conf will be created and you are good to go.

I've done this many times going to new motherboards, new OSs without issue, still using the same old raid5 array.

---

### Post by xixer on 2009-04-13
awesome, thank you!

---

### Post by xixer on 2009-04-14
turns out i actually didn't have to do anything.

i unplugged the raid HDDs, installed ubuntu then mdadm, plugged the raid HDDs back in, booted up and my raid partition was automatically recognized.

yay

---

### Post by fjgaude on 2009-04-14
Guess that means you had a valid mdadm.conf file to start with. Great!

Happy computing!

---

