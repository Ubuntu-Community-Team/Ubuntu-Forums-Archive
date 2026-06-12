---
title: "System Information (HD, RAM)"
date: 2009-01-18
forum: General Help
---

### Post by change_mode on 2009-01-18
Is there a way to

1. see what program is accessing the hard drive?
2. see what program is using the swap memory?

---

### Post by logos34 on 2009-01-19
type 

top

in terminal

or 

gnome system monitor

---

### Post by Yashiro on 2009-01-19
System menu, Administration, System Monitor
or
In terminal type *gnome-system-monitor*
or
In terminal type *top*
or
In terminal type *ps aux*

---

### Post by adamlau on 2009-01-19
What many users consider a better way:

```
sudo apt-get install htop
```

Then after installation and at a terminal:

```
htop
```

---

### Post by Slim Odds on 2009-01-19
None of these actually show **which program** is **accessing** the disks.

---

### Post by change_mode on 2009-01-19
> **Slim Odds said:**
> None of these actually show **which program** is **accessing** the disks.

Exactly. I should probably have worded it more clearly. I know all the mentioned programs and none of them show which program is accessing the disk (read/write operations) or which program is using the swap memory.

---

### Post by change_mode on 2009-01-27
I'm still looking for such a program.

---

### Post by cdtech on 2009-01-27
RAM is divided into chucks of memory called pages. Swapping is the process where a page of memory (or chunk) is copied into the swap space. It's not an entire program that uses swap but rather chunks of memory.

The program "htop" will show you what program is running on your system.

---

### Post by Slim Odds on 2009-01-27
> **cdtech said:**
> RAM is divided into chucks of memory called pages. Swapping is the process where a page of memory (or chunk) is copied into the swap space. It's not an entire program that uses swap but rather chunks of memory.

Fair enough, but how about part 1 of the question?

How can you tell which programs are accessing the disk (not swap)?

---

### Post by jerome1232 on 2009-01-27
lsof will show all open files, which user has them open and what program has them open.

---

### Post by change_mode on 2009-01-27
I am using HTOP. I'm just wondering why the swap partition would occasionally be used, even though the memory usage is under 10%.
And I get like 2-3 mb/sec disk i/o sometimes when the PC is idle. I guess it's defragmenting, but I wanna know if there's a way to check.

I'll look into lsof ty.

---

### Post by jerome1232 on 2009-01-27
It's probably your system logging information.

I bet an "lsof +D /var" will get you a list of programs that have log files open.

 My systems always use a few mB's of swap after they've been on for awhile, even though I have tons of free ram.

You might also want to look at the program iostat.

---

### Post by Wayne_V on 2009-01-27
To debug disk I/O set the vm/block_dump flag : [http://www.linuxinsight.com/proc_sys_vm_block_dump.html](http://www.linuxinsight.com/proc_sys_vm_block_dump.html)

Note, swap is not used by processes, it is used by the kernel:   [http://www.linux.com/feature/121916](http://www.linux.com/feature/121916)

---

### Post by mb_webguy on 2009-01-27
You can change the degree to which your system uses swap.  See [this thread]("http://ubuntuforums.org/showpost.php?p=1255511&postcount=43") for details.  I don't think you should set swappiness to 0, as the thread suggests, but a swappiness of 5 or 10 if you have around 1GB of memory or more seems to work well.

---

