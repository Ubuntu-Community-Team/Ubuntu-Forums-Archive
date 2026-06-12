---
title: "Slow program startup!"
date: 2006-09-21
forum: Desktop Environments
---

### Post by annaraps on 2006-09-21
Hi

I have Ubuntu Dapper Drake 6.06 LTS installed.
It all worked fine for sometime but then programs started slowing down

Nowadays when I start vim in the terminal it takes about 20 secs to start up.This is the case with other applications too , firefox , gthumb , gaim and so on.What could be the problem? :?: 

I am using the 2.6.15-26-386 kernel.

---

### Post by veli on 2006-09-21
Install preload and prelink from Synaptic. Search the forums for prelink. Also you'll find many other tweaks on the thread; How to improve performance in Ubuntu.

---

### Post by annaraps on 2006-09-23
I don't see any visible change even after installing preload and prelink

---

### Post by richardq on 2006-09-23
I used to have a similar problem. There are several things I tried on my way to getting it solved. One of them might help you:

1. Try running the linux 686 kernel package instead of the 386 one.
> sudo apt-get install linux-686

2. Try running the slow-launching application from a terminal window with the command strace and watch the output to see where if it slows down at any specific point. This might provide clues to the problem. You can try this with different apps to see if they all slow down at a similar set of function calls etc. So if gedit is running slowly, then run:
> strace gedit

3. If watching the strace output you notice that fonts are loading really slowly, you can try re-caching the fonts by:
> sudo fc-cache -v -f

4. The above steps helped shorten my application startup times from 25sec down to about 4 sec. But then unrelated to this I read and followed the instructions in [this thread]("http://ubuntuforums.org/showthread.php?t=89491&highlight=speeding"). It describes how to turn off certain services that you don't require so they don't load at startup. I'm not sure which one it was, but after running through that exercise I think I must have turned off something that was eating up resources. The machine was 500% faster after that. So basically steps 1 through 3 might not have been the main culprit after all.

Hopefully you find a solution. I know it was extremely frustrating to me when I had the problem.

---

### Post by annaraps on 2006-09-24
Hi Richard

Yes , it was quite frustrating to see that something as simple as vim could take 20s to start.

I tried strace on different applications but it
doesn't seem as if they get stuck at the same point.

Vim starts up quicker than usual sometimes but at 
other times ,say after two or three writes to file,
it takes longer than 20s.This is the case with other
apps like Gaim, Gnome-Terminal,Firefox and even mutt.

I followed up on the thread about the boot processes
and changed things accordingly.Bootup time has improved
considerably but the problem of slow program startup
still exists.

strace vim performs the following lines repeatedly 
though , which I think might be where it gets stuck.

$$strace vim
> 
..........................
..........................
[B]old_mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7f72000
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
old_mmap(NULL, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7f70000[/B]
access("/etc/ld.so.preload", R_OK)      = -1 ENOENT (No such file or directory)
open("/etc/ld.so.cache", O_RDONLY)      = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=67715, ...}) = 0
old_mmap(NULL, 67715, PROT_READ, MAP_PRIVATE, 3, 0) = 0xb7f5f000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libgtk-x11-2.0.so.0", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\320l\233"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=2953000, ...}) = 0
[B]old_mmap(0x4f96d000, 2966572, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x4f96d000
old_mmap(0x4fc36000, 36864, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x2c8000) = 0x4fc36000
old_mmap(0x4fc3f000, 9260, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x4fc3f000[/B]
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libgdk-x11-2.0.so.0", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0`<\315O"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=514492, ...}) = 0
............................
............................


---

