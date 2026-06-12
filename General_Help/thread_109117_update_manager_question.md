---
title: "update manager question"
date: 2005-12-27
forum: General Help
---

### Post by briancurtin on 2005-12-27
i just reinstalled and the first thing i did was get the 686 kernel, but the update manager keeps bothering me with the updates for the 386 kernel.

if i run these updates, it wont harm the 686, but will that then make the 386 my default kernel at boot time? not sure why im thinking this, but i am for some reason.

---

### Post by anil_robo on 2005-12-27
I'm a non-programmer and non-geek, but I have a little suggestion.
Perhaps you could write a script to select the 686 kernel at bootup? And put it in init.d directory?

On the other hand, why do you use the 686 kernel in the first place? Just curious! :)

---

### Post by briancurtin on 2005-12-27
[QUOTE=anil_robo]On the other hand, why do you use the 686 kernel in the first place? Just curious! :)[/QUOTE]
P4 hyperthreaded processor
i was just suggested to use it once and it has run smoother than the 386 kernel did

maybe i shouldnt be using it, but its never done me wrong. does anyone have a strong reason why i shouldnt be using it? i dont remember the reason, and it wasnt on this board, but i was just told to try that out and it worked a bit smoother

---

### Post by az on 2005-12-27
Yes, 686 is better.  No, a script would not work.  For you to run a script, the kernel would have to already be in place ages ago.

It should not make it the defualt kernel if it is installing anupdate - and update does not update grub.  You may remove the linux-image-386 packages if youare running fine with the 686 ones.

---

