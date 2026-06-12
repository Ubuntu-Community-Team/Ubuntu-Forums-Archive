---
title: "Speeding up Hoary"
date: 2005-06-25
forum: Desktop Environments
---

### Post by zee on 2005-06-25
Hi to all.
   What can one try/do to increase the speed of Hoary? I came to Ubuntu from the Gentoo world where speed is of "essence". What packages can be safely removed in order to decrease boot time? Does recompiling the kernel help (I come to notice that all drivers are compiled as modules?

thanks for the answers. I apologize for maybe not posting the questions in the right forum but I didn't know into which subforum do my questions belong.

zee

---

### Post by royg1234 on 2005-06-25
I think [prelink](http://ubuntuforums.org/showthread.php?t=1971&highlight=howto+prelink) helps a lot.

the above link worked for me, but there's an alternate howto here; [http://ubuntuforums.org/showthread.php?t=25274](http://ubuntuforums.org/showthread.php?t=25274)

---

### Post by zee on 2005-06-25
With prelink everything seems slower  :???:

---

### Post by virgule on 2005-06-25
Might reduce the swappiness factor a little, the default value being 60. 

Check current swapiness value:
```

sudo cat /proc/sys/vm/swappiness
60

```
You can see how much memory and swap is in use:
```

free -m

```

Adjust swapping level with command below. Lower the value for less swapping, raise it for more swapping. Default is 60, The more RAM your computer have the lower you can go. Mine have 320, I settled for 30. My computer use only 1 MB in SWAP. I could have gone much lower.
```

sudo sysctl -w vm.swappiness=30

```

---

