---
title: "Is it possible to install windows with wubi?!"
date: 2009-01-29
forum: General Help
---

### Post by DeltaUK on 2009-01-29
Hey i just wondered that as wubi can install a linux OS from inside of windows without partitioning...

Would it be possible to install a windows OS, within windows with the same method? with wubi or a similar tool?

If we can do it with a linux OS, why not a win OS?

The only problem i can see is the bootloader... but cant we add another windows bootloader as we did with grub?

---

### Post by Feivel on 2009-01-29
Delta,

Can you tell me the name of the forum in the upper left corner?

---

### Post by DeltaUK on 2009-01-29
yeh well this is wubi section and its related to wubi

---

### Post by Feivel on 2009-01-29
> **DeltaUK said:**
> yeh well this is wubi section and its related to wubi

Last I checked Wubi installed Linux.

---

### Post by DeltaUK on 2009-01-30
> **Feivel said:**
> Last I checked Wubi installed Linux.

and im just asking politely, would it be possible to install windows in a similar way.
ur really not helping.
can you answer the question?

---

### Post by halovivek on 2009-01-30
I hope it is not possible. for more about wubi you can read [here]("http://en.wikipedia.org/wiki/Wubi_(Ubuntu)")

---

### Post by halovivek on 2009-01-30
you can find one more [here]("http://ubuntuforums.org/showthread.php?t=39513")
just now i find.

---

### Post by Feivel on 2009-01-30
> **DeltaUK said:**
> and im just asking politely, would it be possible to install windows in a similar way.
ur really not helping.
can you answer the question?

This is being asked in a totally inappropriate forum. Go ask someone over in a Microsoft forum.

---

### Post by joshmuffin on 2009-01-31
Yes it can be done, you need a copy of windows in .iso format and its done using virtualisation. Wubi will only install ubuntu. Look at for a program called virtualbox. There are plenty of tuts out there for it.

---

### Post by Jammanuser on 2009-02-02
Yeah...like the previous posters said, Wubi can only install Ubuntu, not Windows. ;) You can use VirtualBox or similiar to install Windows within a virtual machine. Maybe I'm missing the point here, but why do you want to install Windows within Windows?!! :p If you're trying to get a dual boot of Vista and XP, for instance, then simply create a whole another partition for the Windows you don't currently have, which is a far better method of using two different OSes on the same computer anyway, as any type of virtualization has limits, while installing to a real partition has none. 

If you need help with the partitioning and the dual boot, then I would be happy to help. I have actually managed to tri-boot my own computer with Vista, XP, and Ubuntu 8.10, using an combined method of EasyBCD (for adding boot entries to the Vista boot menu)and BING (BootIT Next Generation). The latter program mentioned has the capability to do all of your partitioning, imaging, booting, and so forth that you might need to do, but unfortunately it is not free. Its not expensive (actually only approx. $35 US), but if you feel it is (expensive, that is...) for you, for whatever reason, then you will most likely want to use the free Gparted solution, which only has the partitioning capability, and not the other features BING has.

Anyhow, it is all up to you, and I will let you make the decision. ;)

Cheers! :popcorn:

-Jam man

:guitar:

---

### Post by azmo35 on 2009-02-02
Sorry disappoint but no it is not possible,but you have a small software from microssof called virtual pc is free but not very good as virtualbox,so get a life and  make questions about wubi/ubuntu and not how to try windows 7 with wubi.

---

### Post by lykwydchykyn on 2009-02-02
Sheesh, some of you guys need to chill out, it's just a question.  

@OP: it depends what you mean by "possible".  I've tried to do various hacky things with the windows install ISO, but they are not often successful (like making it available over PXE with pxelinux, or putting it on a thumb drive).  I would suspect it would take some major modifications that only MS is in a position to make.

How much do you want to get under the hood here?

---

