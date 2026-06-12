---
title: "Boot hangs forced fsck and exit status 4"
date: 2009-05-13
forum: General Help
---

### Post by cheruvim on 2009-05-13
So I upgrade Jaunty Jackalope and when I try and load the deafult kernel it hangs on a black screen.

when I try to boot by selecting a recovery version of the kernel.. 
ubuntu 9.04, kernel 2.6.28-11(generic) (recovery mode)
It says :

/dev/sda1 contains a file system with errors, check forced.

It then does a check, dies with exit status 4, and then asks me for my root password for maintenance. I enter it and then it says that the password is invalid. Is this the same root password that I sudo with?? Is this some mysterious new password that was set up separately. I am unable to get past this point and cannot boot my system.

I tried to boot with a usb drive to run fsck separatly and that didn't work either, that doesn't boot either. It does boot on other machines.

here are some other circumstances:

tried to hibernate and then failed to get out of it... repowered on.

The blank screens started to happen after installing Ibix  


What does it mean when it says "Unexpected Inconsistency?"

I haven't found that one in any fsck documentation.

---

### Post by geraldvillorente on 2009-05-13
sudo password is different from root password...

to setup root password:
```

sudo passwd root

```
then supply your user password and create root password...that's it

---

### Post by cheruvim on 2009-05-13
Thanks, but the problem was the computer couldn't boot..Hence the disk check. Thus, I couldn't get access to a shell. Therefore, there was no way to change the password. So I was stuck.

However, now I know this is the root user and not some other "maintinence root" user I didn't know about.

I was able to fix the disk and get the computer started..

Thanks!

C.

---

