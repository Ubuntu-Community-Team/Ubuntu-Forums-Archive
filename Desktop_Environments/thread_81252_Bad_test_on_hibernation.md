---
title: "Bad test on hibernation"
date: 2005-10-24
forum: Desktop Environments
---

### Post by jrev on 2005-10-24
Hi all,
I tried a to test the hibernate function on my Hoary desktop by 
System/logout :
my screen went black and I couldn't restore the hibernation 

my questions :
What is the use of the hibernation option ?
How to come off this feature once started ?
I would appreciate your suggestions on that  matter :cool:

---

### Post by jrev on 2005-10-25
Well, let's hope they will cancel the button on the new Breezy, unless they found the bug on the Hibernation recovery ...:cool:
When I start my laptop hibernation the screen turns black but the PC is still on this probably means we are on a RAM hibernation. 
The problem is I cannot come back on my last screen and the only solution seems to cut off the power 
Can we cancel this feature which only brings problems ?...

Thanks for it

---

### Post by nocturn on 2005-10-25
[QUOTE=jrev]Well, let's hope they will cancel the button on the new Breezy, unless they found the bug on the Hibernation recovery ...:cool:
When I start my laptop hibernation the screen turns black but the PC is still on this probably means we are on a RAM hibernation. 
The problem is I cannot come back on my last screen and the only solution seems to cut off the power 
Can we cancel this feature which only brings problems ?...

Thanks for it[/QUOTE]


Yes, but it does work for some users.  Specially those that have laptops which adhere better to the ACPI standards.

I've heard that most Thinkpads hibernate correctly (not sure).

---

### Post by mplexus on 2005-10-25
I'd like to add, hibernation worked fine on my laptop (acer 1524) until i installed the nvidia drivers (restricted package). now it still sleeps ok (on hard disk) but on restore it freezes on the "last step" which is to bring up the X server.

---

### Post by jrev on 2005-10-26
can you tell how you start the restore process ?
Thanks :cool:

I am not on a laptop but on my main desktop computer ..

---

### Post by bb002 on 2005-10-27
I've had this problem too. pressing Alt+Ctrl+f7 seems to work.

f1 - f6 are consoles and each are treated seperately from each other while f7 is where the xserver seems to put itself and is treated seperately like the consoles. Hopefully this help you guys.


I'll admit that I haven't tested this if i with the hibernation command though. I the black screen problem if i ever shut the lid on the laptop to make it go into standby (atleast i think that's what it's doing.) and later open the lid. I'll test it here in a few for the hibernation command.

---

### Post by bb002 on 2005-10-27
Well I got my laptop to go into true hibernation and not just ram hibernation.

after selecting the hibernation command from the log off menu. the screen immediatly goes black and there is a lot of disk activity. Once the activity stopped, my laptop was still on. At this point I tried to restore my laptop, thinking that forcing the power was the only way out. I set about removing the battery. Right before i removed the battery i decided to close the lid and was greeted with another spurt of disk activity, then it powered off. Turned it back on and selected my kernel. Once everything was restored i was stuck with a black screen and alt+ctrl+f7 wasn't working. I had to alt+ctrl+f1 then alt+ctrl+f7 to get my screen to come back properly.

---

### Post by jrev on 2005-10-28
Is there any topic on that subject on the wiki or elsewhere to explain how it should work ?:cool:

bb002 : did you get the same screen back when you started your laptop again ?

---

