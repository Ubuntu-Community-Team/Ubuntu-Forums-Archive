---
title: "Ubuntu boots up into colored bars and lines?"
date: 2006-01-08
forum: General Help
---

### Post by Protex on 2006-01-08
Hi there, just dual booted my system with XP and Ubuntu.

When I boot into Ubuntu, when the loading appears to be finished, and it is the time for Ubuntu to display a login screen (I'm assuming) I just just colored bars and lines going horizontally and vertically. I cannot do anything but restart the computer, and the same problem remains.

Anyone have any suggestions, I am very new to Linux (first time).

Don't think it's a graphic issue, and even if it was, I need my GUI to download and install the nVidia drivers for my 6600GT, (don't I?)

Thanks in advance.

*p.s: Just occured to me that this may be a monitor problem? I have an old Compaq P50 that's recognized under WindowsXP as 'default monitor'.

---

### Post by ubuntu27 on 2006-01-08
I suppose you also lost the color. Open any pic and watch. 

I had the same problem before. And a guy suggested it was my monitor's problem. 

Anyway, I truend off my comop and monitor and leave it for one day, and it returned at it's original state. I suppose my monitor was heated up... [ ???] 

Hope this helps.

---

### Post by Protex on 2006-01-08
[QUOTE=ubuntu27]I suppose you also lost the color. Open any pic and watch. 

I had the same problem before. And a guy suggested it was my monitor's problem. 

Anyway, I truend off my comop and monitor and leave it for one day, and it returned at it's original state. I suppose my monitor was heated up... [ ???] 

Hope this helps.[/QUOTE]

Thanks for the help, I was thinking I wasn't going to get a reply.

Unfortunately, I cannot make out anything it's completely messed up on boot to the GUI.

---

### Post by Protex on 2006-01-09
*bump*

I've even tried re-installing but it doesn't work, I really want to use Ubuntu because of Automatix. If anyone else can suggest another distro with a smilar program, please do. Thanks. =[

---

### Post by ubuntu27 on 2006-01-09
[QUOTE=Protex]*bump*

I've even tried re-installing but it doesn't work, I really want to use Ubuntu because of Automatix. If anyone else can suggest another distro with a smilar program, please do. Thanks. =[[/QUOTE]

I'm pretty much sure that it doesn't have anything to do with Software / Operating System since when I had that problem not only was my Ubuntu affected but Windows XP too!

So, it must be hardware, either the Monitor or the Video Card....

Changing the OS won't help. 

Try switching Monitor [borrow from someone if you don't have another computer] and see if it still "semi-color-blind/lost" 
If it solved the problem by switching the monitor, then it was your monitor's fault :)

---

### Post by southernman on 2006-01-09
Question: If you restart your box and select your windows OS in grub, will/does your monitor work as expected?

If not, see below

Along with what ubuntu27 suggested you may want to try these two things:

1 - shut down your box. Once it's down, unplug the power cord - pull out your video card - reinstall video card making sure it's seated properly.

2 - If you have an old video card laying around, try it out just for kicks. Regardless of how new a piece of electronic equipment is, it's liable to go out at any time for various reasons

---

### Post by Protex on 2006-01-09
[QUOTE=southernman]Question: If you restart your box and select your windows OS in grub, will/does your monitor work as expected?

If not, see below

Along with what ubuntu27 suggested you may want to try these two things:

1 - shut down your box. Once it's down, unplug the power cord - pull out your video card - reinstall video card making sure it's seated properly.

2 - If you have an old video card laying around, try it out just for kicks. Regardless of how new a piece of electronic equipment is, it's liable to go out at any time for various reasons[/QUOTE]

Yes, windows works perfectly fine. Even for gaming!

I will try the monitor switching suggestion, but if Ubuntu only work on my other monitor, I will need to consider a new distro (as I would like to use this monitor, the other one is a bit fried and displays a yellow shade over everything.

Thanks for the help, anyone else out there, feel free to suggest anything!

---

### Post by stevec on 2006-01-09
Is this a brand new install. If so you may need to reconfigure xserver.xorg

---

### Post by Dr. Nick on 2006-01-09
When you installed it how did you set up xorg? By default it wont give you much options to configure your monitor, but if you change an option in the configure of xorg you can defne the charestics of your monitor. It is something like "detail level" if I recall. I had similar symptoms due to bad colordepth setting for my video card. Have you been able to boot into recovery mode using grub? It will not load a gui but instead a command line. And you can do all nvidia driver install from a command line, no gui needed.

---

### Post by southernman on 2006-01-09
[QUOTE=Protex]Yes, windows works perfectly fine. Even for gaming!

I will try the monitor switching suggestion, but if Ubuntu only work on my other monitor, I will need to consider a new distro (as I would like to use this monitor, the other one is a bit fried and displays a yellow shade over everything.

Thanks for the help, anyone else out there, feel free to suggest anything![/QUOTE]

If your monitor works with windows (your monitor isn't the problem, nor is the distro), it WILL work with ubuntu!

My next guess would be that during the installation of ubuntu you choose screen resolutions higher than what your card/monitor will accept.

[edited out the cowardly way to solve this]

To go along with Dr. Nicks suggestion here is a [good link]("http://ubuntuforums.org/showthread.php?t=83973") to give you a little direction with the xorg config file.

---

### Post by Protex on 2006-01-09
[QUOTE=Dr. Nick]When you installed it how did you set up xorg? By default it wont give you much options to configure your monitor, but if you change an option in the configure of xorg you can defne the charestics of your monitor. It is something like "detail level" if I recall. I had similar symptoms due to bad colordepth setting for my video card. Have you been able to boot into recovery mode using grub? It will not load a gui but instead a command line. And you can do all nvidia driver install from a command line, no gui needed.[/QUOTE]

Can you maybe type the commands I will need to download the nVidia driver? I will give that a go. (I have a GeForce 6600GT)

And yes I can boot into recovery mode, just not any GUI.

---

### Post by Protex on 2006-01-09
[QUOTE=southernman]If your monitor works with windows (your monitor isn't the problem, nor is the distro), it WILL work with ubuntu!

My next guess would be that during the installation of ubuntu you choose screen resolutions higher than what your card/monitor will accept.

Being that ubuntu is soooooo easy and fassssssst to install, I'd give the installation another shot[/QUOTE]

I have reinstalled three times. The first selecting 1280*1024 as a resolution (my monitor can support in XP) and the second and third time, leaving the resolution settings at default.

---

### Post by stevec on 2006-01-09
From the prompt in recovery mode type

    sudo apt-get install nvidia-glx
    sudo apt-get install nvidia-settings
    sudo nvidia-glx-config enable

You might need to install xserver-xorg first
     sudo apt-get install xserver-xorg

---

### Post by Dr. Nick on 2006-01-09
the above should get you the nvidia drivers. IF you get a package not found error then run
[B]sudo nano /etc/apt/sources.list
[/B]and read that file and remove the #'s to enable universe and the others then hit ctrl+x to save and exit
then run **sudo apt-get update  **and try it again.

I doubt this is easily possiby, but a look at your /etc/X11/xorg.conf file would be helpful, but you would have to retype it all which isnt worth it yet.

You could try to turn down color depth though which solved it for me. To do this run **sudo nano /etc/X11/xorg.conf **look for the line that says  somethinng like default depth and change it from 24 to 16 then save and reboot.

---

### Post by Protex on 2006-01-09
[QUOTE=stevec]From the prompt in recovery mode type

    sudo apt-get install nvidia-glx
    sudo apt-get install nvidia-settings
    sudo nvidia-glx-config enable

You might need to install xserver-xorg first
     sudo apt-get install xserver-xorg[/QUOTE]

Wow, I did that and everything works fine. Thank you very, very much.

I'm excited about using Ubuntu, and will probably be back with a lot of questions! Thanks again!

---

### Post by Dr. Nick on 2006-01-10
Cool glad that worked. I have a nvidia card and have never seen that happen. Maybe its a bug that only hurts newer cards, Im sitting here with a geforce 4 mx which is years old and has had time to be mostly ridden of bugs.

Welcome to ubuntu and I am sure most of your questions can and will be answered by someone.

---

### Post by stevec on 2006-01-10
Your very welcome Protex. I have gained so much help reading this forum. 
 It feels good to give something back no matter how small

---

### Post by southernman on 2006-01-10
Congrats Protex... FWIW, I had edited my last post while you were quoting it I guess.

I added a link to a pretty good xorg.conf howto [here]("http://ubuntuforums.org/showthread.php?t=83973")

It also has some other good links in it.

---

### Post by ubuntu27 on 2006-01-11
Hey Protex ! It's good to know that you solved the problem :)
Good job :D

Now if you have more questions, just create a another thread in the appropriate forums ;)

---

