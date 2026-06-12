---
title: "gcc version ?"
date: 2006-04-13
forum: Desktop Environments
---

### Post by vzdesic on 2006-04-13
Hi,
which version of gcc I have after initial installation of Ubuntu? After I write 'gcc' in command line I get 'command not found'. Why ? Have I gcc at all ???
Vedran

---

### Post by Darkriser on 2006-04-13
in Breezy (Ubuntu 5.10) you'll have gcc-4.0 by default. but many tools require gcc-3.4 if you want to compile them. just download the package from repositories and type in console:

sudo CC=gcc-3.4
sudo export CC

---

### Post by geeknation on 2006-04-13
Im unsure, have you tried useing the Synaptic Package Manager to check?

---

### Post by MartinG on 2006-04-13
gcc is not installed by default, nor are several libraries you need for compiling. Run:```
sudo apt-get install build-essential
```If you also need gcc-3.4, it can be installed separately```
sudo apt-get install gcc-3.4
```

---

### Post by vzdesic on 2006-04-13
After I instaled gcc through Synaptic Package Manager I still get 'command not found' in command line for 'gcc' command.

---

### Post by taurus on 2006-04-13
Open a terminal, Applications -> Accessories -> Terminal, and type this
```

gcc -v

```
What does it say after you hit the return key?

---

### Post by vzdesic on 2006-04-13
As I said:

bash: gcc: command not found

---

### Post by Ramses de Norre on 2006-04-13
```
sudo apt-get install gcc gcc-3.3-base gcc-3.4 gcc-3.4-base gcc-4.0 gcc-4.0-base libgcc1   
```
It should work if you've got this packages.

---

### Post by vzdesic on 2006-04-13
After this line it returned:
...
...is already the newest version.
....
E:Couldn't find package libgccl

---

### Post by vzdesic on 2006-04-13
Sorry, solution is so trivial. I just have to write 'gcc-4.0', but not just 'gcc' in command line.

Thanks

---

