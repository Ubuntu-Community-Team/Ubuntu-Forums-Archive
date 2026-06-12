---
title: "Stand Alone Grub"
date: 2009-01-03
forum: General Help
---

### Post by svenofix on 2009-01-03
Can someone tell me how to install Grub onto a computer without using any linux distros? I've read some guides, but honestly they make absolutely no sense to me, such as this one: [http://www.gnu.org/software/grub/manual/html_node/Installing-GRUB-natively.html#Installing-GRUB-natively]("http://www.gnu.org/software/grub/manual/html_node/Installing-GRUB-natively.html#Installing-GRUB-natively") or this one: [http://orgs.man.ac.uk/documentation/grub/grub_3.html#SEC8]("http://orgs.man.ac.uk/documentation/grub/grub_3.html#SEC8").

Actually I think my question comes down to if and how I can make bootable grub cd?

---

### Post by logos34 on 2009-01-03
Follow this guide to make a grub boot cd:

[http://orgs.man.ac.uk/documentation/grub/grub_3.html#SEC11](http://orgs.man.ac.uk/documentation/grub/grub_3.html#SEC11)

*Note: 'stage2_eltorito' file is now in /usr/**lib**/grub/i386-pc/

You could also make a [dedicated Grub partition]("http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_Grub_Partition_").

But the pages you linked to are for writing grub to the MBR of a disk with linux installed

---

