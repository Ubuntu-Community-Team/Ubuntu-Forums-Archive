---
title: "What is the best Dell laptop with an easy Ubuntu install?"
date: 2010-09-25
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Mr.Ink on 2010-09-25
Hola, 
 
Im so new to Ubuntu that I have yet to purchase my Dell and get my Distro due to the fact that as I go throughout the Forum I see all these problems. I was strongly thinking of buying the 15R. But I have seen some posts about "grub" well like I said Im new so I don't know what that means yet. **So my question is what is the best Dell for noobs? My price range is 700 to 800. I want a smooth transfer.**
 
Much Thanks in advance.... 
 
 
PS - My first post here

---

### Post by mrhhug on 2010-09-25
what are you trying to do with the laptop? Most of the new dells are going to work flawlessly with ubuntu. here are laptop prebundled with ubuntu: [http://www.dell.com/content/topics/segtopic.aspx/ubuntu?c=us&cs=19&l=en&s=dhs&~ck=anavml](http://www.dell.com/content/topics/segtopic.aspx/ubuntu?c=us&cs=19&l=en&s=dhs&~ck=anavml)

grub is a bootloader, it usually used when you want to dual boot 2 operating system on the same computer see: "http://ubuntu-tutorials.com/2006/12/29/tweaking-grub-ubuntu-510-6061-610/"

hope this helps

---

### Post by CoolJohnB on 2010-09-25
I have a Dell Vostro 1700 and 3700 and found it very easy to install Ubuntu on both of them, everything is automatic, much easier than Windows!

I don't have any other operating system on either laptop.

---

### Post by Rinzwind on 2010-09-25
> **Mr.Ink said:**
> Hola, 
 
Im so new to Ubuntu that I have yet to purchase my Dell and get my Distro due to the fact that as I go throughout the Forum I see all these problems. I was strongly thinking of buying the 15R. But I have seen some posts about "grub" well like I said Im new so I don't know what that means yet. **So my question is what is the best Dell for noobs? My price range is 700 to 800. I want a smooth transfer.**
 
Much Thanks in advance.... 
 
 
PS - My first post here

The brand is not the issue. It is the contents of the machine: just get one with a nVidia card and not an ATI. 

I had a 9300i and currently working flawlessly with Ubuntu and have an Inspiron 1720 and it works perfect on Meerkat too.

---

### Post by Mr.Ink on 2010-09-25
> **mrhhug said:**
> what are you trying to do with the laptop? Most of the new dells are going to work flawlessly with ubuntu. here are laptop prebundled with ubuntu: [http://www.dell.com/content/topics/segtopic.aspx/ubuntu?c=us&cs=19&l=en&s=dhs&~ck=anavml](http://www.dell.com/content/topics/segtopic.aspx/ubuntu?c=us&cs=19&l=en&s=dhs&~ck=anavml)
 
grub is a bootloader, it usually used when you want to dual boot 2 operating system on the same computer see: "http://ubuntu-tutorials.com/2006/12/29/tweaking-grub-ubuntu-510-6061-610/"
 
hope this helps
 
Thanks, but I want to learn to program perl and/or Python. And just learn Linux period. So if I dont dual boot will I need a grub? Ooh and I seen those before but I read about a lot of upgrading problems.

---

### Post by Rinzwind on 2010-09-25
> **Mr.Ink said:**
> Thanks, but I want to learn to program perl and/or Python. And just learn Linux period. So if I dont dual boot will I need a grub? Ooh and I seen those before but I read about a lot of upgrading problems.

Grub is 'always' there but you can hide it by setting it to a timeout of 0. It's a failsafe thing: when you have trouble booting or your system crashed for whatever reason it will pop up giving you to the option to start the machine normally or go into fail-safe mode or any other mode that might help you sort out a problem that (for instance) might stop you from logging in.

Gnome is seperate from the kernel so you can fix gnome from the prompt if you can not get into Gnome (if you know where to look of course ;) ).

---

### Post by TBABill on 2010-09-25
My Dell 1564 with Intel Core i3-330m and using the on-chip GPU works flawlessly in Ubuntu. The only think you have to do after install is plug into a router to download updates and install the proprietary Broadcom driver. No way around that, but it's simple.

Note: Once Ubuntu moves up to the 2.6.37 kernel (currently 2.6.32 but 10.10 will use the 2.6.35), the Broadcom driver will be built into the kernel and no extra steps will need to be taken to use the machine after install.

---

### Post by undfined on 2010-09-28
[http://www.dell.com/content/topics/segtopic.aspx/linux_3x?c=us&cs=19&l=en&s=dhs](http://www.dell.com/content/topics/segtopic.aspx/linux_3x?c=us&cs=19&l=en&s=dhs)

A black 15n build with 4 GB memory, HD graphics, 250 GB hard drive, 9 cell battery, and 30 days support comes in at $709 for me this evening.  Unless you are installing another operating system then I can't imagine any reason for grub to complain.

My 1420n works out of the box with Ubuntu 10.04 and has for years.

---

### Post by Mr.Ink on 2010-09-28
> **undfined said:**
> [http://www.dell.com/content/topics/segtopic.aspx/linux_3x?c=us&cs=19&l=en&s=dhs](http://www.dell.com/content/topics/segtopic.aspx/linux_3x?c=us&cs=19&l=en&s=dhs)
 
A black 15n build with 4 GB memory, HD graphics, 250 GB hard drive, 9 cell battery, and 30 days support comes in at $709 for me this evening. Unless you are installing another operating system then I can't imagine any reason for grub to complain.
 
My 1420n works out of the box with Ubuntu 10.04 and has for years.
 
 
 
 
So this 15n is great out of the box? Im trying to avoid discouragement. haha I want to put the lastest version of Ubuntu on it which is coming out in about 12 days I think. And this is a great price.

---

### Post by roddie on 2010-09-28
I assume your budget is listed in US$, since I'm in the UK I don't know how well it will translate to your price range, but secondhand Latitude D620's and D630's can be had cheap and (with the nVidia) both seem to run Ubuntu 10.04 perfectly.

---

