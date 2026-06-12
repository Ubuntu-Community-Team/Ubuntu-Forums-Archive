---
title: "Ubunto crashes when loading programs"
date: 2009-11-23
forum: Dell Ubuntu Support (CLOSED)
---

### Post by RichardStanley on 2009-11-23
Hi,

Sorry if this question has been posted before, but I've been browsing for a few hours and haven't yet come across anything that's been helpful. 

I've just done a fresh install of Ubuntu on a Dell Latitude laptop which went hitch free, up to the point where I try to load a program and the whole system grinds to a halt. The system seems okay with smaller programs like the calculator or note pad, but when it comes to something a little more in depth like any of the OpenOffice programs or FireFox, I get a dialogue box appear in the task bar telling me the program is loading but seconds later the mouse stops working, ALT+F2 won't bring up the task manager and I have to power off to get my system back.

I've read some suggestions that Ubunto doesn't get along too well with my laptop's Radeon Mobility 7500 graphics card and the xorg.conf file appears to be empty, but I'm not too sure how to proceed beyond this. Any suggestions would be much appreciated as the inability to load any programs sort of renders my computer an expensive paperweight!

---

### Post by mikewhatever on 2009-11-24
Can you open Applications->Accessories->Terminal and post the outputs of the following commands:
```
df -h
free -m
```

That will show the amount of space allocated to the system partition and the amount and usage of RAM.

---

### Post by afgsndjfa on 2009-11-24
I think this is enough .....
I do agree with you. Those are the most effective way;):p

---

### Post by RichardStanley on 2009-11-24
Hi, here are the outputs from the commands -

richard@richard-laptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              18G  2.3G   15G  14% /
udev                  249M  232K  249M   1% /dev
none                  249M  764K  248M   1% /dev/shm
none                  249M   80K  249M   1% /var/run
none                  249M     0  249M   0% /var/lock
none                  249M     0  249M   0% /lib/init/rw
richard@richard-laptop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           497        288        208          0         21        103
-/+ buffers/cache:        163        334
Swap:          839          0        839
richard@richard-laptop:~$ 

Thanks for your speedy replies, are you thinking a memory allocation problem might be the root cause of the issue?

---

### Post by mikewhatever on 2009-11-24
> **RichardStanley said:**
> Hi, here are the outputs from the commands -
```

richard@richard-laptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              18G  2.3G   15G  14% /
udev                  249M  232K  249M   1% /dev
none                  249M  764K  248M   1% /dev/shm
none                  249M   80K  249M   1% /var/run
none                  249M     0  249M   0% /var/lock
none                  249M     0  249M   0% /lib/init/rw
richard@richard-laptop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           497        288        208          0         21        103
-/+ buffers/cache:        163        334
Swap:          839          0        839
richard@richard-laptop:~$ 

```
Thanks for your speedy replies, are you thinking a memory allocation problem might be the root cause of the issue?

Yes, both disk and memory allocation could cause freezing, but you seem to be doing fine. Is the system fully updated? What version of Ubuntu are you using? I don't think I've ever seen program opening notifications that you describe.
If you don't get error messages that might hint at the cause of the problem, it might be necessary to look at the logs, but before that, try running one of the problematic programs from terminal and post the output if possible. For example:
```
firefox
```

---

### Post by RichardStanley on 2009-11-24
Hi again, I've just tried to load Firefox through the terminal but it crashes before generating any output at all. Firefox appears minimized in the task bar but the computer then immediately freezes and requires a restart. 

I've installed Ubuntu 9.10 downloaded straight from the Ubuntu website and would run the update program to check for any new patches, but this crashes the system so I am unable to! I'll post some data from the error logs if you're able to advise which ones are relevant and, more importantly, Ubuntu feels up to the task. 

Thanks again for all your help!

---

### Post by mikewhatever on 2009-11-24
I wonder, is there another OS on that computer, that runs well? This is irrelevant to Ubuntu, but would exclude a possible hardware problem. If there isn't, I'd try running memtest, which is one of the options at boot on the live cd.
Looking at the logs may be useful, but I am not quite sure what to look for. The system may also log nothing useful or revealing before it freezes. Anyway, the following are the logs I'd look in:

/var/log/syslog
/var/log/user.log

---

### Post by RichardStanley on 2009-11-25
Hmmm... I had a copy of Windows 2000 Pro installed previously which worked without any problems. It was overwritten during the Ubuntu install though, and as I don't have the installation CD I am unable to go back to it unless I am able to download it 'under the counter' and go back to using the old product key. 

Memtest didn't throw up any errors and I'll check the error logs if the system will run long enough for me to do so without crashing. If there's nothing there I may well try a different OS or maybe an earlier version of Ubuntu?

---

### Post by RichardStanley on 2009-11-25
I've just done a fresh install using Xubuntu instead and it seems to be stable so I think I'll leave it at that, thanks for all your help though, much appreciated!

---

