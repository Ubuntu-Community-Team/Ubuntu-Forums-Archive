---
title: "Using apt-get without Internet"
date: 2006-06-28
forum: Desktop Environments
---

### Post by tonyr1988 on 2006-06-28
I need to use apt-get to retrieve some stuff to get my winmodem working (as per some tutorials on this site). The problem is....my modem doesn't work, so I can't apt-get them.

I need to get build-essential and the Kernel headers onto my local machine. I have Internet access through XP (I'm dual-booting on one desktop).

Options?

---

### Post by Raistlin355 on 2006-06-28
There may be a better way, but what I did when my internet went out was make a cd with all the stuff I needed at a friends house then added the cd as a repository in the synaptic manager then you can use apt-get cause it will only see the cd as an active source.

---

### Post by tonyr1988 on 2006-06-28
The problem is...no one around here has broadband Internet (I hate it in this town...I can't wait to move for college :D), so everyone's stuck with dial-up (winmodems!) which won't work.

I found this:

[http://archive.ubuntu.com/ubuntu/pool/main/b/build-essential/](http://archive.ubuntu.com/ubuntu/pool/main/b/build-essential/)

But:
1) 10, 11.1, or 11.2? I'm assuming 11.2. Is that right?
2) I have an AMD 500 MHz processor. Which one do I want (AMD64, i386, PowerPC, or SPARC)????

---

### Post by bartbes on 2006-06-28
1) Don't now but the newest (stable) is almost every time the best
2) it's an i386 ( i386 versions are for every x86 processor(s), AMD 64 is 64bit, PowerPC is Apple, Sparc :confused: )

---

### Post by Raistlin355 on 2006-06-28
I would go with 11.2, you'll want i386 for x86 processors

BTW my post earlier was a little vauge, I don't know how much experience you have but you get to Synaptic Package Manager by going to
System-Administration-Synaptic Package Manager then
Settings-Repositories then
Add Cd-Rom

What I don't know is if the packages have to be renamed or in a certain format (ie different folders and subfolders) since I have done that (and haven't had to do it again) I feel like I just got lucky in finding a solution, so if you find that you had to do something extra instead of just throwing programs on disc please let me know.

---

### Post by tonyr1988 on 2006-06-28
I ran the Kernel-headers and it said it's done (YAY).

Build-essential is a different story. When I opened it to install, it told me I was missing dependencies:

"Dependency is not satisfiable: libc6-dev|libc-dev"

I found a libc6-dev (I couldn't find libc-dev), and it told me that I needed the dependency libc6. I found libc6, downloaded (I moved all these via JumpDrive), and it told me that it had already been installed. I re-installed and tried libc6-dev, and it still says I'm missing libc6.

I'm so lost. I just want "make" and "make install" to work. :'(

---

### Post by Etoile on 2006-06-28
If you have internet through XP, I suggest noting what packages you need to install and going into XP to get them, then mounting your XP drive in Ubuntu so you can access them.  That's what I did last night when I had a similar problem.

---

### Post by leech on 2006-06-28
I would suggest an alternate route to all of this.  Buy a real modem?  I mean I know winmodems work as a modem, but I'm talking a good old fashioned Hardware Data Modem.  You can get one for about $20.  [http://www.gearxs.com/gearxs/product_info.php?products_id=3464](http://www.gearxs.com/gearxs/product_info.php?products_id=3464)

Yes, I know for a fact this modem works in Linux and Ubuntu in particular because I've tested it myself.  

If people stop buying those crappy software modems, maybe manufacturer's will stop selling them.

Leech

---

### Post by tonyr1988 on 2006-06-28
The only problem is that I'm moving off to college in about a month, and I won't need a dial-up modem anymore. Once you work in shipping time, I don't think it's worth the $20.....

I wasn't sure if there was a simple, run-and-work script for the winmodem. I can just wait to access the Internet until I get broadband....

---

