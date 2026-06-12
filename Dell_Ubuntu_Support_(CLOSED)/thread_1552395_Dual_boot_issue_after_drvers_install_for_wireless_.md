---
title: "Dual boot issue after drvers install for wireless card"
date: 2010-08-13
forum: Dell Ubuntu Support (CLOSED)
---

### Post by rajan.salgaonkar on 2010-08-13
Hello,

I recently purchased DELL 15R laptop with Windows 7 installed. I installed Ubuntu10.04 as a dual boot option on it. I tried getting in and out of Windows and Ubuntu a couple of times after the installation and it was good. 

After a while I realised that wireless card was not getting detected on Ubuntu and probably thought it was missing the drivers for the wireless card. I did 

[COLOR=#009900]apt-get update
[/COLOR][COLOR=#009900]apt-get update

There was no change in the wireless detection and after I logged into Windows and restarted the box, I see no dual boot options. There is some error on the screen which seems to pertain to the wireless driver update. Using the Ubuntu CD I used the 'Try without Installation' to get into and tried restoring the grub by doing some Google for grub restore. But that did not help. So finally I installed Ubuntu again on the same partitions as ealier. After the reinstall, the grub seemed to have restored and I could get into Windows. However once I restarted the box, I was back to square zero, same issue. 

I am not a very sophisticated Unix/Linux user. I am not sure what do I need to do to get things in place again. 

It would be really great if you could provide some help and insights to overcome the problem. I will try to add more h/w info and preice error message once I get back home.
[/COLOR]

---

### Post by deerjoe on 2010-08-14
Is that real?because of de1l wireless drivers?
Seem I have same issue in my 1464

I found that I can't see the Grub2 interface,it directly access into ubuntu.
And the computer can not find the other system. No matter i used "sudo update-grub" command or use the Win7 DVD,I still can't find the Win7 boot.it also happend when i trying to install Mac ox Snow leopard.p.s.:Win7 still in my hard disk.But,Only i can use it when i reinstall Win7.

---

