---
title: "Run Ubuntu and Windows Simultaneously?"
date: 2006-07-27
forum: Desktop Environments
---

### Post by miikkee on 2006-07-27
Dear people of the world, 

I have a dual boot on my work machine. Windows + Ubuntu. Because I need to run different applications, some on windows and others with Ubuntu... I am wondering if it is possible to actually run Windows and Ubuntu at exactely the same time... And switch to one another with a command rather than rebooting all the time... Let me know if it is possible or if I am totally loosing my mind... Thanks... 

Mick The Ouf

---

### Post by aysiu on 2006-07-27
With VMWare, you can "install" and use Ubuntu within Windows or use Windows within Ubuntu.

If you purchase Crossover Office, you can run most Windows applications in Ubuntu. If you use Wine, you can run some Windows applications in Ubuntu.

What are your Windows-only applications?

---

### Post by miikkee on 2006-07-27
I use mostly microsoft access and PATRAN (finite element software) on windows.

So I guess the answer is negative right? It is not possible to run them simultaneously??? 

Mick The Ouf

---

### Post by kpkeerthi on 2006-07-27
Since you are dual booting, there is no need to install windows on top of VMware. There is an option to boot windows from the installed partition on top of VMWare. There's a HowTo in the HowTos forum.

---

### Post by aysiu on 2006-07-27
> **miikkee said:**
> I use mostly microsoft access and PATRAN (finite element software) on windows.

So I guess the answer is negative right? It is not possible to run them simultaneously??? 

Mick The Ouf
No, the answer is that you would need one of these...

1. VMWare
2. Two computers
3. Crossover Office, Cedega, or Wine

---

### Post by aysiu on 2006-07-27
> **kpkeerthi said:**
> Since you are dual booting, there is no need to install windows on top of VMware. There is an option to boot windows from the installed partition on top of VMWare. There's a HowTo in the HowTos forum.
If you find that, could you link to it? I've seen only HowTos that actually have you install Windows...

---

### Post by miikkee on 2006-07-27
OK OK, 

Yep that'll be cool if I don't have to reinstall windows and directly can access to my windows desktop... I checked a bit... could find it... will check more... 

The Ouf

---

### Post by SigmaX on 2006-07-27
qemu is a nice alternative to VMware.  I use it without much of a hiccup.  Love it.

SigmaX

---

### Post by miikkee on 2006-07-27
How do I install and setup QEMU ? Thanks

---

### Post by jimmygoon on 2006-07-27
Buy an overpriced Macbook and put parallels on it

---

### Post by miikkee on 2006-07-27
Lol

---

### Post by jISh on 2006-07-27
VMWare works great. You install Windows (and almost any other OS) to a file that's treated as an entire hard drive. You can have it open just like any other application. Works with all hardware that Ubuntu supports.

Search for forums for "Windows XP VMWare", there's a real good guide to doing it floating around. I have Media Center 2005 installed and working perfectly, it even streams to my Xbox 360!

---

### Post by SigmaX on 2006-07-28
> **miikkee said:**
> How do I install and setup QEMU ? Thanks

```
sudo apt-get install qemu
```

A basic howto, including kernel-level acceleration, can be found [here]("http://lumumba.uhasselt.be/takis/howto/qemu.html#id2451139").  Other resources are readily available with Google.

If you prefer VMware go for it.

SigmaX

---

### Post by Peturrr on 2006-07-28
Howto about installing windows inside Ubuntu in VMWare => [http://ubuntuforums.org/showthread.php?t=183209](http://ubuntuforums.org/showthread.php?t=183209)

You can run Windows simultaneously with Ubuntu with this guide. I didn't cover running an existing windows inside of ubuntu, but there are some people who tried that, you can search for that in the replies.

---

### Post by MTZeon on 2006-07-28
Hum... now here's a new concept... Imagine a GRUB that would boot two different (or more! Hell why not?!) OS's, Windows and Ubuntu, and you just had to press a key combo to change from desktop to desktop?! Like that, we would have both OS's running at native speed!

---

### Post by bluenova on 2006-07-28
> **MTZeon said:**
> Hum... now here's a new concept... Imagine a GRUB that would boot two different (or more! Hell why not?!) OS's, Windows and Ubuntu, and you just had to press a key combo to change from desktop to desktop?! Like that, we would have both OS's running at native speed!
And both of them in Memory :D

---

### Post by frup on 2006-07-28
you mean like VMware becomming a semi standalone OS and acting as grub where you open your virtual machines from?

---

### Post by ravindran.k on 2006-07-28
Was wondering about the Hardware you've got:confused: 
 
In order to Use any emulator .. U need to have good amounts of RAM.. I have a PIII 450 Mhz and 640 MB RAM. So can run Windows and Linux somewhat satisfacotirly  together.. Ofcourse ..using VMWare..but switching to QEMU sooon!!!:D

---

### Post by miikkee on 2006-07-28
I didnt see anybody having succes by using the already installed windows with VMWare. Is it possible with QEMU?  

:confused: :KS :?: :rolleyes:

---

### Post by SigmaX on 2006-07-28
> **miikkee said:**
> I didnt see anybody having succes by using the already installed windows with VMWare. Is it possible with QEMU?  

:confused: :KS :?: :rolleyes:

Not that I know of.  QEMU emulates a specific set of hardware, so it would by like ploppying your Windows HD in another computer and hoping it *just works.*

SigmaX

---

### Post by dubbreak on 2006-07-28
> **SigmaX said:**
> qemu is a nice alternative to VMware.  I use it without much of a hiccup.  Love it.

SigmaX

I've used qemu under windows to run linux/bsd and it's great. Just make sure you have enough memory.

[qemu home]("http://fabrice.bellard.free.fr/qemu/")

Easy to install, then you will just need an image file.

A quick google gave me this for images:
[http://free.oszoo.org/download.php]("http://free.oszoo.org/download.php")

---

### Post by SigmaX on 2006-07-28
Or you can use qemu-img to create a blank one and install an OS from disks you have.  Leastwise that's what I usually do.

Anywho.

SigmaX

---

