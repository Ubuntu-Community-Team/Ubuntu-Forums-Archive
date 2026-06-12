---
title: "Everything loading up a tad slow"
date: 2005-12-30
forum: General Help
---

### Post by pk_volt on 2005-12-30
Firstly, I'm using fvwm, but I don't think that should make any issue with my problem.

Comparing to windows, say for example a firefox tab.  If I click it, there's a slight, but noticible lag before the tabbed page shows up.  But in windows, ofcourse, it happens instantly.

This is not just firefox, but anything else I click, it seems to have a lag.  Also, I also notice the loading time is pretty slow.  Even when I open up leafpad, it'll take ~20ms, but ofcourse, in windows, it'll open up something like notepad instantly.

I'm using nvidia drivers.

I've always had this problem whenever I installed linux on various computers.

thanks

---

### Post by Perfect Storm on 2005-12-30
Did you install the right kernel for your system? Have you tried the new firefox (1.5)? Did you test if the nvidia-driver is woking properly?

---

### Post by Mr Frosti on 2005-12-30
There are a lot of things that you can do to speed up your system. Check out the following options:

1. Disable un-needed processes. iD3master has written a great tutorial here:

[http://ubuntuforums.org/showthread.php?t=89491]("http://ubuntuforums.org/showthread.php?t=89491")

2. Consider the user of prelinking. It holds common library files in memory, much the way that Windows does for quickly launching applications. poofyhairguy has written a great tutorial for this, and it can be found here:

[http://ubuntuforums.org/showthread.php?t=74197&highlight=prelink]("http://ubuntuforums.org/showthread.php?t=74197&highlight=prelink")

3. Install a hardware specific kernel. If you are using a 686 machine (which the odds are probably good that you are), install the 686 kernel, and modules. 

I am judging from the fact that you are using FVWM that you have some experiencing with Linux, so I will not cover how to do these things unless asked. 

As a final note, it is important to note a very important difference between the approach that Linux has taken over the approach Microsoft has taken. Most of a users day to day applications in Windows are programs with libraries built into the OS. Notepad, Internet Explorer, and Office all use libraries that are pretty much loaded in RAM before you ever open them. 

Linux has a different approach of loading libraries on a needed basis. This is because an OS as versatile as Linux cannot assume what applications you will use for what tasks. For a browser, you might use Mozilla, Firefox, Opera, or Konqueror. Try loading a non-Microsoft application in Windows and you experience the effect you are describing in Linux.

---

### Post by Mr Frosti on 2005-12-30
Artificial Intelligence reminded me:

Firefox version 1.5 has made a lot of significant improvements in speed over the version 1.0.* builds. Caching is used effectively, and the entire code base is lighter and less CPU intensive. Give version 1.5 a try and I think that this will help improve the experience.

---

### Post by pk_volt on 2005-12-30
well my kernel verison is

2.6.12-9-386

I have an amd athlon xp 3200+ 

How do I test if my nvidia drivers are working properly as suggested?

gonna try firefox 1.5

I guess what you said about hwo programs load up in windows makes sense as to what I'm experience, but again, I don't know if ti's normal since I've never tried using someone else's linux box

---

### Post by Perfect Storm on 2005-12-30
If you are using Pentium or Celeron proccessor:

```
sudo apt-get install linux-686
```

reboot.

Usually you can check if the nvidia driver is enable by writting **glxgears** and see some gears spinning around.

Edit: Athlon? I think you need to install linux-k7

---

### Post by Lord Illidan on 2005-12-30
The 686 kernel with firefox 1.5 is great.

To install kernel ```
sudo apt-get install linux-686
```

---

### Post by pk_volt on 2005-12-30
just a little update

I installed firefox 1.5

everything seems to load up faster.

I'm gonna go check out the kernel suggested

---

### Post by linkunderscore on 2006-01-10
should he:

```
sudo apt-get install linux-image-2.6.12-9-k7
```

since he is running an amd cpu?


Also, I too run fvwm and notice a delay in the INITIAL start-up of programs. After I open the program once, it boots exponentially faster everytime after. I may have to look into prelinking because that appears to be a useful way to prevent this type of slow down. 

The more I think about it, this happens to me in gnome too...its just everything else is slower as well so its not as noticable comparatively. :)

---

