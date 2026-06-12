---
title: "Mounting Root FileSystem"
date: 2006-07-22
forum: Desktop Environments
---

### Post by rekahsoft on 2006-07-22
I am experiancing a wierd little problem that i just can't figure out...ok...i installed Ubuntu dapper LTS on my brothers desktop and for some reason when i go to boot it it boots up but on the next boot it can not mount the root file system. The only reasons i thyink of why this might be happening is because on shutdown it is not unmounting properly, or the hard drive is flakey. What is the problem?

---

### Post by taurus on 2006-07-22
It also could be that an entry for kernel in /boot/grub/menu.lst is pointing to a wrong directory for your / partition!!!  So, boot the desktop CD (also a LiveCD), mount your /boot (if you have a seperate /boot.  Otherwise, mount / somewhere then) and have a look at your /boot/grub/menu.lst.  Or turn on your machine and at the GRUB prompt, hit e and edit your menu.lst...

---

### Post by rekahsoft on 2006-07-22
ok i will give it a try...thanks for the help :)

---

### Post by taurus on 2006-07-22
> **rekahsoft said:**
> ok i will give it a try...thanks for the help :)
Good luck.

---

### Post by rekahsoft on 2006-07-22
Ok...got some problems...i was dumb and changed my grub.lst file...i changed the root=/dev/hda1 and (hd0,1) when it should be (hd0,0) :'( now it doesn't boot...btw...i am in the live disk now and it had the same problem...when i rebooted i had to turn the computer off because it stopped when mounting root. have mounted / in the live cd but in /boot theire is no grub??? so i can't edit /boot/grub/grub.lst...how do i do it?

---

### Post by taurus on 2006-07-22
How did you partition your harddrive?  Do you have one for /, one for /boot, and one for swap or you have only two partitions: / & swap.

Open a terminal (Applications -> Accessories -> Terminal) from the LiveCD and paste the output of this command here...

```

sudo fdisk -l

```

---

### Post by rekahsoft on 2006-07-22
ok...i was just dumb there for a sec and tried to mount my / over the tmp root made by the live disk...anyway i changed the /boot/grub/menu.lst back to the way it was (i made a backup before)...it is wied tho because it is doing the same thing with the live disk as it is with the normal install??? Wouldn't that automaticy mean hardware? because the live dist does not read the boot infor from my installed copy...thanks so far :)

---

### Post by rekahsoft on 2006-07-22
hmm...i am stumped...the partitioning is fine...everything boots but it is still not booting everyother time...i will explain in the most possable detail:

First when i turn the computer on it starts loading until it gets to the "mounting root file systems" part where it freezes...then i turn the computer off then back on again and it boots fine.

---

### Post by taurus on 2006-07-22
How long did you wait when it gets to "mounting root file systems"?

---

### Post by rekahsoft on 2006-07-22
I have waited 10 minuites...other times it takes just seconds...here i will give it a try again :)

---

### Post by rekahsoft on 2006-07-22
There...just tried..same results...what is going on?

---

### Post by diablozx9 on 2006-07-29
I have always had the same problem.
I cant help fix it,,, but, i live with it.

---

### Post by zek725 on 2006-08-06
count me in!

---

### Post by rekahsoft on 2006-08-06
ok..what hardware are you guys running? Have you tried other distros? if so what are the results?

---

### Post by Kodiak3000 on 2006-08-07
Hey, 
I'm having a very similar problem.  I installed this from a burned CD, and it's worked great for a week.  Starts up every time.  

Suddenly this morning it freezes at Mounting Root File System. Gets there, then nothing.  Did that twice in a row, and now I've restarted it again, it's frozen at "Uncompressing Linux... Ok, booting the kernel."

So what's up with THAT?

I've already done quite a bit of work on this machine, and like an idiot, don't have any of it backed up, so any help will be most appreciated!

---

### Post by pppetter on 2006-08-07
Okey. This is how it goes...After a certain number of boots, the system automatically checks your filesystem for errors. I don't remember how many boots we are talking about. So depending on how big your harddrive is...the larger - the longer time you'll have to wait.

Is this possibly what happened to all of you guys?

---

### Post by Kodiak3000 on 2006-08-07
well mine's 300GB and I think I probably rebooted a total of maybe 10 times...

---

### Post by rekahsoft on 2006-08-07
> **pppetter said:**
> Okey. This is how it goes...After a certain number of boots, the system automatically checks your filesystem for errors. I don't remember how many boots we are talking about. So depending on how big your harddrive is...the larger - the longer time you'll have to wait.

Is this possibly what happened to all of you guys?I know for a fact that my fs is fine...and it was not doing checking because it was doing this from the start...i would turn it on and the root fs wouldn't mount...then i would turn it off and on again and it would boot fine...Maybe it is because the hd is in auto mode...and auto is messed up...i will check today and report back...it is surely not software tho.

---

### Post by rekahsoft on 2006-08-07
Hey Kodiak3000, i think what pppeter might be right for your little problem...have you been messing with any boot files like /boot/grub/menu.lst or any other file like that?

---

### Post by rekahsoft on 2006-08-08
I think i have found the solution to my problem...i still have to try it out but this is the idea...i am thinking that auto detection on some hd's does not work properly and because of this it boots in a pattern: Slave, Master, Slave, Master, etc... This would make sence because ubuntu can only mount the root fs off a properly set-up hd. That is why it works every second time. Anyway I have not slept all night so when i wake up i will report what i have found after testing my theory.

---

