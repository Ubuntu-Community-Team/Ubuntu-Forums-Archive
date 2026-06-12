---
title: "Nvidia drivers stop working after installing 'linux-server' package."
date: 2009-06-18
forum: General Help
---

### Post by insanity54 on 2009-06-18
Looks like my tinkering has got me into trouble.

I recently installed intrepid onto a freshly formatted HDD, and easily upgraded to jaunty. I've had GB of ram since I've had this machine, but only 3GB are recognized. I thought I'd do something about that and follow the advice of several helpful people over in [this thread]("http://ubuntuforums.org/showthread.php?p=7367999&posted=1#post7367999"). All I did was open a terminal and type,

```
sudo apt-get install linux-server
```

I then restarted, and when starting up, I was notified that the NVIDA drivers couldn't start, and it asked if I wanted to start in low-graphics mode. I wasn't really surprised. I am assuming that installing 'linux-server' changes my kernel, and that my nvidia drivers are not configured for said kernel? I thought it would be easy to get back up and running again from System>Administration>Hardware Drivers, but it doesn't look like that's the case. Going to System>Administration>Harware Drivers shows both available drivers as not activated, and try as I might, I can't get either driver to become activated.

Upon starting Nvida X Server Settings, I am greeted with,

```
You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. 
```

Did what it said, got some warnings, no improvements.

My CRT display is making a very high pitched screech that gives me a headache, and the refresh rate hurts my eyes. On the up side, my system now sees all 4 GB of ram! 

What I'm thinking of doing next is going to nvidia.com and just downloading the nvidia drivers from there, but I'm not sure if that's a good move, or if it will just mess up my system even more. What should I do?

*Edit:

Thanks to ericab for the quick and simple fix:

```
sudo apt-get install linux-headers-server
```

---

