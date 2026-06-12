---
title: "Where are all those usefull things that are so easily found in windows?"
date: 2005-08-09
forum: Desktop Environments
---

### Post by snoochems on 2005-08-09
Hi.  I'm new to ubuntu... and linux for that matter.

So, i want to know how much hard drive space i have available... i can't find 'my computer', therefore, i can't find my HDD's, and therefore can't 'right-click -> properties'.

Also, i can't find a real version of 'Task Manager'.  I want to see how much ram i have, how much ram is available, and what the CPU load is.  (my ubuntu install is going rather chunky monkey and i want to know why)

I've found this thing called 'System Monitor', but it's obviously wrong.  I know i have 1 GB of RAM installed, but it claims i only have 885MB.

Also, where do i find out my CPU frequnency?  I got the feeling that my CPU is stuck at 1.2GHz as opposed to 2.4GHz (dell laptop auto underclock).


Thanks for your help.

---

### Post by Stormy Eyes on 2005-08-09
[QUOTE=snoochems]So, i want to know how much hard drive space i have available... i can't find 'my computer', therefore, i can't find my HDD's, and therefore can't 'right-click -> properties'.[/quote]

Right-click on the desktop and pick "Open terminal". At the prompt, type **df --si /** to see how much disk you have left.

[QUOTE=snoochems]Also, i can't find a real version of 'Task Manager'.  I want to see how much ram i have, how much ram is available, and what the CPU load is.  (my ubuntu install is going rather chunky monkey and i want to know why)[/quote]

In a terminal, type **top** for a list of processes, CPU load, and other info.

[QUOTE=snoochems]I've found this thing called 'System Monitor', but it's obviously wrong.  I know i have 1 GB of RAM installed, but it claims i only have 885MB.[/quote]

The Linux kernel that comes with Ubuntu by default doesn't have support for machines with 1GB or more of RAM built in. Do a search on the "smp kernel" to learn how to install it.

[QUOTE=snoochems]Also, where do i find out my CPU frequnency?  I got the feeling that my CPU is stuck at 1.2GHz as opposed to 2.4GHz (dell laptop auto underclock).[/QUOTE]

Try **cat /proc/cpuinfo | less** in your terminal prompt.

---

### Post by dbott67 on 2005-08-09
[QUOTE=snoochems]I've found this thing called 'System Monitor', but it's obviously wrong.  I know i have 1 GB of RAM installed, but it claims i only have 885MB.[/QUOTE]

It's possible that your Dell uses "shared RAM" --- meaning that the system RAM (1 GB)  allocates a portion for the video card.  This is quite typical for laptops and systems with integrated video cards.

From the fine print on Dell's website:

```
11. Up to 128MB of system memory may be allocated to support graphics, depending on system memory size and other factors.
```

Just check your model number & you may find where the missing memory went! :)


-Dave

---

### Post by fng on 2005-08-09
EDIT: Storm Eyes was faster than me :)




i can give you some console commands.
I'm not at home for the moment, so i can't look for the exact gui-tools.

```

fng@butters:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda2              18G  2.7G   14G  17% /
tmpfs                 507M     0  507M   0% /dev/shm
/dev/hdc1             190G  149G   42G  79% /mnt/hdc
/dev/hdd1             190G   78G  113G  41% /mnt/hdd
/dev/hde1             153G   49G  105G  32% /mnt/hde
/dev/hdf1              58G   11G   47G  19% /mnt/hdf
/dev                   18G  2.7G   14G  17% /.dev
none                  5.0M  2.8M  2.3M  56% /dev
fng@butters:~$

```

df gives you how much space is used on the mounts and how much is free.

```

fng@butters:~/downloads$ du
738M    ./et
56M     ./qw
1.6G    ./nwn
7.3M    ./doom3
53M     ./cedega
4.8M    ./gPerfection
118M    ./quake3/jb
349M    ./quake3/q3f
201M    ./quake3/wfa
146M    ./quake3/cpma
186M    ./quake3/3wave
488M    ./quake3/reactionq3
449M    ./quake3/urban terror
2.0G    ./quake3
109M    ./warsow
4.7G    .
fng@butters:~/downloads$

```

du gives you how much space a directory (default + subdirs) takes on the drive.

```

fng@butters:~$ top
top - 16:42:49 up 3 days, 13:49,  5 users,  load average: 0.21, 0.18, 0.13
Tasks:  92 total,   2 running,  90 sleeping,   0 stopped,   0 zombie
Cpu(s):  4.4% us,  0.7% sy,  0.0% ni, 92.6% id,  0.5% wa,  1.8% hi,  0.0% si
Mem:   1036484k total,  1027880k used,     8604k free,   109468k buffers
Swap:   979956k total,     5852k used,   974104k free,   451268k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
15591 root      15   0 91988  77m  11m S  3.9  7.7  42:10.51 Xorg
 3845 fng       15   0  446m 167m  27m S  3.9 16.6  13:15.01 java
 8225 fng       16   0  3172 1996  856 S  1.9  0.2  37:15.26 gam_server
    1 root      16   0  1552  508  444 S  0.0  0.0   0:00.64 init

```

top gives you an overview of all the processes running on the system. Similar like the Task Manager in windows.  Don't be allarmed if the numbers of in-use memory is so high.  Its more like "in-use memory + buffers + cache + ...".


```

fng@butters:~$ free
             total       used       free     shared    buffers     cached
Mem:       1036484    1027508       8976          0     106804     454140
-/+ buffers/cache:     **466564**     **569920**
Swap:       979956       5852     974104
fng@butters:~$

``` 

free gives you a better overview of the memory management. The second row are the real numbers :), the actual used and free memory.

---

### Post by snoochems on 2005-08-09
Damn... what kind of dodgy OS is this?  Can't handle 1 GB of RAM?    :) 

That kind of sucks... BTW, this lap top has dedicated video ram, not shared, so there is 1GB of RAM in there for sure.  I know this also because it dual boots windows XP, which reports 1GB installed.

---

### Post by fng on 2005-08-09
I dont have a problem using 1 gb of RAM.  Works fine here.

---

### Post by varunus on 2005-08-09
Everyone above for some reason keeps giving you console commands; I'm assuming you're looking for graphical ones, just like windows has.

Um, if you can't find "My Computer", you must not have looked very hard.  Try Places->Computer.  Ubuntu gets all of the icons off the desktop; most people (including myself) seem to like it this way.  Frankly, I set up windows so that only the recycle bin is on the desktop, and I really wish I could put that on the taskbar somehow.

To see your disk space, you can't right click and then go "properties" though.  Just double click "filesystem."  It'll tell you in the status bar how much space you have free.

Also, you'll probably need a little help installing programs; in Linux, unlike in Windows, you don't go to each individual website to download programs.  Use something called "synaptic" (System->Administration->Synaptic Package Manager).  Follow the instructions here first:
[http://www.ubuntuguide.org/#extrarepositories](http://www.ubuntuguide.org/#extrarepositories)
This will enable Synaptic to look for software in some extra repositories on the internet.  You can install up to 16,000 programs with two clicks!  And dependencies get handled for you, so you know it will work.

You may also want to read this, good for people new to Ubuntu and Linux:
[https://wiki.ubuntu.com//UbuntuHowCome](https://wiki.ubuntu.com//UbuntuHowCome)

---

### Post by Stormy Eyes on 2005-08-09
[QUOTE=snoochems]Damn... what kind of dodgy OS is this?  Can't handle 1 GB of RAM?    :) [/QUOTE]

The Linux kernel can handle a hell of a lot more than a GB of RAM, *if* you build the kernel with the right options. The default kernel wasn't built with the right options. Don't blame Linux; blame whomever built the kernel and didn't think to include high memory support.  [-X

---

### Post by snoochems on 2005-08-09
Okay, i think it is time for me to ask:  WTF is a kernel?

I've heard the word now a million times, but i have no idea what it is, and how on earth do i build one?

Thanks so far guys.  Keep those commands coming.  I'm writing them all done in my note book.

BTW, i don't mind the terminal command line stuff.  I prefer graphical, but, meh.  Either will do

---

### Post by Stormy Eyes on 2005-08-09
[QUOTE=snoochems]Okay, i think it is time for me to ask:  WTF is a kernel?

I've heard the word now a million times, but i have no idea what it is, and how on earth do i build one?[/QUOTE]

The kernel is the core of the operating system. It handles all memory management, disk access, device drivers, etc. All of your software talks to the kernel, and the kernel in turn talks to your hardware. Windows has a kernel as well: kernel32.exe, if memory serves.

Unlike Windows, you can get the source for the Linux kernel and compile it yourself. It's something you do if you need your OS to support something the distro maintainers consider non-standard equipment -- like 1GB of RAM on a single-CPU desktop machine. There should be at least one HOWTO on the Ubuntu forum if you really want to do this; search for it.

---

### Post by varunus on 2005-08-09
No need to recompile.  Just open up synaptic package manager and install the following package:

linux-686 (if you have an intel chip)
linux-k7 (if you have an AMD chip)

Ubuntu ships with 386 linux by default, designed for older processors.  These processors couldn't handle 1 GB of RAM.  However, the 686/k7 kernel is designed for modern processors with more RAM support.

---

### Post by snoochems on 2005-08-09
Thanks.  But do i have to uninstall the 386  version?

---

### Post by jobezone on 2005-08-09
[QUOTE=snoochems]Thanks.  But do i have to uninstall the 386  version?[/QUOTE]
 Lets see whos faster to answer this :)
You can install as many kernels as you want in the system, and at the GRUB screen(The selector thing when you restart the computer) you'll be able to choose which one you want to boot ubuntu with. 
Of course, if the 686 kernel works, you don't have any reason to keep the 386 one, so you can delete it (use Synaptic to remove it).

---

### Post by snoochems on 2005-08-10
Yeah, i noticed the 686 kernal option on booting up.  It detects my 1GB RAM now too.  

Yay and stuff.

---

### Post by Sam on 2005-08-10
[QUOTE=snoochems]BTW, i don't mind the terminal command line stuff.  I prefer graphical, but, meh.  Either will do[/QUOTE]
For a tool showing the amount of free space, install gtkdiskfree from Synaptic. Otherwise use the System Monitor and Resources tab.

---

### Post by Lord Illidan on 2005-08-10
Thanks for the info of the 686, it will solve my problems too!!

---

