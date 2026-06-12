---
title: "Slooooooow interface"
date: 2006-08-26
forum: Desktop Environments
---

### Post by ekymk on 2006-08-26
Hello,
My Unbuntu box is working really slow. I have no idea why is this happening.
Different linux distributions used to run ok. Also Windows XP that is currently runs ok in the same computer. 
I have a Pentium 4 2.2Ghz and 768 MB of memory with another 450MB swap.
The unbuntu version is  Ubuntu 6.06 LTS! and the kernel version is 2.6.15-26-386
I have a very standard and up to date Unbuntu distribution, with some Theme visual effects added to gnome, but the problem is from before i added those effects.

Now i randomly run gps and see many programms that are using as much as they can, it doesn't make much sense.
This is the most memory consuming entries in the process table:
openoffice  170MB
Thunderbird 160MB
XOrg        156MB
Firefox     119MB
(I have also seen a few times adobe acrobat reader consuming huge amounts of RAM, for documents that only contain text).

I know that thats a lot of programms, but it doesn't depend on which programms are opened, it is always the same behaiviour, it depends more on which tasks are running, for example downloading a file, or installing components, or running any other task which continually uses resources will always speed down the whole computer till the task is finished. The mouse pointer can completly stop to respond, or move a few seconds after i move the mouse. These behaiviour doesn't seem logical since the linux process scheduler should give priority to tasks that do user interface rather than tasks that are processor consuming. I have seen this code in the 2.4 kernel, but i am not up to date with the current kernel.

I hope one of you have a solution for this headche,
thank you
Marcelo Taube

---

### Post by mgmiller on 2006-08-27
with your CPU, you might have better luck switching the the 686 kernel.

---

