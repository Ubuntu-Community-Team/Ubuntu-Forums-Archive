---
title: "running out of hard drive space, help"
date: 2009-06-02
forum: General Help
---

### Post by coops351 on 2009-06-02
right i partition only a small part of my hdd to try out ubuntu 9.04 and i like it alot better then the previous 8.10 so i started using thus installing programs so i can use it.

ive got less then 400mb left on the partition, if i create another partition is there way i can intergrate that partition into the current filesystem without installing linux again?

cheers for the help

---

### Post by merlinus on 2009-06-02
You can use gparted to enlarge the size of your ubuntu partition:

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

---

### Post by coops351 on 2009-06-02
after i create more space can i intergrate this partition into my current linux so when i install more programs will it install directly to that hdd?

---

### Post by perrti-y02 on 2009-06-02
What you would be doing in that situation is making the space Linux is using bigger so it is already integrated. This would only work if you can get rid of some stuff off the hard drive that is being used elsewhere, Windows, /home partition, that kind of thing.

---

### Post by coops351 on 2009-06-02
right thanks very much :)

---

### Post by ajgreeny on 2009-06-02
You don't say, but if you are running Vista, I recommend that you use the vista disk management tools to shrink the vista partition, and not use gparted which has been known to make vista un-bootable.

Then having used that to free some space just resize your ubuntu partition with gparted on the ubuntu live CD to take up that space.  It may take a long time as you will probably, in effect, be moving the ubuntu partition to the "left" so it will need to be copied and then written back to drive.  Make sure also that you defrag a couple of times before you shrink the vista partition, and don't forget to backup everything first just in case.

---

