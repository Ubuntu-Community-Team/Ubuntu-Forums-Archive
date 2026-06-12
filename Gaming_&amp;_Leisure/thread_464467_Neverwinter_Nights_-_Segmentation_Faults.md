---
title: "Neverwinter Nights - Segmentation Faults"
date: 2007-06-04
forum: Gaming &amp; Leisure
---

### Post by Jainith on 2007-06-04
I've been trying to get Neverwinter Nights working following the various instruction sets posted here and in the Bioware forums, and had no luck. I always seem to get the same error:

```
Fatal signal: Segmentation Fault (SDL Parachute Deployed)
```

I've deleted everything and started fresh twice, most recently following the [official Bioware instructions]("http://http://nwn.bioware.com/downloads/linuxclient.html")

I still end up getting the same error.

I've verified that fixinstall reports everything is ok (previously it did not).
and I am pretty sure that my user owns the directory everything is installed to 
/usr/local/games/nwn

I've tried running 2 straces, and have them available, but they don't seem to offer any insight into what the problem is.

Fragment from the simpler trace...
```
read(10, "#!/bin/sh\n\n# This script runs Ne"..., 8192) = 333
chdir("/usr/local/games/nwn")           = 0
clone(child_stack=0, flags=CLONE_CHILD_CLEARTID|CLONE_CHILD_SETTID|SIGCHLD, child_tidptr=0xb7e61708) = 8105
wait4(-1, Fatal signal: Segmentation Fault (SDL Parachute Deployed)
[{WIFEXITED(s) && WEXITSTATUS(s) == 245}], 0, NULL) = 8105
--- SIGCHLD (Child exited) @ 0 (0) ---

```

Fragment from the detailed trace...
```
8378  _llseek(9, 4935680, [4935680], SEEK_SET) = 0
8378  read(9, ", ability to cast 9th level spel"..., 4096) = 4096
8378  --- SIGSEGV (Segmentation fault) @ 0 (0) ---
8378  rt_sigaction(SIGSEGV, {SIG_DFL}, {0xb7d29200, [SEGV], SA_RESTART}, 8) = 0
8378  write(2, "Fatal signal: ", 14)    = 14
8378  write(2, "Segmentation Fault", 18) = 18
8378  write(2, " (SDL Parachute Deployed)\n", 26) = 26
```

I'd really appreciate it if anyone could help me get this working.

---

### Post by nille on 2007-06-04
I'm not entirely sure about this, but I can recall that when I once did a system-wide installation (not into my /home-directory, but instead to /usr/local/games/nwn) I had to make myseft owner to all the files anyway, otherwise this problem would occur.

Pretty annoying, since the plan was to make the installation reachable for all my users.. :(

However, try this:
**sudo chown -R username:group /usr/local/games/nwn**

Replace username and group with yours, and it should be something like:
**sudo chown -R Jainith:Jainith /usr/local/games/nwn**

Good luck!

---

### Post by Jainith on 2007-06-04
Nille,

Thanks for your suggestion. I checked and found that some files did not have the write permission so I went ahead and permitted everything.
```

 sudo chmod -c -R 777 /usr/local/games/nwn/
```

However, this still results in the same error:

```
Fatal signal: Segmentation Fault (SDL Parachute Deployed)
```

I checked the simple strace again just to be sure, and nothing has changed there.

---

### Post by DoktorSeven on 2007-06-04
I remember having problems with one of the files in the install directory giving me problems; after I installed all of the files and ran ./fixinstall, it complained that it wasn't there, so I **touch**ed the file to create it and ran fixinstall again, but after it said everything was fine, running it gave me that segfault. 

(I can't remember what file it was; seems like it was the last thing fixinstall checks, some small text file).

Removing that file again made it run fine.

Wish I still had it installed so I can be more specific and/or help, but had to make room for other stuff and it had to go.

---

### Post by Jainith on 2007-06-04
DoktorSeven,

My fixinstall file shows the following variables defined...

```
aRequiredDirs=(ambient data music override miles nwm)
aRequiredFiles=(chitin.key dialog.tlk nwmain patch.key)
aLCDirs=(ambient data dmvault hak localvault music override portraits)
aProblemFiles=()
aWritables=(nwn.ini nwnplayer.ini nwncdkey.ini saves localvault tempclient currentgame dmvault)
```

Do any of the aRequiredFiles or aWritables sound like the file you remember?

---

### Post by khaije1 on 2007-06-27
I think I'm having the same problem. Have you been able to make any progress?

---

### Post by Jainith on 2007-06-27
Sorry, to say but I haven't. I was hoping to get some more suggestions of what to try next. But I think I will probably just end up using VMWare to setup a virtual windows box.

---

### Post by rfurman24 on 2007-07-05
This happened to me when I used the files off the Bioware website and I installed the wrong patch. I installed the correct patch and know it works.

---

### Post by ChaOConnor on 2007-07-19
What was the correct patch?  I am having the same problem (SDL Error) and installed the 1.68 patch for the Platinum Edition (Linux) and it hoses it all up.  Thank you!

---

