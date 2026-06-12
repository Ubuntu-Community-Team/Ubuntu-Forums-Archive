---
title: "VMWare questions"
date: 2009-06-05
forum: General Help
---

### Post by feardotcom on 2009-06-05
Hello all,
     Thanks in advance for reading. I have a few questions I'm sure someone on this forum can answer. I was curious, if i install VMWare it installs a copy of one my windows CD's, even if its windows 98 (which its not) or how does it work. Is it like VMWare Fusion? In the sense that it creates a separate file for the operating system and NOT a separate partition? How is the performance? Is it well enough to run Visual Studio? Can it play games as well?  Last question, are there any free alternatives to VMWare?

Thanks again,
And I'm not new to Ubuntu, just VMWare

MY soon to be PC specs: (if anyone wants to know; i ordered it today)

AMD Phenom II X4
GIGABYTE GA-MA770T-UD3P
4GB DDR3 1333
GeForce 8800GTX

---

### Post by .nedberg on 2009-06-05
Have a look at this thread: [http://ubuntuforums.org/showthread.php?t=973756](http://ubuntuforums.org/showthread.php?t=973756)

VMWare or VirtualBox will both create a file with your virtuall machine. No extra partitions on your disk.

I use VirtualBox. I don't recommend the version in the repositories as it doesn't have USB support. Get it from [http://www.virtualbox.org/](http://www.virtualbox.org/) instead.

VMWare Server is free also.

---

### Post by feardotcom on 2009-06-05
How good is the performance? Does it perform well enough to runs games and/or development software? e.g. Virtual Studio?

I have some programming classes in a few quarters that is going to require C# and VB 2008.

---

### Post by .nedberg on 2009-06-06
Games? Probably not with VirtualBox, give VMWare a try, but I don't think it will be great.

Visual Studio? Never used it so I can't say for sure. But I see no reason why it shouldn't work just fine.

Install VirutalBox or VMWare and make a XP or Vista VM. Make a snapshot and play all you want, if you ruin something revert to the previous snapshot!

---

### Post by hyperdude111 on 2009-06-06
Games - Not really, there is very limited graphics support in a virtual machine.

However most apps will work, itunes, ms office ect. I recommend virtualbox, it offers better performance and its free unlike vmware.

---

### Post by noob707 on 2009-06-06
Give wine a try. [www.winehq.org](www.winehq.org)

It runs windows programs inside linux. Look at the appdatabase on their to see how visual studio runs in wine.

Also, if you cant get visual studio to run, try code::blocks. It's and IDE like viusal studio and they have a linux and windows edition. I used code::blcoks for C++, but it supports C, LUA, Java and some other scripting languages.

---

### Post by .nedberg on 2009-06-06
> **noob707 said:**
> Give wine a try. [www.winehq.org](www.winehq.org)

It runs windows programs inside linux. Look at the appdatabase on their to see how visual studio runs in wine.

Also, if you cant get visual studio to run, try code::blocks. It's and IDE like viusal studio and they have a linux and windows edition. I used code::blcoks for C++, but it supports C, LUA, Java and some other scripting languages.

Visual Studio is rated as "Garbage"/"Not installable" under [http://appdb.winehq.org/](http://appdb.winehq.org/). So I would not recommend that...

Other IDEs should work fine. I like Eclipse, but I have never used any C variant.

If your classes require the use of Visual Studio, then VM or dual boot is the way to go. I also think you should try [monodevelop]("http://monodevelop.com/"), it is for C# and .NET. From the webpage:
> MonoDevelop is an IDE primarily designed for C# and other .NET languages. MonoDevelop enables developers to quickly write desktop and ASP.NET Web applications on Linux. MonoDevelop makes it easy for developers to port .NET applications created with Visual Studio to Linux and to maintain a single code base for all platforms.

---

### Post by feardotcom on 2009-06-06
Wow, thanks guys. 
Yeah I'm between a beginner and intermediate user when it comes to Linux. Wine has always caused me problems, I'm not familiar enough with the file structure and the way things work enough to be messing around with setting i probably shouldn't be messing with. 
Of course, the last time i used Wine was probably in early 2008 or late 2007. Once my computer parts get here Wednesday i am going to attempt to get Steam, HL2, CS:S, and L4D to work.

---

