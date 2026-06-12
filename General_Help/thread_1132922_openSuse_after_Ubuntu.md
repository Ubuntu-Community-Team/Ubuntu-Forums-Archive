---
title: "openSuse after Ubuntu"
date: 2009-04-22
forum: General Help
---

### Post by jofren on 2009-04-22
I am newb on linux and Ubuntu, anyway i have my compputer with win vista, ubuntu 8.10 all ok, but yesterday I installed open suse on a new partition and can't load ubuntu anymore, please some ideas!!!! (sorry my english i am spanish talking guy):confused::confused:

---

### Post by Merk42 on 2009-04-22
Are you sure you didn't overwrite Ubuntu with openSUSE?

Are you still able to boot into Vista?
What bootloader are/were you using? GRUB, LILO?

---

### Post by jofren on 2009-04-22
I supose I din't overwrite ubuntu I am going to try mount ubuntu partition on suse and coment, vista is working,open suse is working, i am using grub or the las loader that openSUSE installed

---

### Post by Merk42 on 2009-04-22
Do you know what partitions openSUSE, Ubuntu and XP are on?
if not
```
sudo fdisk -l
```
should tell you

also what is your grub menu?

/boot/grub/menu.lst ?

---

### Post by coffeecat on 2009-04-22
Opensuse is good at picking up other Linux distros and adding boot options to the grub menu, so it's surprising it didn't do so this time. As others have said, check that you still have an Ubuntu partition.

First question: is the grub menu an openSUSE one? You can tell. It's prettier than the Ubuntu one and says openSUSE all over the place with openSUSE as the first choice. If so, **don't** try to manually edit the openSUSE menu.lst yourself. Opensuse doens't like the user manually editing a whole load of configuration files and will re-edit them back again first chance it gets. Instead, go into YAST. There's a whole load of easy-to-use graphical configuration utilities (which is why you shouldn't edit these files manually) in YAST. It's very powerful. I can't remember exactly where the grub menu editor utility is because I hardly use Suse at all, but it's in there. Have a look in YAST.

---

### Post by randyklein99 on 2009-04-23
I did something very similar yesterday and had the same problem.  I followed directions very similar if not identical to [these]("http://ubuntuforums.org/showthread.php?t=224351").  

This technique gave my Ubuntu back, but I can't boot OpenSuse anymore.  Although I'm pretty sure I know why.

I don't know why or what Opensuse's install did to not boot Ubuntu, but to by pass it you must tell Grub to look for Ubuntu's boot menu instead of OpenSuse's. And I believe that is what the above instructions do.

---

### Post by jofren on 2009-04-28
sorry, I din't answer before, finaly I resolved the problem, I re-install grub (How to grub on ubuntu comunity) and now ubuntu and open suse, and vista work well.
The problem: when i installed open suse for one reason, i don't know why, linux headers 2.6.27-11 where erased on ubuntu and grub menu was incorrect, after install grub i was able to run ubunru with linux headers 2.6.27-7 ans reinstall 2.6.27-11.

thank you all.

---

### Post by max_power on 2009-04-28
please mark this thread [SOLVED]

---

### Post by jofren on 2009-04-29
yes it's solved i don't know how to mark in that way this thread, I add a tag [solved]...????

---

### Post by cybrsaylr on 2009-04-29
> **max_power said:**
> please mark this thread [SOLVED]

Don't think you can do that anymore.
I couldn't find that [solved] feature.

Think it was removed, along with the ability to thank people for helping you out.

---

### Post by max_power on 2009-04-29
> **cybrsaylr said:**
> Don't think you can do that anymore.
I couldn't find that [solved] feature.

Think it was removed, along with the ability to thank people for helping you out.

thats a bummer..

---

