---
title: "Kernel Compilation for 64 Bit"
date: 2011-03-31
forum: Desktop Environments
---

### Post by Naqib on 2011-03-31
Hi everyone,
   Just I compiled Kernel xxx.3.6 in ubuntu in Virtual Machine for 32 bit. However, I wanted to do it for 64 bit, I dont know what parameter is necessary for 64 bit.  I am new in the world of linux.

                Thanks for the help

---

### Post by 3Miro on 2011-03-31
Your system is either 32-bit or 64-bit. You compile the kernel for the one you are using. I think you need to have some BIOS settings enabled to be able to run 64-bit Virtual Machines but I am not sure what.

Here is the official HowTo about kernel compiling, I hope it helps:

[https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)

I am not sure what you are trying to do. Why are you recompiling the kernel anyway?

---

### Post by Naqib on 2011-04-01
First of all thanks for your reply and I am sorry, I may ask stupid questions, because, I am new in the world of Linux.
In fact, We have a mini computers of 64 bit which has Ubuntu version 8.4 with the kernel xxx.24: 
1. I have two mini computer A and B which are of same specification:
in A i installed ubuntu version 10.10 and compiled kernel version xxx.38. Then I installed that in the same computer A successfully.

2. Then I tied to install the compiled kernel in minicomputer B(with ubuntu version 8) but I received this message:
[start of message]
..............................................................................
Hmm, there is a symbolic link /lib/modules/2.6.38 
However, I cannot read it: No such file or directory 
Therefore, I am deleting /lib/modules/2.6.38/source.
.............................................................................
[end of message]

however, it is installed. But when I did SUDO REBOOT, I could not entered to the computer.

Any Idea please thanks

---

### Post by Naqib on 2011-04-01
The error after reboot is:
.......................................................................................................
Kernel Panic-not syncing VFS:Unable to mount root fs on unknown-block
......................................................................................................

Thanks

---

### Post by 3Miro on 2011-04-01
I don't think you can install kernel for 10.10 on 8.04. There is a host of possible issues (like using extra drivers/modules).

You can compile a kernel for 10.10 and install it on another 10.10 machine (I have done this), however, I wouldn't mix versions. At any rate you should probably install something newer than 8.04 as it is no longer supported.

Having said that, we can try to fix this one. For the kernel error that you are getting, can you post the content of:
```
cat /boot/grub/menu.list
```
also, what kind of file system do you have on 8.04, is it ext3 or ext4 and when you recompiled the kernel, did you compile it with the right driver.

---

### Post by Naqib on 2011-04-01
I tried grub/menu.list file and entered to my system just a 4 minutes a go and now I get error:
.......................................................................................................
xinit: connection reset by peer(errno 104): unable to connect to X Server
xinit: No such process (errno 3) Server error.
........................................................................................................

I dont know alot of stuff are installed in the server :confused:

---

### Post by 3Miro on 2011-04-01
> **Naqib said:**
> I tried grub/menu.list file and entered to my system just a 4 minutes a go and now I get error:
.......................................................................................................
xinit: connection reset by peer(errno 104): unable to connect to X Server
xinit: No such process (errno 3) Server error.
........................................................................................................

I dont know alot of stuff are installed in the server :confused:

Naqib: I don't understand what you are trying to do and exactly how you are trying to do it. Your comments are very short and lack any kind of details, which makes it practically impossible for us to help you.

When you say "I tried grub/menu.list" exactly what do you mean?

Which of the two computers refuses to boot? Is it 8.04 or 10.10. Note that both use different versions of Grub.

Which of the two computers gives you the X server error?

What commands did you run right before that?

Are you using Google translate?

---

### Post by Naqib on 2011-04-01
No I am not using google transulation but my english is not strong. Let me explain it better

1.I compiled  kernel version 2.6.36 in  (Ubuntu 10.10) and installed it in the same (Ubuntu 10.10). It is working fine.

2.I took the same compiled kernel version 2.6.36 and installed it in Ubuntu 8. It was installed successfully but I got this message:

.................................................. ............................
Hmm, there is a symbolic link /lib/modules/2.6.38
However, I cannot read it: No such file or directory
Therefore, I am deleting /lib/modules/2.6.38/source.
.................................................. ...........................

3. When I did restart the machine. I could not log int to the system.
4. I selected the default kernel by selecting the default kernel on restart.
5. Then I have gone through these steps:


   a. sudo update-initramfs -c -k 2.6.36
   b. I added this statement in boot/grub/menu.lst which was not there
      initrd   /boot/initrd.img-2.6.36
   c. restarted the computer.
   d. Now I get this error:


.................................................. .................................................. ...
Kernel Panic-not syncing VFS:Unable to mount root fs on unknown-block
.................................................. .................................................. ..

I hope it is a bit clear than before

Thanks in advance

---

### Post by 3Miro on 2011-04-01
This makes more sense now.


```
sudo update-initramfs -c -k 2.6.36
```
Did you get any error messages?

Check
```
ls /boot
```
Do you see initrd.img-2.6.36 as listed there?

Can you tell me what video card are you using?

Can you post the result from
```
ls /lib/modules
```

The Linux modules are the drivers being used by the system. Those should have been installed along with the kernel (if it compiled and installed correctly). update-initramfs creates a file initrd.img containing all the drivers needed for the system so that those drivers are automatically loaded at boot time. If any of those steps goes wrong, then you will not have the proper drivers to run video or even mount the root partition:
```
Unable to mount root fs on unknown-block
```
This is not the only reason though.

---

### Post by Naqib on 2011-04-04
I am sorry to say that I cannot execute these commands because, my computer does not log in. I mean, I cannot provide the error information.

In fact, my key intention for compiling kernel was get install nvidia driver:
1. whith this version of kernel or upper : linux-image-2.6.31-19-     server_2.6.31-19.56_amd64.deb with


Can I directly install nvidia driver without compiling kernel? 
Can you please advise me any other solution for it after clean installation?

Thanks

---

### Post by 3Miro on 2011-04-05
You don't need to recompile the kernel to install an Nvidia driver! Nobody had to do that since many years ago.

Go to System -> Admin -> Additional Drivers and install it from there. You will get a simple menu to select a driver and then activate it.

I don't know why you cannot login. Can you boot into safe-mode, if you don't get the boot menu, hold the shift key while booting to enter the menu.

---

