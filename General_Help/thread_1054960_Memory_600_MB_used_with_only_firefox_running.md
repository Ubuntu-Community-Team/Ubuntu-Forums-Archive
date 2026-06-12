---
title: "Memory 600 MB used with only firefox running"
date: 2009-01-30
forum: General Help
---

### Post by rajeev1204 on 2009-01-30
Hi

Iam using intrepid 64 bit with 4400 X2 proc and 1 gb ram .

I only have firefox running and system resources shows 650 Mb used.

Whats going on.

---

### Post by LowSky on 2009-01-30
how are we supposed to know what is going on from so little information

open a terminal, type ```
top
``` then hit CTRL+C then select all the data it reported and copy and paste it here, then we can tell you what is taking up your RAM

---

### Post by rajeev1204 on 2009-01-30
raj@raj-desktop:~$ top

top - 19:01:25 up 32 min,  3 users,  load average: 0.27, 0.45, 0.49
Tasks: 141 total,   2 running, 139 sleeping,   0 stopped,   0 zombie
Cpu(s):  2.8%us,  0.7%sy,  0.0%ni, 96.6%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   1023852k total,   907608k used,   116244k free,    27456k buffers
Swap:   995988k total,     3120k used,   992868k free,   236084k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 7053 raj       20   0  492m  76m  24m S    2  7.6   1:04.97 firefox            
 5503 root      20   0  147m  61m  14m R    2  6.2   3:45.26 Xorg               
 7077 raj       20   0  301m  29m  14m S    1  2.9   0:01.18 gnome-terminal     
 7111 raj       20   0 19100 1336  992 R    1  0.1   0:00.12 top                
    1 root      20   0  4100  904  616 S    0  0.1   0:01.22 init               
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S    0  0.0   0:00.02 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1        
    7 root      15  -5     0    0    0 S    0  0.0   0:00.02 ksoftirqd/1        
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1         
    9 root      15  -5     0    0    0 S    0  0.0   0:00.02 events/0           
   10 root      15  -5     0    0    0 S    0  0.0   0:00.02 events/1           
   11 root      15  -5     0    0    0 S    0  0.0   0:00.00 khelper            
   49 root      15  -5     0    0    0 S    0  0.0   0:00.00 kintegrityd/0      
   50 root      15  -5     0    0    0 S    0  0.0   0:00.00 kintegrityd/1      


Its reporting 3 users logged in.Is that the problem?

Iam the only one using this pc.

Thanks .Any help will be appreciated.


P.S.Guest was logged in so i logged out of that.It still shows 500 MB though.No compiz nothing .

---

### Post by theDaveTheRave on 2009-01-30
Just a quick note,

I just ran a top on my terminal and firfox is supposedly using 20% of the memory.

An easy way to check is, once you are running top, hit 'u' and it will ask for your user name, enter it, and as you are running firefox as yourself (and not as root for instance) it will sit at the top of the column.

When I first instaled intrepid firefox used 99% of my cpu, I don't understand why, and after opening just a couple of extra tabs the whole system would slowly crash down.....

The question is, are you therefore runnning a fresh install of intrepid? and have you had all the relevant updates? I only ask about the updates because I have friends using intrepid now and they say that it is fine (in fact they are so pleased with it that I may do a clean install of it myself).

David.

---

### Post by LowSky on 2009-01-30
I only see root and raj using any of the system resources, do you have another login user?

It looks to me that your RAM is holding mostly sleeping processes. nothing crazy.. If you start to run more application the OS will take it off the RAM and place it into SWAP

---

### Post by binbash on 2009-01-30
Do you know the linux ram management ? There is nothing wrong here

---

### Post by rajeev1204 on 2009-01-30
> **binbash said:**
> Do you know the linux ram management ? There is nothing wrong here

Well, it used to be around 350 MB so i will obviously wonder.

Plus when you add up the processes, its just around 100 MB.

So if you can tell me where the other ram is being used i will appreciate it.

I play a lot of games so want to be as lean as possible.

---

### Post by hyper_ch on 2009-01-30
install htop and compare then.
```

sudo apt-get install htop

```

```

htop

```

Are you sure it really uses so much ram or does it just have so much cache?

---

### Post by rajeev1204 on 2009-01-30
> **hyper_ch said:**
> install htop and compare then.
```

sudo apt-get install htop

```

```

htop

```


Are you sure it really uses so much ram or does it just have so much cache?

What is cache? Sorry i dont really understand.

Hmm i found that the zope web server was active on the system duh.
Funny it didnt show in system monitor.

Ill try htop from now on.
Got usage down to 450 mb now.

Ok now down to 350 again huh. Strange.

THanks a lot for htop. Here is a smiley for you :)

---

### Post by liquidhot on 2009-01-30
> **rajeev1204 said:**
> What is cache? Sorry i dont really understand.

The cache hyper_ch is referring to is a space on your hard drive that is used by the OS to hold information from RAM on the hard drive so that your RAM can be freed up for active programs. This cache is called swap because it 'swaps' free space on your hard drive to make free space on your RAM.

---

### Post by PriceChild on 2009-01-30
> **liquidhot said:**
> The cache hyper_ch is referring to is a space on your hard drive that is used by the OS to hold information from RAM on the hard drive so that your RAM can be freed up for active programs. This cache is called swap because it 'swaps' free space on your hard drive to make free space on your RAM.Some information, although not used by any active programs is held in RAM (not just swap) incase it is needed soon, this is the cache. This is counted as part of the used memory in top I believe. Try using ```
free
```

---

### Post by hyper_ch on 2009-01-30
cache is not space on the harddrive.

Unused ram == waste ram

so things that were loaded will still stay in the cache as long as you have enough of it. Only when other applications then need it, it will be cleared. So this improves memory usage.

As PC said, "top" will just display the total amount used while htop differentiates.

---

### Post by PriceChild on 2009-01-30
Bah, edited my previous post. I had 'cache' on the mind when I really meant to suggest running the program 'free' as it shows exactly how much ram is used in cache.

---

### Post by liquidhot on 2009-01-30
I guess I had misinterpreted cache then. :o

---

