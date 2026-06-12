---
title: "need help with ndiswrapper"
date: 2006-07-08
forum: Desktop Environments
---

### Post by cjax1 on 2006-07-08
Hi all. This is the first time I've posted on this forum.
I just reinstalled Breezy Badger and am trying to get my Motorola WN825GP wireless card working. I got it working before after a lot of searching and wrote down what I did and how I got it going in case I had to do it again. But now it will not work. I don't know if I'm missing something. I read that ndiswrapper is already installed in Breezy Badger and I need to install ndiswrapper-utils by using the "Sudo dpkg -i command just like before. That seemed to work. Then I installed ndisgtk. That seemed to go OK. (I'm wondering if I need ndisgtk). Then I installed the Windows driver, in my case the bcmwl5a.inf file, with "sudo ndiswrapper -i bcmwl5a.inf". With out the quotes. But now when I check ndiswrapper -l it says that is an invalid driver. I know it worked before. I also learned how to uninstall the driver by using ndiswrapper -e bcmwl5a.inf. I thought I messed something up and decided to do another clean install of Ubuntu and start over. This time with the same results. When I look at where the inf file is copied to (/etc/ndiswrapper) there are 5 other files there with names like 14E4:4320:1057:7010.5.conf. And after this install I cannot uninstall the inf file like I did before using "ndiswrapper -e." When I try I get this message back, "Driver bcmwl5a.inf is not installed. Use -l to list installed drivers" That's what I did again and this is what it says,
"Installed ndis drivers:
bcmwl5a invalid driver!"
Why is it this time I can't even uninstall the driver?

This time I am realy discusted. After days of searching and trying things out I got it working the first time. Boy was I happy. Now after a reinstall nothing is working. I must have forgot to make a note of something. Can anyone tell me what I'm doing wrong.
Thanks

---

### Post by DJ Scribblinni on 2006-07-08
Well a quick note, when uninstalling the driver the code is only the driver name without the .inf at the end, hence ```
sudo ndiswrapper -e bcmwl5a
```

But from the looks of it your code typing was correct.  So either something changed with the hardware or the driver that is being used.  I'm not exactly sure how to help you from there... :|

---

### Post by cjax1 on 2006-07-08
Thanks. I removed the driver. Then I tried installing the inf driver again. I get no errors but when I check ndiswrapper -l it still says invalid driver. I know it worked before, I wrote it down. The hardware is exactly the same, nothing has changed. What could change from one install to the next? Is it like MS Office 2003 I wonder? I've installed that several times and each time the layout is different. Always some small thing is different. Could this happen when I reinstall Ubuntu? In other words, I just got lucky the last time and now I need to find another driver? This just doesn't sound right.

---

### Post by cjax1 on 2006-07-08
I was just wondering if I need ndisgtk. Is this needed? Could it be the source of my problems?

---

### Post by DJ Scribblinni on 2006-07-08
ndis-gtk is just a gui version of ndiswrapper.  More than likely, there will be no difference after installing it, except a pretty way to look at it in nice dialog boxes rather than the command line.

---

### Post by wieman01 on 2006-07-08
Not sure if this helps but I had a similar problem with my "wusb54g". The driver would not install correctly if the folder containing the driver would only hold the *.inf file. 

You need to have all files that come with the Windows driver package in the folder so that NDiswrapper does its job (in my case these were 3 files in total with different extensions including the *.inf one). Try it out.

He

---

### Post by cjax1 on 2006-07-08
Thanks to both of you. I tried wieman01's suggestion and it worked! I got all the files of the CD that came with the card. bcmwl5.inf, bcmwl5a.inf, bcmwl5.sys and bcmwlntp.sys. This time I installed all of them. This time it said bcmwl5a and bcmwl5 was good. Both said driver present and hardware present. The others said invalid. I uninstalled those. I had both of those inf files installed at once before but not with the .sys files. Ok, I then typed "sudo depmod-a" I forget what this does, I just remember it was important. Then "sudo modprobe ndiswrapper". That got the lights on the card to turn on. But to get the card to activate automatically at boot time you have to type the command "sudo ndiswrapper -m". That didn't work until I uninstalled the bcmwl5 driver, leaving nothing but the one driver, bcmwl5a. Then I had to go to System>Administration>Networking and activate the wireless connection and configure it. I hope all of this I'm typing helps someone else.

So it looks like I need to install all four files, the .inf and .sys files to get it working then after it's all set up get rid of all but one.

Thanks again. I really appreciate the replies.

---

### Post by wieman01 on 2006-07-08
Glad to hear it worked.

As far as I remember, however, you need to install only the *.inf file that corresponds to your wireless card. All the other files merely need to be present in the folder that contains your *.inf file.

He

---

### Post by cjax1 on 2006-07-09
Yes that was my impression too. Here is what it says in the terminal,

chris@Laptop:~$ ndiswrapper -l
Installed ndis drivers:
bcmwl5a driver present, hardware present
chris@Laptop:~$

This is after I uninstalled all the others. However when I look in the ndiswrapper folder the bcmwl5a.inf and the bcmwl5.sys file was put in the folder along with other .conf files that were put there automaticaly. So it looks like I have to install not only bcmwl5a.inf but also at least the bcmwl5.sys file to get it going. The .sys file gets copied into the same folder as the bcmwl5a.inf file.

I don't know if this makes sense. But I am using Ubuntu wirelessly now.

Thanks,
Chris

---

### Post by wieman01 on 2006-07-09
So now try "DJ Scribblinni's" suggestions again... no .inf at the end when installing the driver. That should solve your problem.

---

### Post by cjax1 on 2006-07-09
Yes he was right. After that I was able to uninstall them. But I believe you still need to use the extensions to install them. I should've installed all of them before but what do I know :) I'm tempted to do it all over again and just install the only two files it appears to use and see if that works but why rush it? Let's see how long this install lasts before I screw it up. There's allways a next time. :)

Thanks again. I love Ubuntu! Especialy now.

---

### Post by cjax1 on 2006-07-10
Hi again,

Just an update.

This is what I learned so far. I got it pretty much narrowed down as to exactly which drivers I need. After another install I went through the steps again. Actually I reinstalled because I wanted to change the partitions around. I have one gripe about Ububtu's partitioner but I won't get in to that here. Anyway, It turns out for my Motorola WN825GP wireless card I need the bcmwl5.inf and bcmwl5.sys files. I got those right off of the install CD that came with the card. I put both of those drivers on my desktop. After ndiswrapper and ndisgtk are installed I change directory in the terminal to Desktop and type > sudo ndiswrapper -i bcmwl5.inf. As long as the bcmwl5.sys file is on the desktop it will get installed right along with the .inf file at the same time. If the bcmwl5.sys is not also on the desktop when you install bcmwl5.inf it will not work. This sure beats installing all four then going back and uninstalling all but one.
 
Actually the bcmwl5a.inf will also work. But you still have to have the same sys file on the desktop. So far I do not see any difference in either one as far as how it works. I may find out later. There is one other .sys file on the CD but it was not needed.
 
I am using Breezy Badger on a Toshiba 1555CDS laptop. I would like to upgrade but evidently I need more memory to install Dapper Drake. This thing only has 160 MB of memory. I think I'll try Dapper Drake on my one year old Dell desktop pc. So far Ubuntu and Kubuntu are the only Linux distros that work well on this laptop. I couldn't even get Damn Small Linux on this pc. I may try later but so far out of all the distros I've tried even on my newer pc, I like Ubuntu best. :D
 
Maybe I should write step by step instructions on getting the Motorola card set up.

---

### Post by cjax1 on 2006-07-10
Is there a way to mark this thread solved?

---

