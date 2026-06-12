---
title: "Dell xps l501x ubuntu maverik amd_64 nvidia driver installation"
date: 2011-01-16
forum: Dell Ubuntu Support (CLOSED)
---

### Post by bhaskerchatterjee on 2011-01-16
Hi,

Searched and tried all possible methods/solutions but could not start X after installing nvidia (260.19.26 i.e. the current) on my Dell xps (i5, 420m, 4gb). Please help me.

---

### Post by krunalpatel on 2011-01-16
> **bhaskerchatterjee said:**
> Hi,

Searched and tried all possible methods/solutions but could not start X after installing nvidia (260.19.26 i.e. the current) on my Dell xps (i5, 420m, 4gb). Please help me.


I don't think you searched enough. You have a gpu notebook that supports a technology developed by Nvidia called OPTIMUS. It works fine on Win7, because the drivers have been developed. Currently when you boot into Ubuntu you will be running the Intel gpu by default. From what I understand, the Nvidia gpu is powered ON but cannot be switched to. There are developers that are working on creating "hybrid drivers" (search launchpad) that will allow us to use the OPTIMUS technology. I'd say just sit tight and relax and DONT install the restricted drivers or you will run into issues.

---

### Post by bhaskerchatterjee on 2011-01-18
> **krunalpatel said:**
> I don't think you searched enough. You have a gpu notebook that supports a technology developed by Nvidia called OPTIMUS. It works fine on Win7, because the drivers have been developed. Currently when you boot into Ubuntu you will be running the Intel gpu by default. From what I understand, the Nvidia gpu is powered ON but cannot be switched to. There are developers that are working on creating "hybrid drivers" (search launchpad) that will allow us to use the OPTIMUS technology. I'd say just sit tight and relax and DONT install the restricted drivers or you will run into issues.

Thanks a lot krunalpatel.

I have now come to know all these issues and am really in wait, regularly read all your posts/replies and subscribe to Hybrid-graphix-linux group.

Ok, indeed i am not that interested in any high visual-gaming or some flashy utilities. My main motive behind buying this laptop is to program in CUDA on nVIDIA GPU. I am able to do that even in console provided my CUDA toolkit can see the GPU driver. So as i get stuck at the step of installing the driver i do not move or in reality have not moved further to install/test the CUDA on it.

So can it somehow happen using some 'switcheroo'/.. or something that the X runs only on intel graphics chip and i could run my cuda on nVIDIA GPU as a compute engine as in case of some TESLA GPUs of nVIDIA? 

I can run CUDA on Win7 using visual c++ but that is not as productive as i can do in LINUX.

If anyone in this forum has any experience/idea about any such work out, it would be so great to share it with me.

---

### Post by iammeagain on 2011-03-09
This may interest you. I got the Nvidia turned off for VGA purposes. I figure thats half what you wanted.
I used these two links. I'm gonna try and do a better writeup.
[https://lists.launchpad.net/hybrid-graphics-linux/msg00450.html](https://lists.launchpad.net/hybrid-graphics-linux/msg00450.html)
[http://linux-hybrid-graphics.blogspot.com/2010/07/using-acpicall-module-to-switch-onoff.html](http://linux-hybrid-graphics.blogspot.com/2010/07/using-acpicall-module-to-switch-onoff.html)

Heres the basic commands I used.

```

 lspci -vnnn | perl -lne 'print if /^\d+\:.+(\[\S+\:\S+\])/' | grep VGA
 git clone http://github.com/mkottman/acpi_call.git
 sudo apt-get install git
 git clone http://github.com/mkottman/acpi_call.git
 cd acpi_call
 make
 sudo insmod acpi_call.ko
 ./test_off.sh
 sh m11xr2.sh off
 lspci -vnnn | perl -lne 'print if /^\d+\:.+(\[\S+\:\S+\])/' | grep VGA

```


Here is a more thorough write up.
[http://ubuntuforums.org/showthread.php?p=10540069#post10540069](http://ubuntuforums.org/showthread.php?p=10540069#post10540069)

---

