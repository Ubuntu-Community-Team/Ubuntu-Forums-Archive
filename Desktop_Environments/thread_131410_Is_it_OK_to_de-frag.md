---
title: "Is it OK to de-frag?"
date: 2006-02-16
forum: Desktop Environments
---

### Post by mit on 2006-02-16
Hi,

I have Ubuntu and XP Pro (need it for work :) )on my laptop.

Can i de-frag from within Windows without the risk of corrupting anything? Is there a de-frag utility within Breezy?

Thanks

---

### Post by frodon on 2006-02-16
Defrag what ? your ubuntu partition ?

The ubuntu partition should be ext3 formated (if you didn't choose reiserFS) and don't need to be defrag because ext3 fragmentation level is very low.

---

### Post by Ramses de Norre on 2006-02-16
Defraging in XP will only affect your windows partitions, so no problem. I'd advice you to do it in XP. No use to do it in Linux however, it's done automatically.

---

### Post by mit on 2006-02-16
oh, that is great! Thanks guys :)

---

### Post by psusi on 2006-02-16
[QUOTE=Ramses de Norre]Defraging in XP will only affect your windows partitions, so no problem. I'd advice you to do it in XP. No use to do it in Linux however, it's done automatically.[/QUOTE]

It is not done automatically, it just isn't really needed because the linux kernel does not use retarded block allocation algorithms like Microsoft does.  If you really want to defrag an ext3 volume you can boot from the live cd and install the defrag package from the universe.

---

