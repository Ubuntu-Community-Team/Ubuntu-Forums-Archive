---
title: "pyrit install problems"
date: 2009-03-19
forum: General Help
---

### Post by bgalfond on 2009-03-19
Has anyone installed pyrit on 8.10?  I keep getting an error that I just can not figure out!

```
ben@ben-desktop:~/pyrit-read-only/pyrit$ ./setup.py build
running build
running build_py
running build_ext
building '_cpyrit._cpyrit_cpu' extension
gcc -pthread -fno-strict-aliasing -DNDEBUG -g -fwrapv -O2 -Wall -Wstrict-prototypes -fPIC -I/usr/include/python2.5 -I/usr/include -I/usr/include/python2.5 -c _cpyrit/_cpyrit_cpu.c -o build/temp.linux-i686-2.5/_cpyrit/_cpyrit_cpu.o -O2
_cpyrit/_cpyrit_cpu.c:21:20: error: Python.h: No such file or directory
_cpyrit/_cpyrit_cpu.c: In function ‘padlock_available’:
_cpyrit/_cpyrit_cpu.c:81: warning: implicit declaration of function ‘strcmp’
_cpyrit/_cpyrit_cpu.c: In function ‘segv_action’:
_cpyrit/_cpyrit_cpu.c:124: error: ‘REG_EIP’ undeclared (first use in this function)
_cpyrit/_cpyrit_cpu.c:124: error: (Each undeclared identifier is reported only once
_cpyrit/_cpyrit_cpu.c:124: error: for each function it appears in.)
_cpyrit/_cpyrit_cpu.c: In function ‘padlock_xsha1_prepare’:
_cpyrit/_cpyrit_cpu.c:134: warning: implicit declaration of function ‘getpagesize’
_cpyrit/_cpyrit_cpu.c:149: warning: implicit declaration of function ‘memcpy’
_cpyrit/_cpyrit_cpu.c:149: warning: incompatible implicit declaration of built-in function ‘memcpy’
_cpyrit/_cpyrit_cpu.c:150: warning: implicit declaration of function ‘memset’
_cpyrit/_cpyrit_cpu.c:150: warning: incompatible implicit declaration of built-in function ‘memset’
_cpyrit/_cpyrit_cpu.c: In function ‘padlock_xsha1_finalize’:
_cpyrit/_cpyrit_cpu.c:182: warning: incompatible implicit declaration of built-in function ‘memcpy’
_cpyrit/_cpyrit_cpu.c: In function ‘prepare_pmk_padlock’:
_cpyrit/_cpyrit_cpu.c:200: warning: incompatible implicit declaration of built-in function ‘memset’
_cpyrit/_cpyrit_cpu.c:201: warning: implicit declaration of function ‘strlen’
_cpyrit/_cpyrit_cpu.c:201: warning: incompatible implicit declaration of built-in function ‘strlen’
_cpyrit/_cpyrit_cpu.c:203: warning: incompatible implicit declaration of built-in function ‘memcpy’
_cpyrit/_cpyrit_cpu.c:206: warning: implicit declaration of function ‘strncpy’
_cpyrit/_cpyrit_cpu.c:206: warning: incompatible implicit declaration of built-in function ‘strncpy’
_cpyrit/_cpyrit_cpu.c: In function ‘finalize_pmk_padlock’:
_cpyrit/_cpyrit_cpu.c:230: warning: incompatible implicit declaration of built-in function ‘memcpy’
_cpyrit/_cpyrit_cpu.c: In function ‘prepare_pmk_openssl’:
_cpyrit/_cpyrit_cpu.c:254: warning: incompatible implicit declaration of built-in function ‘memset’
_cpyrit/_cpyrit_cpu.c:255: warning: incompatible implicit declaration of built-in function ‘strlen’
_cpyrit/_cpyrit_cpu.c:257: warning: incompatible implicit declaration of built-in function ‘memcpy’
_cpyrit/_cpyrit_cpu.c:260: warning: incompatible implicit declaration of built-in function ‘strncpy’
_cpyrit/_cpyrit_cpu.c: In function ‘finalize_pmk_openssl’:
_cpyrit/_cpyrit_cpu.c:287: warning: incompatible implicit declaration of built-in function ‘memcpy’
_cpyrit/_cpyrit_cpu.c: At top level:
_cpyrit/_cpyrit_cpu.c:315: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_cpyrit/_cpyrit_cpu.c:335: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_cpyrit/_cpyrit_cpu.c:377: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘CPyritCPUMethods’
_cpyrit/_cpyrit_cpu.c:384: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘init_cpyrit_cpu’
_cpyrit/_cpyrit_cpu.c: In function ‘main’:
_cpyrit/_cpyrit_cpu.c:406: warning: implicit declaration of function ‘Py_Initialize’
_cpyrit/_cpyrit_cpu.c:408: warning: implicit declaration of function ‘init_cpyrit_cpu’
error: command 'gcc' failed with exit status 1

```

Any ideas?

Thanks!

---

### Post by sahabcse on 2009-03-19
Hi

Install build-essential and G++. Then compile the source package

---

### Post by bgalfond on 2009-03-19
I have both of those installed already.

---

### Post by erik_boi on 2009-03-21
You'll be needing python-dev.

---

### Post by JJjester on 2009-09-14
Sorry to bump an old thread.

I am getting the same errors, I have install essential, g++ and python-dev. Still getting the same error.

Thanks in advance.

---

### Post by cgb223 on 2009-10-12
sorry to bump again but this would be really nice to know. i have all the above packages the python-dev did not help...

Thanks in advanced

---

### Post by andytof47 on 2009-11-05
worked for me, once all packages were installed I compiled and installed

Thanks guys

also check this for additional packes, I follow the to threads and she works for me..... this is just for future reference

[http://ubuntuforums.org/showthread.php?t=1316158](http://ubuntuforums.org/showthread.php?t=1316158)

---

### Post by Elie-M on 2010-05-28
I just did:

sudo apt-get install libssl-dev
sudo apt-get install scapy
sudo apt-get install python-dev
sudo python setup.py build
sudo python setup.py install


and that's enough for it to work, for all who cares.

---

### Post by dowcet on 2011-01-08
> **Elie-M said:**
> I just did:

sudo apt-get install libssl-dev
sudo apt-get install scapy
sudo apt-get install python-dev
sudo python setup.py build
sudo python setup.py install


and that's enough for it to work, for all who cares.

Thanks Elie-M... as a bit of a noob to Linux, this was helpful for me. I realized along the way that I had to download the files from the web and be in the right directory for the last two commands to work, and it also seems that "scapy" is now "python-scapy".

---

### Post by jm.mico on 2011-08-07
In 10.04, I had to do:

```
sudo apt-get install libssl-dev python-scapy python-dev libpcap-dev
```

That did it!

Thanks

---

