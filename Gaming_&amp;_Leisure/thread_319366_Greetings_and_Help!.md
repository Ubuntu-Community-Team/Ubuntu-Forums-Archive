---
title: "Greetings and Help!"
date: 2006-12-15
forum: Gaming &amp; Leisure
---

### Post by yange on 2006-12-15
Hey all, first off, I'm a new ubuntu user. My first time on Linux and I looks look I'm getting the hang of this. Well anyways, I'm trying to install WoW, and when Install wine, after downloading/extracting from the terminal, this guide says to ./configure.
When I do I get this:

yange@yange-desktop:~/downloads/wine/wine-0.9.25$ ./configure
checking build system type... i686-pc-linux-gnulibc1
checking host system type... i686-pc-linux-gnulibc1
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
See `config.log' for more details.

Any ideas on what to do?

---

### Post by Shatrat on 2006-12-15
If you enable universe and multiverse repositories in your /etc/apt/sources.list or using the synaptic sources tool you can install it using synaptic or by typing sudo apt-get install wine
Installing from source isn't very beginner friendly, but for future reference you need a compiler and other goodies to do that.  You can get those with sudo apt-get install build-essential

---

### Post by reiki on 2006-12-15
yes.... stop what you're doing. There should be no need for you to compile Wine any more.

It is helpful if you create a signature on the message boards here that lists important data about your machine. What graphics card are you using? Which Ubuntu version are you using? 

If you go to WineHQ.com ... specifically to:

[http://www.winehq.com/site/download-deb](http://www.winehq.com/site/download-deb)

You will get great instructions on how to add the repositories to get Wine and install it using either Synaptic or apt-get from the command line. 

This will make your life much easier. :)
As with many things, it will be important for anyone trying to help you, to know what graphics card you have. Instructions for dealing with ATI cards are different at times from those instructions you would get for nVidia cards.

---

### Post by predaeus on 2006-12-15
another friendly tip:
Try to chose thread titles that are more specific to your problem, like "Problem configuring wine" instead of the very general "Greetings and Help!". This will cause more people who know about the specific topic to read that thread and look if they can help. No harm done. Just pass those tips on and help where you can ;)

---

### Post by hikaricore on 2006-12-15
> **reiki said:**
> yes.... stop what you're doing. There should be no need for you to compile Wine any more.

It never hurts tho, they all have to learn sometimes.  So it's not cultureshock when someone comes across a great app with no debian/ubuntu package.

---

### Post by yange on 2006-12-16
Thank you all, I've had a long night since I posted this and I just woke up. So when I'm more coherent, I will reply to all your threads and try your solutions out. But for now I rest :P. Okay, thanks again all, bbl.

---

