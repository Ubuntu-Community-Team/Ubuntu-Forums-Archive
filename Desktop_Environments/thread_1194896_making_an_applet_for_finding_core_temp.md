---
title: "making an applet for finding core temp"
date: 2009-06-23
forum: Desktop Environments
---

### Post by abhigyan91 on 2009-06-23
hey, im a noob linux user.. i have a compaq zq50, nvidia geforce 8200MG.
i found out that using,

```


 nvidia-settings --query all | grep 'GPUCoreTemp'


```

I can find out the core temperature of my computer.

on executing the code, it returns
```

Attribute 'GPUCoreTemp' (abhigyan-laptop:0.0): 77.
    'GPUCoreTemp' is an integer attribute.
    'GPUCoreTemp' is a read-only attribute.
    'GPUCoreTemp' can use the following target types: X Screen, GPU.

```

as you can see, the last three lines are pretty useless.
1. Is there any way to get rid of these lines? means i only want the last integer on the first line as the output.

2.Also i wanted to make an applet that can be added to my panel that perennially shows the core temp. Can any1 advise me on how to proceed. I want to know how to make an applet in general, can it be made only using only the shell programming language or do you need c++, python etc?
I have some knowledge of python, c and c++(am very noob here too :(), so i dont mind using this to my advantage to build the applet. 

Thanks in advance!!

---

### Post by VCoolio on 2009-06-23
nvidia-settings --query all | grep 'GPUCoreTemp' | grep abhigyan-laptop | awk '{print $4}'

change the 4 until you get the right thing. Awk prints the 4th item on that line. Also something like 
nvidia-settings --query all | grep 'GPUCoreTemp' | cut -f2 -d:
could do the trick, but I'm not into 'cut'.

---

### Post by prshah on 2009-06-23
> **abhigyan91 said:**
> 
on executing the code, it returns
```

Attribute 'GPUCoreTemp' (abhigyan-laptop:0.0): 77.
    'GPUCoreTemp' is an integer attribute.
    'GPUCoreTemp' is a read-only attribute.
    'GPUCoreTemp' can use the following target types: X Screen, GPU.

```

as you can see, the last three lines are pretty useless.


```
 nvidia-settings --query all | grep 'GPUCoreTemp' | head -1
```

---

