---
title: "GCC problem"
date: 2006-02-05
forum: Desktop Environments
---

### Post by sacoskun on 2006-02-05
Hello,

I have installed gcc-4.0 from Synaptic Package Manager but when I compile my C program, I'm receiving an error like this 

deneme1.c:1:20: error: stdio.h: No such file or directory
deneme1.c: In function ‘main’:
deneme1.c:5: warning: incompatible implicit declaration of built-in function ‘printf’

Program is just a hello world application.

It cannot see include directives.

Any help would be appriciated,

Best wishes,

Sarp Arda Coskun

---

### Post by taurus on 2006-02-05
May have to install all the libraries related to gcc as

sudo apt-get install build-essential

---

### Post by sacoskun on 2006-02-05
Thank you very much.

It worked, how do you know this command friend? I'm very impressed. Is there anywhere that I can learn about these commands?

Lastly what does this command do? It installed g++ and its libraries, right? But it does not work when I installed them from Synaptic Package Manager?

Thank you again taurus.

---

### Post by cdhotfire on 2006-02-05
Build essential is a collection of, as the name refers, building essentials, for making from source.

If you go to Synaptic and search for build-essential then right click it and press "Properties", then click on the "Dependencies" tab, it should show what packages it installed. :)

---

### Post by sacoskun on 2006-02-05
Cool thanks cdhotfire.

build-essential Dependencies were;
libc6-dev libc-dev
gcc
g++
make
dpkg-dev

---

