---
title: "Login Problem / Disk Space"
date: 2006-04-09
forum: Desktop Environments
---

### Post by msandersen on 2006-04-09
I've been testing Ubuntu on an old 500Mhz machine with a 10Gb drive, half of which is Win XP. Only 3Gb for the system with the rest for /home and swap.

I've installed a few things starting with Automatix; it takes a helluva long time to download it all. 

In any case, after it popped up a message suggesting I update some files, which was the Kernel, I let it, a fairly chunky download. Well, they installed fine as far as I know. On restart, apart from having messed with my menu.lst setup (no Windows or bootsplash), I got the infamous "*Your session only lasted less than 10 seconds*" error which I've read about here, and the error message does indicate space being the problem. The fact that Linux fails to login in such a case is pathetic, but that's besides the point. Knoppix's qtparted told me there was a bit of space, though not a lot.
I used Ctrl+Alt+F1 in Ubuntu and freed a couple of megabytes by using **rm *12-10-686** in the /boot dir and edited the menu.lst accordingly; maybe not the best way, but I know no better. The point is, it still doesn't recognise that there's free space. Knopix now reports **2.85Gb** of **3.00Gb** used. And yet, using **df** in Ubuntu reports 100% used. 
What gives, why does Ubuntu not recognise the free space and allow login? Not even man pages work on the terminal, since they are gzipped and require space to unzip.
This is only a test machine, and if not for bloody Automatix and the imminent Dapper release, a reinstall would be a relatively easy but bad solution. Knowing how to let it recognise the free space would be better.

---

### Post by localzuk on 2006-04-09
You could try deleting the temporary files in /var/cache/apt/archive/ - this is where the .deb files are downloaded to when you use apt.

---

### Post by Ramses de Norre on 2006-04-09
sudo apt-get clean
I think rm'ing /tmp/* wont do no harm neither but I'm not sure.

---

### Post by msandersen on 2006-04-10
[QUOTE=Ramses de Norre]sudo apt-get clean[/QUOTE]
That did the trick, cleared up some 460Mb, presumably mostly from Automatix. Why does it keep a copy of the deb files anyway? For uninstallation, it presumably keeps a database.
Mind you, on Windows, I usually keep a copy of the installers for future use, but this is an automatic process and hidden deeply in th directory tree. Another thing I worry about over time is log buildup, as I don't know where they all are. 

There wasn't much in the tmp dir so not worth worrying about. When I gt the money, may get a decent hard drive for this thing and use it as a download server or the like. Needs a graphics card, too, Gnome is damn slow compared to Win XP or even KDE.

As a side note, for my Linux knowledge I rely on an ancient Idiot's Guide picked up at a book sale years ago; it comes with Caldera OpenLinux 1.3 no less! It says it "uses a standard 2.0.35 Linux kernel. It also includes other unique features, making OpenLinux the most reliable and easy-to-use Linux available". Hmm, wonder how they're doing now and if they've furthered the cause on Linux :)

---

### Post by localzuk on 2006-04-10
It keeps a copy in order to allow you to re-install without having to download the apps again (re-install the apps, not the OS).

Logs are kept in /var/log.

Well, Caldera was purchased by SCO a while back - and now doesn't exist... The company is focusing on trying to sue anyone they can at the moment. So they aren't doing too well.

---

