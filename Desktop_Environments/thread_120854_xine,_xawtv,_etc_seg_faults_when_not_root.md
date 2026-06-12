---
title: "xine, xawtv, etc seg faults when not root"
date: 2006-01-23
forum: Desktop Environments
---

### Post by alexq on 2006-01-23
hi all.. i don't know what triggered this to start happening, but most video apps i try to use (xmms, xawtv, xine) segfault when i run as a user. they didn't used to do this- something has changed. i've checked all the groups i could think of, as well as access rights to things  in /dev that made sense to check (audio, video, etc), but that didn't seem to help.

when run as root, these apps are fine.

interestingly tvtime can be run as a non-root user.

when i run strace on these apps, i find that they all crash with the same last few calls:
open("/dev/zero", O_RDWR)               = 8
mmap2(NULL, 8192, PROT_READ|PROT_WRITE|PROT_EXEC, MAP_PRIVATE, 8, 0) = 0xb63f2000
close(8)                                = 0
mmap2(NULL, 372736, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb5986000
--- SIGSEGV (Segmentation fault) @ 0 (0) ---
+++ killed by SIGSEGV +++

does this mean anything to anyone?

much thanks!!!

---

### Post by tfotherby on 2006-01-25
I have the same problem (xmms, xine, mplayer etc seg fault when run).

If I run "xine --verbose" I can see that the segfault occurs after the pluggins have been loaded but with mplayer the seg fault occurs immediatly.

I guessing one of my libraries that these programs share is corrupt. Does anyone have any ideas?

---

### Post by alexq on 2006-01-25
interesting.. have you tried running it as root?

i'll have to try what you suggest and see if i have the same problem.

---

### Post by tfotherby on 2006-01-25
I tried running xine and mplayer as root and still get the same seg fault.  Typeing "strace mplayer" ends with:

open("/dev/zero", O_RDWR)               = 3
mmap2(NULL, 8192, PROT_READ|PROT_WRITE|PROT_EXEC, MAP_PRIVATE, 3, 0) = 0xb7f23000
close(3)                                = 0
mmap2(NULL, 372736, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb64c4000
--- SIGSEGV (Segmentation fault) @ 0 (0) ---
+++ killed by SIGSEGV +++

I'm hoping someone smart will read this thread and tell me what to do.

---

### Post by alexq on 2006-01-25
it feels like that's the same problem then. 

from what i could see, all the programs that crash were crashing with the same last 3 calls - which implies a library routine that's failing?
in my case i'd wondered if it could be access rights to some file, since i can run as root. for you, not sure.
i wonder what that library routine is supposed to do.

just out of curiousity, what kernel version are you using? :)

---

### Post by tfotherby on 2006-01-26
I'm running kernel version 2.6.12-10-386.

My current workaround is to use ffplay. Using ffplay I can watch mpg files such as lost.mpg and I can watch TV by streaming the TV card output to a mpg file and then watching it using ffplay. But it was a lot simpler to just use xine to watch TV.

The question is why does ffplay work but xine and mplayer not? Have xine & mplayer got a library in common which ffplay doesn't use? If so, it might pin point our problem.

I also discovered xmms doesn't work, neither does mythTV but aviplay does.

---

### Post by tfotherby on 2006-02-15
Note: Just this one little command fix's it for me:

sudo touch /etc/ld.so.nohwcap

(see [http://ubuntuforums.org/showthread.php?p=738069#post738069](http://ubuntuforums.org/showthread.php?p=738069#post738069))

---

