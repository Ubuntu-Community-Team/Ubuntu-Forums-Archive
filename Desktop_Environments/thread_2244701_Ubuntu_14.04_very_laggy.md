---
title: "Ubuntu 14.04 very laggy"
date: 2014-09-18
forum: Desktop Environments
---

### Post by marshal-banana on 2014-09-18
[COLOR=#000000]hi, I have Acer e725 laptop , 2gb ram, dual boot, win xp sp3, ubuntu 14.04. Ubuntu 14.04 is very laggy and freezes alot especially at web browsing, and images scrolling, and grays alot,, how can I solve this?? thx[/COLOR]

---

### Post by TheFu on 2014-09-18
Don't use Unity, which is a hog.
Look into xfce4 or lxde or a pure WM solution instead. These are designed for low-spec hardware like you have.  Doing things to limit the memory usage would help too.  Browsers these days suck RAM and think nothing of using 1.5G for themselves.  

I have a netbook with 2G of RAM. It has a relatively fast processor and SSD, but the RAM is a limiting thing. I have to watch memory use to ensure the RAM + swap don't get fully used and the system crashes/locks up.  If you cannot add more RAM (I cannot), consider making the swap partition larger - 2G-4G would normally be the recommended size, perhaps 6G would provide the elbow room needed?  BTW, I'm think about this for my own situation too.

```
$ swapon -s
Filename                                Type            Size    Used    Priority
/dev/sda2                               partition       2150396 305836  -1

```
I have 2G for swap and it is currently using about 300M - I'm good right now - but with lots of tabs open in FF and a few doing flash or javascript - that 2G swap can easily be exhausted.

That is why using a lighter DE will help too - less RAM used, means more spare RAM to run programs.

Install lxde with ```
sudo apt-get install lxde
```
Then logout, click on the gear near the login, select LXDE, type in your password and everything should seem a little faster.  If you like it, you can purge Unity.  No OS install/reinstall needed.  A similar command for xfce4 will work too.

---

### Post by marshal-banana on 2014-09-19
thx alot

---

### Post by frankmorris2 on 2014-09-19
Hello,

I would also suggest to take a look at Lubuntu, the Ubuntu OS using a LXDE environment.

It works well on my aging machines.

Have a nice day.

---

