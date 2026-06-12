---
title: "Installing Grub"
date: 2011-07-31
forum: Desktop Environments
---

### Post by Banshee-2007 on 2011-07-31
Hi every body

Since a while I've installed Windows my laptop , with the wishes of installing grub again after Windows erases it . But today I tried to to that , but all my tries failed .

I depended on this thread to see the way of installing grub :
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

I checked this also :
[http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/](http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/)

I searched for the way of installing grub before I install Windows , just to make sure about where I was going to .

By the way , I have got Ubuntu 11.04

First I applied the first step , when I applied this command :

```

sudo grub

```And Ubuntu gave me the following message >>    sudo: grub: command not found

Then I tried this :
```

grub

```But it gave me this message >>   The program 'grub' is currently not installed.  You can install it by typing:
sudo apt-get install grub

So I applied the command and installed grub . But I want to know install grub from the live CD , because I may face some occasions when the computer is off-line !!

Anyway , I installed it , then rebooted , but nothing has changed . I rebooted again , then reinstalled grub , I applied the first command :
```

sudo grub

```That worked , and then I was in grub I think . I check this command below :

```

find /boot/grub/stage1

```But Ubuntu unfortunately gave me this result >>    Error 15: File not found


So where's the problem ??

Please help guys
and sorry for long thread

---

### Post by Banshee-2007 on 2011-08-01
Isn't there anybody can help ?!

Please I need you help !

---

### Post by xdominex on 2011-08-02
First of all... I feel your pain! I know exactly what you mean! It seems like all these people use that "great wonderful" method of getting GRUB back up and running, but it never works for me. I used THIS thread to get it reinstalled:
[HTML]http://ubuntuforums.org/showthread.php?t=1581099[/HTML]

I would be glad to help you figure out how to work it on your particular setup if you need additional help with it. Anyway, give it a try and let me know how it goes!

With regards,
XSpiritusX

---

### Post by Bobhuber on 2011-08-02
> **Banshee-2007 said:**
> Hi every body

Since a while I've installed Windows my laptop , with the wishes of installing grub again after Windows erases it . But today I tried to to that , but all my tries failed .

I depended on this thread to see the way of installing grub :
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

I checked this also :
[http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/](http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/)

I searched for the way of installing grub before I install Windows , just to make sure about where I was going to .

By the way , I have got Ubuntu 11.04

First I applied the first step , when I applied this command :

```

sudo grub

```And Ubuntu gave me the following message >>    sudo: grub: command not found

Then I tried this :
```

grub

```But it gave me this message >>   The program 'grub' is currently not installed.  You can install it by typing:
sudo apt-get install grub

So I applied the command and installed grub . But I want to know install grub from the live CD , because I may face some occasions when the computer is off-line !!

Anyway , I installed it , then rebooted , but nothing has changed . I rebooted again , then reinstalled grub , I applied the first command :
```

sudo grub

```That worked , and then I was in grub I think . I check this command below :

```

find /boot/grub/stage1

```But Ubuntu unfortunately gave me this result >>    Error 15: File not found


So where's the problem ??

Please help guys
and sorry for long thread

If all else fails you need to look at the offcial ubuntu help documentation.
It gives you everything you never wanted to know and then some about installing Grub. For your problem go toward (near) the bottom of the page.

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by Elfy on 2011-08-02
When you are searching for help on issues try and look at more recent results - what you've found was fine with grub legacy - ubuntu now uses grub2.

---

