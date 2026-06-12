---
title: "Power off problem"
date: 2006-06-10
forum: Desktop Environments
---

### Post by Genesius on 2006-06-10
Running Kubuntu 6.06 on a 1Ghz AMD Duron system, with the latest kernel updates. The weird thing is, when I use the K7 kernel which should be the right one for my processor, the system won't power itself off. It goes through the shutdown process, gets to "will now halt", my keyboard lights flash and it stays there until I hit the power button. However, if I use the 386 kernel my system powers off normally.

Using the 386 kernel isn't a big deal, since I don't see a big performance difference, but I am curious why this is happening. Any suggestions?

---

### Post by Genesius on 2006-06-16
No ideas, huh? Do I get a prize for stumping the forum?   ;) 


Not sure if this has any bearing on the problem, but. . . when I'm notified about new packages and run the updater, my 386 kernel gets included for updating but my K7 kernel doesn't. Is it possible something on the K7 kernel install is messed up & causing the glitch in powering down?

---

### Post by daiwai on 2006-06-16
I have the same problem and none of the solutions posted in other threads worked for me so far.

---

### Post by kinematic on 2006-06-16
for a distro backed by a few million bucks there are a lot of bugs #-o

---

### Post by Culito on 2006-06-19
Hey!
I also have a Duron.  I just tried the k7 kernel, and I also have that problem now.  The system works fine, but does not turn off.

I guess it's just something with the k7 kernel.  Glad to see that no one else knows what's going on!

-C

---

### Post by scxtt on 2006-06-19
i have (had?) the same problem w/ dapper (not breezy) - now it shuts down fine, but i can't restart ... i get "will now restart" and nothing happens ... and if i do it from recovery mode it says "there is no fixup for your hardware" or something like that ... weird!

---

### Post by Genesius on 2006-06-20
Same here - I could shut down fine with the K7 kernel in hoary & breezy, but not dapper. Oh well, guess I'll use 386 for now & see what happens with Edgy Eft.

---

### Post by MetaMorfoziS on 2006-06-20
I have samething similar to this on my father's notebook.
If i press the powerbutton it seems going to shutdown, but sometimes it is going to an odd state, the power led is bright, the mouse [optical] isn't lights, and it isn't ansvers to the powerbutton [boot up!] ... So the only solution for it is if i get off the accumulator and get back... it's brutal...

The solution:
Don't use powerbutton for shutdown. :D

---

### Post by Culito on 2006-06-20
Yeah, Dapper won't shut down with the power button here either, but I forgot about that, since I always use the "door".

---

### Post by forlau on 2006-06-21
Be sure you enabled acpi in your BIOS and modify your /boot/grub/menu.lst and add **apm=on** and **acpi=on** so it looks like this

```
kernel      /boot/vmlinuz-2.6.15-25-k7 root=/dev/hda8 ro quiet splash vga=775 apm=on acpi=on
```

if its still not working try
```
kernel      /boot/vmlinuz-2.6.15-25-k7 root=/dev/hda8 ro quiet splash vga=775 apm=on acpi=force
```

This should solve your problem with shutdown.

---

### Post by Genesius on 2006-06-21
Using acpi=force did the trick! Many thanks!

---

