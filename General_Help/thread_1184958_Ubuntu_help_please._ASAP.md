---
title: "Ubuntu help please. ASAP"
date: 2009-06-11
forum: General Help
---

### Post by Boxx1993 on 2009-06-11
OK this is really hard to explain but I'll try my best.  When I start Ubuntu- it starts perfectly but before it said's username and password in the normal way a black screen pops up like cmd and it saids username password exactly like the cmd lettering something like that. And when i put my username and password it wont log in, it gets stuck in the cmd formation and then it will say to go to [http://help.ubuntu.com/](http://help.ubuntu.com/).



This happened after i was deleting something in Ubuntu and I turned the computer off forcly because I changed my mind and didnt want to delete it.


I hope you guys could help me out.

Thank You,
Boxx

---

### Post by jonobr on 2009-06-11
Hello


Im assuming the desktop was working ok before this event?

Can you tell us what you were deleting?
Can you recall the exact command you used to delete and what?

Thanks

---

### Post by ActiveFrost on 2009-06-11
What this command says ?
```
startx
```

---

### Post by Boxx1993 on 2009-06-11
i was deleting python but when i saw something else deleting i don't recall what it was but it wasn't python i forced to stopped it by turning off the comp.


i didnt use program/removes i used something else under system i forgot what it was since it didnt let me delete it through remove/program it told me to go to systems and got to another place to delete it i dont recall what it was called

---

### Post by donkyhotay on 2009-06-11
In the future, if you delete the wrong thing, assume it's gone and focus on replacing it. Unlike other OS's linux actually does what you tell it to do (especially if you have root access), unfortunately if that command amounts to 'shoot yourself in the head' well... you get a mess. Also, turning a computer off while it's trying to remove something like that generally just does more harm then good. This problem is definitely repairable (worse case scenario back everything up and reinstall ubuntu again) but if you're looking at a solution besides that, see if you can get into repair mode (hit esc at the GRUB screen) and get a working bash terminal. If this fails you'll need a liveCD to boot the computer and try reinstalling/repairing the corrupt files.

---

### Post by Boxx1993 on 2009-06-11
OK so how do i repair it and would my files be deleted?

---

### Post by jonobr on 2009-06-12
Hello

Did you try startx and see what happened?
I dont think people will be able to help you get out of your jam.
Its hard to say what when wrong without know what happened.

Is there a chance that you hit some shortcut keys and ended up in the prompt?
If you hit control alt f7, what does that do?



removing python should only remove python but it sounds as if you knew it was doing more then when it was removing. which makes it sound as if you were removing something else.

I think your only option maybe a reinstall, but try the suggestions below before doing so

---

### Post by eilios on 2009-06-12
I think he corrupted the filesystem(he shut down without unmounting the filesystem). I doubt there is any way to fix this, you would be best to reinstall.

---

### Post by cariboo on 2009-06-12
Many programs depend on python, if you removed it, you probably removed quite a few files that were needed to run the desktop. If you are at the command prompt I would suggest you try to reinstall the desktop to see if that solves your problem. at the prompt type:

```
sudo apt-get install ubuntu-desktop
```

Of course you have to have a network connection before you run the above command to do this at the prompt type:

```
sudo dhclient eth0
```

substitute your network device for eth0 if it is different.

---

### Post by eilios on 2009-06-12
> **cariboo907 said:**
> Many programs depend on python, if you removed it, you probably removed quite a few files that were needed to run the desktop. If you are at the command prompt I would suggest you try to reinstall the desktop to see if that solves your problem. at the prompt type:
 
```
sudo apt-get install ubuntu-desktop
```
 
Of course you have to have a network connection before you run the above command to do this at the prompt type:
 
```
sudo dhclient eth0
```
 
substitute your network device for eth0 if it is different.
He can't login at the command prompt, so he can't reinstall ubuntu-desktop.

---

### Post by Cheesemill on 2009-06-12
Removing python is a **very** bad idea. It generally screws your system up as so many programs depend on it being installed.

Cheesemill

---

### Post by LKjell on 2009-06-12
> **Boxx1993 said:**
> OK this is really hard to explain but I'll try my best.  When I start Ubuntu- it starts perfectly but before it said's username and password in the normal way a black screen pops up like cmd and it saids username password exactly like the cmd lettering something like that. And when i put my username and password it wont log in, it gets stuck in the cmd formation and then it will say to go to [http://help.ubuntu.com/](http://help.ubuntu.com/).



This happened after i was deleting something in Ubuntu and I turned the computer off forcly because I changed my mind and didnt want to delete it.


I hope you guys could help me out.

Thank You,
Boxx

As other pointed it out it is king of vague. So we need to start from the beginning. Maybe the easiest is to reinstall everything but that is not fun. Do you think you can boot into recovery mode? Just press esc before the 3 second elapse at the beginning of a boot. Just read what is on the screen and boot from the recovery image.

After booting you should get a menu. Press down and select fsck to fix your filesystem first since you did an unclean shutdown. However linux should have detected this before and ran the utility but this is just for precaution. If it finds a problem but are not able to fix you usually have to do a manually check. Just drop to a root shell on the menu option. Just to be sure you have to umount the disk. umount is the command. Then you run the fsck command without automatic fix. Remount your file system and type exit to drop back to the menu. Or just type "shutdown -r now" to reboot and go to the recovery menu again.

When you are there you should select fixing X. See if this work first.

---

### Post by jonobr on 2009-06-12
Boxx1993 is there anything major important on your system that would prevent you from reinstalling?
It looks like that may be the best option.

My feeling is that if you manage to get your system working , anytime in the future whan you run into problems, you will always be wondering is it because you had this problem.

---

### Post by Sinkingships7 on 2009-06-12
As a few others have said, removing Python is like removing a card from the bottom of a house of cards. So many applications in Ubuntu depend on it. I'd imagine you're going to have to reinstall the operating system.

---

