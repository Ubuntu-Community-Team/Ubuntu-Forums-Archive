---
title: "Qucs simulation doesn't work"
date: 2009-06-13
forum: Desktop Environments
---

### Post by Iteria on 2009-06-13
I'm running Jaunty and I installed Qucs for an assignment I needed to do. I attempted to run a simulation from pure vhdl code, but I got an error that libtool was missing. I installed it via synaptic. then I got a new error:
```
libtool: link: specify a tag with `--tag'
```
I searched google a bit and found [this]("https://bugs.launchpad.net/ubuntu/+source/freehdl/+bug/291075"). According to them it's some sort of problem with a script called gvhdl and were even helpful enough to give a patch script. 

I attempted to patch the script using this command:
```

~/Desktop$ sudo patch -b /usr/bin/gvhdl < gvhdl.diff

```

I go the error again. I had a look at the patch and it looked like it was just updating a variable. I had a peek at the script and the variable wasn't updated from the patch, so I did it manually. 

Despite that, I'm still getting the error when I try to run a simulation. Anyone have an idea how to fix this?

---

### Post by expelledboy on 2009-06-14
Perhaps the patch does something else and you just missed it?

You should check exactly what the patch command is doing..
```
man patch
```
then try and get it working as it is supposed to.

---

### Post by Iteria on 2009-06-14
when I opened the patch up in a text editor it read this:
```

8c8
< my $libtool_options = "--mode=link";
---
> my $libtool_options = "--mode=link --tag=CXX";


```

that's all that's in the patch. I'm pretty sure that it's just updating that one field.

---

