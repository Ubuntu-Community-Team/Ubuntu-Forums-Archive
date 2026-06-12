---
title: "Open Source Compiler Question"
date: 2009-01-02
forum: General Help
---

### Post by rushinblue on 2009-01-02
I found an app I would like to compile but don't know how to do it. How do I compile open source code?

Thanks

---

### Post by cariboo on 2009-01-02
Seeing as you didn't give us any details, I would suggest checking the repositories to see if the program is available. Go to System-->Administration-->Synaptic Package Manager and click the search button.

For help installing ptograms, have a look [here]("http:///martin.ankerl.com/2007/04/19/how-to-install-anything-in-ubuntu-condensed/").

Jim

---

### Post by oldos2er on 2009-01-02
[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

 [https://help.ubuntu.com/community/OtherWaysToInstall](https://help.ubuntu.com/community/OtherWaysToInstall)

---

### Post by rushinblue on 2009-01-02
I am trying to compile dc3dd-6.12.2 on Ubuntu: 

```

abc@abc-pc:~/Desktop$ cd dc3dd-6.12.2/
abc@abc-pc:~/Desktop/dc3dd-6.12.2$ ./configure 
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
See `config.log' for more details.

```

---

### Post by oldos2er on 2009-01-02
You need to install the package build-essential

---

### Post by rushinblue on 2009-01-02
Thank you oldos2er I am installing it as I post this reply!

---

### Post by rushinblue on 2009-01-02
Thanks!! It worked!

---

