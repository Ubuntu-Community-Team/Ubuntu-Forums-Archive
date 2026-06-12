---
title: "Too many boot options/No gui at startup"
date: 2010-06-30
forum: Desktop Environments
---

### Post by Pithikos on 2010-06-30
Hi! I had bought a new wifi card(rtl8185) and spent 2 days trying to make it work. I finally got it working but now I am experiencing some other problems. 


First of all I get two many bootup options. Before I used to have 4 generic options(2 different kernels with each of them having their own recovery), memtest and then my win7. Now I am having those plus 4 server options and 4 preemp(no clue what this is) options. I am suspicious that this has to do with some command I ran: [COLOR=Red]sudo apt-get install linux-backports-modules-wireless-*[/COLOR]
I got some notify at that point about broken packages. I followed the instructions given and made the messages dissapear(I don't remember excactly what I did).
Then when I saw that it shows all those bootup options I tryied [COLOR=Red]sudo apt-get remove  linux-backports-modules-wireless-server [COLOR=Black]and [/COLOR][/COLOR][COLOR=Red]sudo apt-get remove  linux-backports-modules-wireless-preemp [COLOR=Black]but that didn't solve anything.

My second problem is that in startup now even if I choose the *generic* option it doesn't load the gui but just gives me the command prompt so I have to run [COLOR=Red]startx[/COLOR] each time.


I am kind of a noobie in linux but would like to learn so please give me some guidance. I thought of reinstalling a fresh copy of Ubuntu-desktop but it's just too hard work. So I would be grateful if you could tip me on how fixing the problem as it is. I run Ubuntu 10.04 x64

Cheers! :)
[/COLOR][/COLOR]

---

### Post by iponeverything on 2010-06-30
First make a note of kernels that you no longer want in your boot menu. 

Next find with this command:

```
dpkg -l |grep kernel 
```

This will list all of the installed kernels. Only remove the ones that you no longer want. Say for example one of kernels is linux-image-2.6.27-11-generic remove it with -- find associated packages with:
```

dpkg -l |grep 2.6.27-11
```

which will give:

```
ii  linux-headers-2.6.27-11                    2.6.27-11.31                              Header files related to Linux kernel version
ii  linux-headers-2.6.27-11-generic            2.6.27-11.31                              Linux kernel headers for version 2.6.27 on x
ii  linux-image-2.6.27-11-generic              2.6.27-11.31                              Linux kernel image for version 2.6.27 on x86
ii  linux-restricted-modules-2.6.27-11-generic 2.6.27-11.16                              Non-free Linux kernel modules for version 2.
```

remove them with:

```
sudo dpkg -e linux-image-2.6.27-11-generic linux-headers-2.6.27-11 linux-headers-2.6.27-11-generic linux-restricted-modules-2.6.27-11-generic
```

To have it start into X

```
sudo runlevel --set=3
```


lastly the extra kernels had nothing to do with your:
```
sudo apt-get install linux-backports-modules-wireless
```

---

### Post by Pithikos on 2010-06-30
Thanks for the fast reply but I am having some problem with the commands. So far I can see these: ```
>dpkg -l |grep 2.6.32.21
ii  linux-backports-modules-wireless-2.6.32-21-generic 2.6.32-21.11                                    compat-wireless Linux modules for version 2.
ii  linux-headers-2.6.32-21                            2.6.32-21.32                                    Header files related to Linux kernel version
ii  linux-headers-2.6.32-21-generic                    2.6.32-21.32                                    Linux kernel headers for version 2.6.32 on x
ii  linux-image-2.6.32-21-generic                      2.6.32-21.32                                    Linux kernel image for version 2.6.32 on x86
ii  linux-image-2.6.32-21-preempt                      2.6.32-21.32                                    Linux kernel image for version 2.6.32 on x86
ii  linux-image-2.6.32-21-server                       2.6.32-21.32                                    Linux kernel image for version 2.6.32 on x86

```So what I want is to just have the generic kernel that I had from the beginning when I installed ubuntu-desktop. And by the way is it right that the kernels are x86? As I installed Ubuntu x64 for my system :S
If I am right I should remove all of those except *linux-headers-2.6.32-21-generic*, *linux-image-2.6.32-21-generic* and* linux-headers-2.6.32-21*.

I tryied running ```
sudo dpkg -e linux-backports-modules-wireless-2.6.32-21-generic
```  and ```
sudo dpkg -e linux-backports-modules-wireless-2.6.32-21-generic linux-image-2.6.32-21-preempt linux-image-2.6.32-21-server
```but none seems to work. With the first command I get "dpkg-deb: failed to read archive `linux-backports-modules-wireless-2.6.32-21-generic': No such file or directory" and with the second I get "dpkg-deb: --control takes at most two arguments (.deb and directory)"

---

### Post by iponeverything on 2010-06-30
Sorry, I gave you the wrong flag with dpkg, it should be "-r" and not "-e".  I am so used to just pulling things out of my head, that I rarely check any more!

---

### Post by Pithikos on 2010-07-01
OK thanks a lot! I cleaned up the system now :> Had to run ```
sudo dpkg --purge <package>
``` also to clear its config files

About the runlevel I read somewhere that Ubuntu does have only 2 runlevels and the default is 2. I run ```
runlevel
``` and it replied with "2" so didn't do anything further. On next reboot it was just running like normal :)

---

