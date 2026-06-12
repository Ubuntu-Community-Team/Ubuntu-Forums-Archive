---
title: "Return to Castle Wolfenstein Install in Ubuntu 8.10 (64 bit problem)"
date: 2009-02-02
forum: Gaming &amp; Leisure
---

### Post by willbe1kenobi on 2009-02-02
I really have this one strange problem. I had installed Return to castle wolfenstein (Game of The Year Edition) for linux first way back when it was released (I had installed it in ubuntu 4.10) and about last year i had lost the cd's. Now a couple of weeks ago I bought another copy from a literally bargain bin in a second hand goods shop, so I decided to try and install it again. I downloaded the setup file from the ID software FTP (and several other websites) and I get this error:

willbeone@ubuntu:~$ cd /home/willbeone/Desktop
willbeone@ubuntu:/home/willbeone/Desktop$ sudo sh wolf-linux-1.4-goty.x86.run 
[sudo] password for willbeone: 
Verifying archive integrity...tail: cannot open `+6' for reading: No such file or directory
Error in check sums 2053104243 3031636474
willbeone@ubuntu:/home/willbeone/Desktop$ 

Yet I haven't had any problems with the install of it. I really would like to play the game again.

---

### Post by MepisReign on 2009-02-17
An error of that kind indicates a bad download, I would strongly suggest that you download those files again. Now that you are on it I will proceed to install it as well and let see how it goes :P

Best Regards,


MepisReign

---

### Post by Sockerdrickan on 2009-02-19
Actually it's probably because of deprecated syntax.

---

### Post by albins on 2009-08-24
> **Tux0r said:**
> Actually it's probably because of deprecated syntax.Correct. I saw this problem [mentioned on the Fedora forums]("http://forums.fedoraforum.org/showthread.php?t=133598"), where the person asking was advised to make tail accept the old syntax by setting _POSIX2_VERSION to 199209, which means if you previously ran ```
./wolf-linux-1.4-full.x86.run
``` you'd now do ```
_POSIX2_VERSION=199209 ./wolf-linux-1.4-full.x86.run
``` This works for me, and it will probably work in other similar cases.

---

### Post by vinnie1 on 2010-01-13
Hi

I am trying to install and play this game, but I get the following error

```


vincent@Athlon5600:~/Downloads$ _POSIX2_VERSION=199209 ./wolf-linux-1.4-goty.x86.run 
Verifying archive integrity...OK
Uncompressing Return To Castle Wolfenstein.............................................................
./setup.sh: 20: source: not found
This installation doesn't support glibc-2.1 on Linux / x86_64
(tried to run setup)
Fatal error, no tech support email configured in this setup
The setup program seems to have failed on x86_64/glibc-2.1

Fatal error, no tech support email configured in this setup
The program returned an error code (1)


```

I know its an old game but hopefully it is still playable.

---

