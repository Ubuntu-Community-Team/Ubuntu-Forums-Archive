---
title: "how to properly uninstall openSUSE and install Ubuntu"
date: 2008-12-19
forum: General Help
---

### Post by akapaul on 2008-12-19
Here is what I did so far:

1) I have a computer with Vista on it as primary OS
2) using Vista's shrink volume function, I created a 20GB partition
3) i downloaded openSUSE iso, burned it on dvd, booted, installed it on that 20GB partition
4) now when I turn the computer on, it loads GRUB, and I can choose openSUSE or vista

here is what i want to do...
1) get rid of opensuse
2) get rid of grub
3) make the computer boot straight to vista like it did prior to me installing openSUSE on a seperate unformatted partition

then...
1) i just downloaded 64bit ubuntu... burning it on dvd as we speak
2) i want to install this ubuntu on the 20gb unformatted partition
3) i want it to recreate grub (because currently the grub i have has openSUSE logos)

What's the best way of doing this?
I read bad stories where people cannot launch Vista once they mess with Grub, partitions, etc.

Thanks!

---

### Post by dcstar on 2008-12-19
> **akapaul said:**
> Here is what I did so far:

1) I have a computer with Vista on it as primary OS
2) using Vista's shrink volume function, I created a 20GB partition
3) i downloaded openSUSE iso, burned it on dvd, booted, installed it on that 20GB partition
4) now when I turn the computer on, it loads GRUB, and I can choose openSUSE or vista

here is what i want to do...
1) get rid of opensuse
2) get rid of grub
3) make the computer boot straight to vista like it did prior to me installing openSUSE on a seperate unformatted partition

then...
1) i just downloaded 64bit ubuntu... burning it on dvd as we speak
2) i want to install this ubuntu on the 20gb unformatted partition
3) i want it to recreate grub (because currently the grub i have has openSUSE logos)

What's the best way of doing this?
I read bad stories where people cannot launch Vista once they mess with Grub, partitions, etc.

Thanks!

Simply delete the Suse partition and install Ubuntu, it will set up a new Grub with Vista in it.

---

### Post by zvacet on 2008-12-19
You can remove Suse during Ubuntu install.After install go to the synaptic and install **startup-manager **and with it select whitch OS you want to load first.

---

### Post by cybrsaylr on 2008-12-19
akapaul, 
I had the same setup as you only with XP instead of Vista.
I just put in the 8.10 CD and installed 8.10 in the same 20GB partition SUSE was in. It formated that SUSE partition and installed 8.10 flawlessly in its place leaving XP alone and fully functional.

---

### Post by akapaul on 2008-12-20
> **dcstar said:**
> Simply delete the Suse partition and install Ubuntu, it will set up a new Grub with Vista in it.

My system originally had 3 visible partitions in Vista. The first one was C: (vista) and the second partition was the D: (hp restore partition).

When I installed SUSE, it created 3 extra partitions. I am guessing one of the newly created partitions was for the actual openSUSE partitions, the second one was for GRUB and the third one was probably a swap partition.

When I decided to get rid of openSUSE and install Ubuntu, what I did was deleted all three of the partitions that were created by openSUSE. I rebooted the computer and now I cannot boot into Vista. I don't have a Vista restore CD because this is an HP computer and the recovery is on the recovery partition. (doh!).

So what I am trying to do now is to install Ubuntu from the boot CD and setting up the partitions manually. I am getting more and more nervous that Ubuntu might over right my Vista partition? I hope not!

---

