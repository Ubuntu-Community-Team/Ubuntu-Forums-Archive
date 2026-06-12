---
title: "Running Xubuntu to maximaize MATLAB"
date: 2010-02-02
forum: Desktop Environments
---

### Post by wannabegeek on 2010-02-02
hi everyone,

I just ordered a new IBM Thinkpad T400, the only upgrade I took was the 4GB of RAM.

I want to use this machine to run MATLAB for research projects. It won't be my main machine for hard core number crunching, but I'd like to 
be able to do as much as possible on it.

I have 9.10 on my old Dell now and like it. I just installed the Xubuntu
desktop and really like it...so I am wondering if people here think
it is worth installing Xubuntu over Ubuntu (both 9.10 64 bit) to squeeze
more out of MATLAB.

I also will be using this new computer as my main personal machine too...
Should I just install Ubuntu 9.10 and Xubuntu, and just switch sessions..
or only one ?  or am I mixed up in my understanding ?

thanks,
wbg

---

### Post by Schitso on 2010-02-02
I don't think a desktop environment would be a major drain on system resources. However, if you really wanted to squeeze every last ounce of performance out of your machine, you could stop GDM and launch X with nothing but MATLAB.

---

### Post by wannabegeek on 2010-02-02
> I don't think a desktop environment would be a major drain on system resources. However, if you really wanted to squeeze every last ounce of performance out of your machine, you could stop GDM and launch X with nothing but MATLAB.

that sounds like what I may want...I 'll need to research how that would work, Ubuntu is still new to me.

thanks
wbg

---

### Post by Schitso on 2010-02-03
Hit ctrl+alt+F1, log in, and enter (# lines are comments):
```

# Kills GNOME Display Manager
sudo /etc/init.d/gdm stop
# Starts X
X

```
Wait for X to start up, then hit ctrl+alt+F2, log in, and enter the following:
```

# "/bin/MATLAB" is just a placeholder.
# Enter the full path to the MATLAB executable in its place.
DISPLAY=:0 /bin/MATLAB

```

---

### Post by 3Miro on 2010-02-03
I do numerical simulations (C++) and I have done some testing with Ubuntu. Gnome vs just a terminal gives about 1% improvement in speed. For me this is hardly noticeable and I am using C++, for MATLAB you will have the added inconvenience of the lack of visualization.

To get a better performance, consider using a different kernel. Check these links:

[https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)

[http://blog.avirtualhome.com/2009/11/03/how-to-compile-a-kernel-for-ubuntu-karmic/](http://blog.avirtualhome.com/2009/11/03/how-to-compile-a-kernel-for-ubuntu-karmic/)

READ CAREFULLY, this can actually damage your machine. It is simple enough to follow the instructions, but if you mess up, you can do some damage.

I managed to get almost 10% boost in speed with a custom server oriented kernel build. This was very significant for me. You can also try the server kernel in the repos, I don't know how that would work, but it might be good enough without recompiling.

---

### Post by wannabegeek on 2010-02-04
thanks you I'll check into the kernel switch...before I get my new T400....

I'll post back when I've done something, good or bad :)

wbg

---

