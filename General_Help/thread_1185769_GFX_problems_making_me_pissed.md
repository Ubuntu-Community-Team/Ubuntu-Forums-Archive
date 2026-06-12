---
title: "GFX problems making me pissed"
date: 2009-06-12
forum: General Help
---

### Post by kokkus on 2009-06-12
Hey.
OK here's the situation.
I upgraded to the newest Ubuntu version the other day.
Now I can't get my Nvida graphic card to work. 
When I try to install one of the 3 alternative nvida drivers, I get an error message everytime I start ubuntu again.
SO I go to recovery mode and try to repair the GFX settings so I can atleast use the OS.
I really love Ubuntu but there are also 100s of problems I do not get with windows. I don't know why the GFX cards can't be auto installed since everything else does?

I hope you guys can help me getting this fixed. Thanks in advance:)

EDIT: I think it has something to do with Grub. I remember the last time this happend was because I still had grub ubuntu 8.04 Kernel 2.6.24 something.
I wonder if this is the problem now but I can't figure out how to update the grub from 8.10. Thanks!

---

### Post by kokkus on 2009-06-14
Bump
I really hate to bump but this is importent.
Please!

---

### Post by Comzee on 2009-06-14
Heres a possible solution for you. I think the three possible solutions (drivers) that you mentioned are the restricted ones that Ubuntu by default lets you use. In my opinion, they are complete junk and nobody should use them if they have an Nvidia card. Nvidia has released it's own drivers for Linux, they have support all the way back to the MX 4 series (hope you don't have a card older then that). Go [here]("http://www.nvidia.com/Download/index.aspx?lang=en-us") and choose your series and download the Linux driver they have.

Installation is a little tricky, I'll give you a little tutorial.

1: Download the driver to your home directory (for simplicities sake)

2: (Warning, read this entire tutorial before you take this step, you can't go back and read this once you do) Use the hotkey ctrl+alt+f1, this brings you to a black screen and prompts you for your username and password. You'll want to enter your credentials obviously.

3: Once your enter your credentials, you get a nice little bash prompt. Don't be afraid, this is your friend. The first thing you want to do is type in the command ```
sudo /ect/init.d/gdm stop
``` it will prompt you for your password, enter it. 

4: Now if you downloaded the driver into your home directory, you want to cd there: example ```
cd /home/(your user name)
```

5: type the command ```
ls
``` to view the contents of the folder your in, if you see your Nvidia driver your doing good.

6: Type **sudo chmod +x (complete name of your nivida driver, which you should have seen in the last step)**. Example ```
sudo chmod +x NVIDIA-Linux-x86-185.18.14-pkg1.run
```

7: now type **sudo ./(complete name of your nvidia driver)**, example ```
sudo ./NVIDIA-Linux-x86-185.18.14-pkg1.run
```

8: follow the on screen directions to install the driver, their pretty simplistic.

9: Now your back at your bash prompt, type ```
reboot
``` and cross your fingers!

10: Don't forget the step #2 warning, you should probably write these commands down if your not sure you can remember them all during the process.

---

### Post by merlinus on 2009-06-14
I followed your instructions, and now have kernel problems, which means I can only run in lo-res.  How can I restore my previous nvidia driver?

Thanks.

---

### Post by Comzee on 2009-06-14
> **merlinus said:**
> I followed your instructions, and now have kernel problems, which means I can only run in lo-res.  How can I restore my previous nvidia driver?

Thanks.

Thats not good, your problem was most likely caused if you already had the restricted drivers installed. I usually install the official Nvidia drivers on a clean install to avoid problems like yours.

I grabbed this from [here]("http://ohioloco.ubuntuforums.org/showthread.php?t=683291&highlight=low+resolution") I give credit to overdrank.

> Hi, when you reach the login screen use the keys ctrl, alt, F1 all at the same time and this will bring you to the command line. Login with user name and password and then enter this command

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

and when complete use the command to reboot

```
sudo reboot
```

---

### Post by bollix47 on 2009-06-14
FYI

The following link shows the procedure I have used successfully to install nvidia's drivers:

[http://ubuntuforums.org/showpost.php?p=7081255&postcount=6](http://ubuntuforums.org/showpost.php?p=7081255&postcount=6)

I usually have problems if I don't purge any existing drivers.

Good luck.  ;)

---

### Post by Comzee on 2009-06-14
> **bollix47 said:**
> FYI

The following link shows the procedure I have used successfully to install nvidia's drivers:

[http://ubuntuforums.org/showpost.php?p=7081255&postcount=6](http://ubuntuforums.org/showpost.php?p=7081255&postcount=6)

I usually have problems if I don't purge any existing drivers.

Good luck.  ;)

That nvidia purge command is pro, thanks for the tip.

---

### Post by night_fox on 2009-06-14
lol I wish I could go to a party and get pissed on GFX problems!

---

### Post by Comzee on 2009-06-14
> **night_fox said:**
> lol I wish I could go to a party and get pissed on GFX problems!

Get an ATI card and your invited. hehe >.>

---

### Post by kokkus on 2009-06-16
So I shouldn't use Ubuntu's recommended drivers? Why are they even thre?
I forgot to mantion that this worked fine before I upgraded to 9.04. Also it worked fine in version 8.10. I don't wanna do all these PC expert / geek things if it can cost trouble. I saw one of the commands there was to stop the gnome display manager so it sounds "scary", and I mean Ubuntu shouldn't be made this advanced. It's a great OS but when it comes to fix problems I must say it's only user friendly for advanced PC experts and not normal PC users. I just want this thing to work for gods sake.
Isn't there an easier way to solve this? And does grub have anything to do with these problems since the kernel is from 8.10?

Edit: I don't know which Nvida card I have. I suppose I have to know that before I choose a driver, so where do I go to find that out? I think there's a terminal command for that but I am not sure.

---

### Post by kokkus on 2009-06-17
Bump

---

### Post by kokkus on 2009-06-20
Bump.

---

### Post by hyperdude111 on 2009-06-20
I too updated ubuntu yesterday and woke up to the same low graphics problem :(

Before I consider re-installing is there any way to fix this?

---

### Post by hyperdude111 on 2009-06-20
> **hyperdude111 said:**
> I too updated ubuntu yesterday and woke up to the same low graphics problem :(

Before I consider re-installing is there any way to fix this?


Firstly this is my 300th post WOO

Secondly :

I fixed this by, using the nvidia purge command then rebooting to the second kernel on grub .11 not .13 then I installed the graphics driver from a nvidia download and re-booted.

This fixed the .11 kernel the.13 still wont work.

---

### Post by kokkus on 2009-06-21
Ok so what command did you use to fix this?
There are like 100s of people here with this problem I suppose but I still can't figure out how to fix this. I should never update this ****. Everything worked just fine. When will Ubuntu work for normal (non pc geek) people? This is so frustrading me. And I don't wanna re-install it either.
So you said you ren a nvida command or something?

---

### Post by kokkus on 2009-06-21
I tried to install this driver now but it keeps saying No matching kernel. So as I told you before, I don't have any kernel from this ubuntu version (9.04), but only from version 8.04 which is waired. Where do I go to update my kernels?

---

### Post by kokkus on 2009-06-23
BUmp

---

