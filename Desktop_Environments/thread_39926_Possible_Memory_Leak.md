---
title: "Possible Memory Leak?"
date: 2005-06-07
forum: Desktop Environments
---

### Post by ]SK[ on 2005-06-07
I cant use Ubuntu at all on my laptop.  It works fine for about 2 minutes before not responding to any mouse clicks.  The fan also kicks in which makes me believe that CPU is now running at full load.  I cant do anything at this point other than switch it off.  I first thought I had broken my users profile somehow in Gnome so created a new user and deleted my old one.  Still no luck.  Any ideas on what this is or at least what I can try?

HP Compaq nx9000

---

### Post by zAo on 2005-06-07
Which kernel do you use? What happens when you enter Single User mode?
What CPU do you use? It looks like a Hyperthread-problem (with 686-smp kernels)

---

### Post by ]SK[ on 2005-06-07
[QUOTE=zAo]Which kernel do you use? What happens when you enter Single User mode?
What CPU do you use? It looks like a Hyperthread-problem (with 686-smp kernels)[/QUOTE]

Kernel - 2.6.10-5-386

but I have no idea about single user mode?

I dont believe the P4 in this laptop has HT.

---

### Post by nocturn on 2005-06-07
[QUOTE=']SK[']I cant use Ubuntu at all on my laptop.  It works fine for about 2 minutes before not responding to any mouse clicks.  

HP Compaq nx9000[/QUOTE]

Do you have an Nvidia card,  If so I think the problem is the nvidia driver and Xorg, which would account for the CPU load...

---

### Post by ]SK[ on 2005-06-07
[QUOTE=nocturn]Do you have an Nvidia card,  If so I think the problem is the nvidia driver and Xorg, which would account for the CPU load...[/QUOTE]
 ATI Radeon IGP 340M

Apparently

---

### Post by zAo on 2005-06-07
[QUOTE=']SK[']Kernel - 2.6.10-5-386

but I have no idea about single user mode?

I dont believe the P4 in this laptop has HT.[/QUOTE]
Ok. The kernel shouldn't be the problem. 
You can boot singleuser by typing 'e' when Grub shows up and edit the line with you kernelname (mostly the second line). Put an space and an 'S' (capital) at the end of the line. Now boot this config.

Show us some information of /var/log/messages and /var/log/Xorg.0.log

---

### Post by ]SK[ on 2005-07-01
Didnt know I had a reply after my last post.  

Anyway only today I thought I would try something.  My laptop runs on 256Mb of RAM and shares 64Mb of it with the Video Card.  I did'nt think my laptop really needed to steal all that memory so I put it down to 8Mb.  Today I changed it back to 64Mb and I am now typing this message from Ubuntu!  Ive just ordered another 512Mb RAM as 256Mb is so slow in Windows XP.  Thanks for the replies anyway.

---

