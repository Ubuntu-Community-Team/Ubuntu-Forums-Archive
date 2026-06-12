---
title: "how to install gcc4.3 on Ubuntu10.04"
date: 2010-06-21
forum: Desktop Environments
---

### Post by kwanu on 2010-06-21
Hi,

I am using Ubuntu10.04, but I want to use the gcc4.3.
As you know, there are gcc4.4 and gcc4.3 in Synaptic Package Manager, but if I select the gcc, the gcc4.4 is selected automatically.
So, do you guys know how can I choose the gcc4.3 instead of gcc4.4.

Thanks,

---

### Post by kwanu on 2010-06-21
anybody knows that?
please, let me know...
Thanks,

---

### Post by 3Miro on 2010-06-21
First you need to install gcc 4.3 from Synaptic. Then it depends.

Case 1: If you are making your own program, then just use gcc-4.3 to compile your code (as opposed to simply gcc)

Case 2: If you have downloaded some program from the internet, then it probably comes with its own Makefile. You need to look for common.mk or whatever they have and edit it so that you are using gcc-4.3 as opposed to gcc.

Case 3: This not advisable, but if all else fails you can try it. gcc is actually only a link to gcc-4.4. What you need to do is to at least temporarily change the link to gcc-4.3. Don't leave it pointing to 4.3 since Ubuntu assumes gcc = gcc-4.4 and you may run into trouble.

To make gcc = gcc-4.3:
```
sudo ln -s /usr/bin/gcc-4.3 /usr/bin/gcc 
```
Now compile whatever you need to compile.

To revert it back to the original
```
sudo ln -s /usr/bin/gcc-4.4 /usr/bin/gcc 
```

---

### Post by kwanu on 2010-06-21
Thank you so much, 3Miro.
I can solve it.

---

