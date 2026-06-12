---
title: "[SOLVED] What do I do if my scanner isnt supported by sane"
date: 2008-12-07
forum: General Help
---

### Post by Frogster on 2008-12-07
Good evening everybody,

I have a Tiny Fu66ie scanner that I would like to use. However, xsane states that it cant find the device. 

It seems that the scanner isn't supported, what are my options?

---

### Post by aysiu on 2008-12-07
There are basically two options.

**Option 1**
Use Windows

**Option 2**
Sell your scanner on eBay
Find a compatible scanner [here](https://wiki.ubuntu.com/HardwareSupportComponentsScanners)
Buy that scanner

---

### Post by Frogster on 2008-12-08
Thank you aysiu. I had thought those were the only options.

**Hmmm** I have heard about this windows OS, is it any good?.....

---

### Post by howefield on 2008-12-08
There might be a third option :p

Is your scanner a USB scanner ? if so you might be able to set it up in a windows virtual machine using something like Virtualbox.

I am assuming that you don't use the scanner heavily, so loading up a VM when you do want to use it might be acceptable ?

---

### Post by Frogster on 2008-12-08
Good thought, I shall ponder that one :p

---

### Post by theozzlives on 2008-12-08
get VirtualBox at [http://www.virtualbox.org]("http://www.virtualbox.org")

---

### Post by Zimmer on 2008-12-08
Ponder also that the USB layer via Virtual Machine is not necessarily 'good' (in my limited experience).

I have a hardly used AGFA 1200p scanner gathering dust, was 6 months old when I bought a new XP machine(@2002), which did not support the scanner. No drivers, ever, released for it on XP....  none in SANE either... so it will only work using W95 or W98..
... you are not alone and it also illustrates that hardware issues are often rooted in the manufacturer's ability/willingness  to write driver software or release specs so that other people can try...

---

### Post by cmay on 2008-12-08
> **Frogster said:**
> Good evening everybody,

I have a Tiny Fu66ie scanner that I would like to use. However, xsane states that it cant find the device. 

It seems that the scanner isn't supported, what are my options?
i have a new prnter with scanner trhat also is not found by sane. but i found out ther is a package that is called sane utils and some other sane extra packages in synaptic that should work as a backend - as i understand it. could you try out to see if that is true and maybe get it too work. 

i have already traded my new printer so when i did some reading on this subject i found out i may not even have had to trade the device as it could have been apackage that needed to be intalled. maybe if it is like that it could help others. 
i went for a new printer with no scanner in it since i do not need it so its not something that means the whole world to me but if it means something to others it could be great if you could figure it out :).  
thanks.

---

### Post by Frogster on 2008-12-08
> **Zimmer said:**
> Ponder also that the USB layer via Virtual Machine is not necessarily 'good' (in my limited experience).

I have a hardly used AGFA 1200p scanner gathering dust, was 6 months old when I bought a new XP machine(@2002), which did not support the scanner. No drivers, ever, released for it on XP....  none in SANE either... so it will only work using W95 or W98..
... you are not alone and it also illustrates that hardware issues are often rooted in the manufacturer's ability/willingness  to write driver software or release specs so that other people can try...

I came across this problem with Agfa scanners while trying to find an answer to my problem.  

I think the scanner is going to be attached to an xp machine, it seems the far more sensible course of action to take. Hopefully, I can find an xp driver.

Thank you for your reply

---

