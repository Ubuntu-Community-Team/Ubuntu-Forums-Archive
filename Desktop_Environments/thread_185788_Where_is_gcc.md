---
title: "Where is gcc?"
date: 2006-06-01
forum: Desktop Environments
---

### Post by jerinjoy on 2006-06-01
I've installed gcc 3.4 from Synaptic, but I'm not sure where its gone.
jerinjoy@jerinjoy-laptop:~$ whereis gcc
gcc: /usr/lib/gcc
jerinjoy@jerinjoy-laptop:~$ which gcc
jerinjoy@jerinjoy-laptop:~$

Anyone know what the default location is? Its not in /usr/bin.

[j]

---

### Post by patrickfromspain on 2006-06-01
why do you need gcc 3.4?

---

### Post by jerinjoy on 2006-06-01
I don't need a specific version. I was trying to install the CISCO vpn client and it required gcc to compile a few files. I installed gcc 3.4, I can install 4.0 also. 
But I'm not able to find the one that Synaptic installed on my system.

---

### Post by woot on 2006-06-01
doesnt 

```
sudo apt-get install build-essential
```

install most of the common needed compilers? im quit sure it includes some version of gcc

---

