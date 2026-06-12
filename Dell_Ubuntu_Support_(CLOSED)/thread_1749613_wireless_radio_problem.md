---
title: "wireless radio problem"
date: 2011-05-04
forum: Dell Ubuntu Support (CLOSED)
---

### Post by jgoff35 on 2011-05-04
I am using a dell inspiron e1505 laptop. I installed ubuntu 11.04 and had to have a friend who is a linux engineer help me find the drivers for the broadcom card. I was at school today and used fn+f2 to turn off the wireless radio to make the battery last longer. When i came home i tried to turn it back on and it wouldnt go back on. I used to use fedora and my way around this was to restart the computer and there was always this like 5 second time window to turn the radio back on while it was starting up. Now when i try to turn it back on it won't no matter what.

---

### Post by Vishnu V on 2011-05-05
> **jgoff35 said:**
> I am using a dell inspiron e1505 laptop. I installed ubuntu 11.04 and had to have a friend who is a linux engineer help me find the drivers for the broadcom card. I was at school today and used fn+f2 to turn off the wireless radio to make the battery last longer. When i came home i tried to turn it back on and it wouldnt go back on. I used to use fedora and my way around this was to restart the computer and there was always this like 5 second time window to turn the radio back on while it was starting up. Now when i try to turn it back on it won't no matter what.
me too have a similar problem when i was using ubuntu 10.04. Not only wifi bit also brightness keys are not working after 5 seconds. I solved that problem by changing following line in /etc/default/grub
```

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

```
to
```

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash noapic"

```
and then update grub using
```

sudo update grub

```
Please try this
Good luck

---

