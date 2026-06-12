---
title: "Installing Savage (help!)"
date: 2006-12-05
forum: Gaming &amp; Leisure
---

### Post by DudeNuked on 2006-12-05
Ok so I downloaded the Savage+SEP package and when I try to install it it says: ```
~$ sudo sh Savage_with_sep3t.run
Verifying archive integrity... All good.
Uncompressing Savage and SEP3T Installer..........................................................

Gdk-WARNING **: locale not supported by C library

```
It seems not to matter while installing (I can install) but the game wont work as it can read some .log file or so but is the problem with some C-compiler or something ... I don't know. Do you?

---

### Post by haxer on 2006-12-05
try the guide by artificiall experience at ubuntu gamer 
:-k

---

### Post by DudeNuked on 2006-12-06
And where can I find that...? All the 'how to's I've found are a bit outdated as there is no mention of SEP.

---

### Post by mudfly on 2006-12-13
I am having the same issue as DudeNuked with Savage. Here is what happens when I launch from the terminal.

```
Mudfly:~/Games/Savage$ ./Savage 
System_Init()
Couldn't open debug.log for writing
Signal SIGABRT received.

Stack dump:
{
        ./silverback.bin [0x80a956c]
        ./silverback.bin [0x80a9e0f]
        ./silverback.bin [0x809dce7]
        ./silverback.bin [0x80aa2eb]
        /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc) [0xb78178cc]
        ./silverback.bin(__gxx_personality_v0+0xd1) [0x804d6e1]
}

```

I set all of the permissions on the dir to 777 and still have the same problem, yet, I can play if i sudo ./Savage

---

### Post by lrmall01 on 2006-12-27
I think it is because you installed as sudo, so you have to run as sudo.

I installed as my regular user, and installed it into the home directory.

---

### Post by SBFC on 2007-03-05
I installed it in my home directory as well. Thing is...unless I run it as sudo I too get the same error mudfly received. How's that for weird?

---

### Post by conjur3r on 2007-03-06
But the difference was that you installed using sudo which installs as root.  You can try removing the folder and installing again but not using sudo, just your normal account.

---

### Post by SBFC on 2007-03-06
> But the difference was that you installed using sudo which installs as root. You can try removing the folder and installing again but not using sudo, just your normal account.

Mostly true. 

The first time I had installed it, yes, I did install as sudo. But I also installed it in /usr/local/games/Savage. The installer, or I accidently ran the game as sudo without thinking, made a .savage folder in my home directory owned by root. 

I couldn't get the game to work so I deleted it from /usr/local/games/Savage and reinstalled it in my home directory as my user account. Unknown to me was the .savage folder owned by root hiding out in my home directory.

Once I got my wits about me and gave myself ownership of the folder everything was well.

---

