---
title: "Executing a bash script - permission denied"
date: 2009-05-21
forum: General Help
---

### Post by carlbeech on 2009-05-21
Hi All,

A rather weird one - I've just come over from SuSE after many years, after being very impressed when installing on another machine... - but one aspect has me really puzzled...

I've a bash script, I've made it executable (using chmod +x) - kde says it's executable. But when I try and run it (e.g. ./fred.sh), I get permission denied.... - I've not known this on other linux distributions, solaris or other unix's...

Seems the only place I can run scripts is if they're in /usr/local/bin. - Am I going crazy?  (I even get permission denied if I use sudo ./fred.sh   !

Can someone shed some light before I go crazy?

Many thanks in advance...

Carl

---

### Post by baseface on 2009-05-21
> **carlbeech said:**
> Hi All,
 
A rather weird one - I've just come over from SuSE after many years, after being very impressed when installing on another machine... - but one aspect has me really puzzled...
 
I've a bash script, I've made it executable (using chmod +x) - kde says it's executable. But when I try and run it (e.g. ./fred.sh), I get permission denied.... - I've not known this on other linux distributions, solaris or other unix's...
 
Seems the only place I can run scripts is if they're in /usr/local/bin. - Am I going crazy? (I even get permission denied if I use sudo ./fred.sh !
 
Can someone shed some light before I go crazy?
 
Many thanks in advance...
 
Carl
 
you need to add ```
#!/usr/local/bin/bash
``` to the script.

---

### Post by donkyhotay on 2009-05-21
either that or put 'sh' in front of it as in:
```

sh myscript.sh

```

---

### Post by carlbeech on 2009-05-21
Thanks for the swift reply!

Added #!/usr/bin/bash to start (not /usr/local/bin/bash) - interesting - not had to do this before (although I know it's good practice....)

However, I get:

**bash: ../tompg.sh: /usr/bin/bash: bad interpreter: Permission denied**


Any thoughts?

Many thanks

Carl.

---

### Post by baseface on 2009-05-21
are you sure bash is in /usr/bin and not /usr/local/bin?
every system that ive ever used that has had bash installed has had it in /usr/local/bin... hence the reason that its giving you that bad interpreter error.

---

### Post by Kareeser on 2009-05-21
```
julian@julian:~$ which bash
/bin/bash

```

Mine's strictly in /bin. Which would make your crunchbang statement: #!/bin/bash

---

### Post by carlbeech on 2009-05-21
Hi,

Yes - sorry -it is /bin/bash:

carl@carl-desktop:/SPARE3/VIDEO/backing_track$ ls -l /bin/bash
-rwxr-xr-x 1 root root 729040 2009-03-02 14:22 /bin/bash

- Altered my bash script:
carl@carl-desktop:/SPARE3/VIDEO/backing_track$ cat ../tompg.sh
#!/bin/bash
...

carl@carl-desktop:/SPARE3/VIDEO/backing_track$ ls -l ../tompg.sh
-rwxr-xr-x 1 carl carl 209 2009-05-21 19:51 ../tompg.sh

- Execution still gives an error:
bash: ../tompg.sh: /bin/bash: bad interpreter: Permission denied

Good one this....  ](*,)

Carl.

---

### Post by wirelessmonkey on 2009-05-21
Will it run from the directory it's in? 
```

cd ..
./tompg.sh

```

---

### Post by carlbeech on 2009-05-21
Even in the current directory, the program still comes up with the error...

-rwxr-xr-x 1 carl carl 209 2009-05-21 19:51 tompg.sh
carl@carl-desktop:/SPARE3/VIDEO$ ./tompg.sh
bash: ./tompg.sh: /bin/bash: bad interpreter: Permission denied


If I copy it to /usr/local/bin, then it'll work:
carl@carl-desktop:/SPARE3/VIDEO$ /usr/local/bin/tompg.sh
MEncoder 2:1.0~rc2-0ubuntu19 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Core(TM)2 CPU          4400  @ 2.00GHz (Family: 6, Model: 15, Stepping: 2)
CPUflags: Type: 6 MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.

So I'm thinking this is some sort of security 'feature'? - even if I specifically put the path into the PATH variable, I still get the problem:

carl@carl-desktop:/SPARE3/VIDEO$ PATH=$PATH:/SPARE3/VIDEO
carl@carl-desktop:/SPARE3/VIDEO$ export PATH
carl@carl-desktop:/SPARE3/VIDEO$ ./tompg.sh
bash: ./tompg.sh: /bin/bash: bad interpreter: Permission denied

- BTW: forgot to mention, I'm using 9.0.4...

Thanks

Carl

---

### Post by taurus on 2009-05-21
Post tompg.sh.

---

### Post by carlbeech on 2009-05-21
Don't think that the problem is the commands within the script - it's that it can't execute the script - for example:

carl@carl-desktop:/SPARE3/VIDEO$ cat fred.sh
#!/bin/bash

echo "Hello"

carl@carl-desktop:/SPARE3/VIDEO$ ./fred.sh
bash: ./fred.sh: /bin/bash: bad interpreter: Permission denied

carl@carl-desktop:/SPARE3/VIDEO$ ls -l fred.sh
-rwxr-xr-x 1 carl carl 27 2009-05-21 21:45 fred.sh

---

### Post by carlbeech on 2009-05-21
AHA - Solution!

Had a look around for 'bad interpreter' and found the answer - it is in fact the FSTAB!

The fstab entry did NOT have the 'exec' option... setting it to:

/dev/sda8       /SPARE3         ext3    rw,user,exec

- I can now run fred.sh:

carl@carl-desktop:/SPARE3/VIDEO$ ./fred.sh
Hello


At least that's sorted it out - now just to work out the correct mencoder commands to create a MPG file that's readable by windows media... but that's another story!


Many thanks for all the help...

Ta

Carl.

---

