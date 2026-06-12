---
title: "Noob Help with Wireless Networking &amp; Admin Rights"
date: 2006-03-07
forum: Desktop Environments
---

### Post by KeepingTheFaith on 2006-03-07
Hello,

Im new to the forums and new to Linux. I've been wanting to try out Linux for a long time. A few friends directed me to Ubuntu and I liked it so last week I reformatted, partitioned 3 areas, (I have an 80 gig, I splitted into 60gigs for WinXp, 9.9gigs for Ubuntu, and 0.1gig as swap space). 

Im happy with the dual boot configuration and I am learning a lot, but I do seem to have some major problems.

1.) I cant get my Wireless Network card going, which is my only way to access the internet. (And without the internet, Im lost). It is a Belkin Wirless G Desktop Card, and the CD only comes with Windows drivers for it. This is my main problem at the moment.

2.) I am now able to see my "C:\" partition from WindowsXP, which is great, but it tells me I dont have the access rights to use it. Yet, if I go to Administration -> Hard Disks, after I type my password, I can see it and browse thorough it. Id like to fix that so I dont have to do that to access not only the main drive but also my D: drive.

3.) I installed the drivers for my NVIDIA Geforce 5200 but they dont seem to work. As a matter of fact, all the software I install from the package manager, (I also tried install the C++ compiler), does not seem to show up or work.

Any help I would and I would highly appreciate it. My view of Linux is only getting better, Im really liking it, and if I could solve those problems that would be A+.

Thanks,
Pablo

PS: According to what I've heard Linux is not only far more stable but should be much faster than Windows. Is this true?

---

### Post by Sutekh on 2006-03-07
[QUOTE=KeepingTheFaith]
1.) I cant get my Wireless Network card going, which is my only way to access the internet. (And without the internet, Im lost). It is a Belkin Wirless G Desktop Card, and the CD only comes with Windows drivers for it. This is my main problem at the moment.[/QUOTE]Yes this is definately your main problem, I'm not really sure where to look to get this working yet.

I would start here [The Ubuntu Wiki](https://wiki.ubuntu.com/UserDocumentation).  Section 4.3 has wireless info.

Is your card lised here? [https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards]("https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards")


[QUOTE=KeepingTheFaith]
2.) I am now able to see my "C:\" partition from WindowsXP, which is great, but it tells me I dont have the access rights to use it. Yet, if I go to Administration -> Hard Disks, after I type my password, I can see it and browse thorough it. Id like to fix that so I dont have to do that to access not only the main drive but also my D: drive.[/QUOTE]

To fix this you need to change your **/etc/fstab**.  The fstab is a file that specifies the way your partitions are 'mounted'.  You will need to modify the line that is in this file related to the Windows partitions (C: and D: )

This link is great for setting up Windows partitions in Ubuntu.

[http://www.psychocats.net/linux/mountwindows.php](http://www.psychocats.net/linux/mountwindows.php)

Let me know how this goes for you.

[QUOTE=KeepingTheFaith]
3.) I installed the drivers for my NVIDIA Geforce 5200 but they dont seem to work. As a matter of fact, all the software I install from the package manager, (I also tried install the C++ compiler), does not seem to show up or work.
[/QUOTE]Unfortunately most of the software is only available from the online repositories, so getting the NVIDIA drivers installed isn't going to be easy.  Fortunately some pacakges that you will need are still on the install CD

First use this link to install the C compiler that you will need to install the NVIDIA drivers

[Ubuntu Forums - HOWTO: Install gcc-3.4 via-apt get without an internet connection]("http://ubuntuforums.org/showthread.php?t=79896")

I tried this the other day and its pretty easy to setup


Once you get the C compiler installed follow this link (Method 2) to install the NVIDIA drivers

[Ubuntu Forums - HOWTO: Install Latest NVIDIA Drivers]("http://ubuntuforums.org/showthread.php?t=75074")


[QUOTE=KeepingTheFaith]
Any help I would and I would highly appreciate it. My view of Linux is only getting better, Im really liking it, and if I could solve those problems that would be A+.

Thanks,
Pablo

PS: According to what I've heard Linux is not only far more stable but should be much faster than Windows. Is this true?[/QUOTE]In *my* experience it is faster than Windows, but depending on your setup and hardware could be different.

---

### Post by deathbyswiftwind on 2006-03-07
for your wireless networking all you need is the windoze drivers and ndiswrapper which can be installed through synaptics. If you need any help understanding that let me know through a pm. As far as your drivers you could use automatix [http://ubuntuforums.org/showthread.php?t=80295](http://ubuntuforums.org/showthread.php?t=80295) which will install the drivers for you. As well as drivers automatix offers codecs for movies and other formats as well as lots of other nifty things

---

### Post by Sutekh on 2006-03-07
[QUOTE=deathbyswiftwind]for your wireless networking all you need is the windoze drivers and ndiswrapper which can be installed through synaptics. If you need any help understanding that let me know through a pm. As far as your drivers you could use automatix [http://ubuntuforums.org/showthread.php?t=80295](http://ubuntuforums.org/showthread.php?t=80295) which will install the drivers for you. As well as drivers automatix offers codecs for movies and other formats as well as lots of other nifty things[/QUOTE]
Which requires an internet connection.

[Ubuntu Packages - ndiswrapper-utils]("http://packages.ubuntu.com/breezy/misc/ndiswrapper-utils") is fortunately on the install CD
```
sudo apt-get install ndiswrapper-utils
```
[Ubuntu Wiki - ndiswrapper]("https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper")

---

### Post by KeepingTheFaith on 2006-03-07
**Sutekh**,

Thanks for the reply and support! I did find my Wirelss card in that list, Im excited! Its the F5D7000 . I then proceded on to feeling stupid and helpless as to what to do next. I tried the links but the documents dont exist. I dont know much about Linux, but I do want to learn!

As far as the access rights and mounting of the Windows partition and the rest of my problems, I am going to try your suggestions that when I log off the Windows session. Im using Windows right now obviously because I dont have my wireless network settings right on Linux and I did find a utility for Windows which allows me to use the Ubuntu file format. This is all so new to me-the different file formats. I didnt know there were that many! But as I mentioned, this really intrigues me and I want to learn more.

**deathbyswiftwind**,

Automatix looks absolutely awesome, I did want to download it but to my disapointment I read it does not work on A64. I have an AMD 2800 64-bit CPU, so that would include me I believe. Is there another package I could use?

Thank you both for the help! You both were very helpful, I will try the solutions right now and I hope to learn more about Linux.

---

### Post by deathbyswiftwind on 2006-03-07
do you have ubuntu 64 bit installed? i run ubuntu 32bit on my amd64 processor with the k7 kernel and works great and since your new to linux Id recommend the 32bit because there is alot more support for it Ive ran the 64bit but alas i chose to switch back

for ndiswrapper copy your driver.inf and driver.sys from your cd to your desktop
now open a terminal and enter 

sudo ndiswrapper -i ~/Desktop/whatever your driver.inf (replace drive with the name of inf file)

sudo modprobe ndiswrapper

sudo ndiswrapper -m

Now you may need to do a few extra things just in case your card is like the broacom (which I have) so if you need to just say and Ill look for you. Next go to system>administration>Networking you will need to config your card (probably wlan0) and then active it. After activiating it make sure you switch it to be the default gateway

---

### Post by KeepingTheFaith on 2006-03-07
Well, I tried the unmounting stuff for the harddrive. Some of the syntax the site provided dint work so I played aroudn until I figured it out. It worked alright! Im really liking the whole DOS comman-line type deal works. Anyway, it would be great if I knew how to make an alias so I can put it on my desktop.

As far as installing the C+ compiler, the method for installing it offline did not work because I am using the A64 architecture. At least that's the error it gave me. (And it did mention x386 on the package filenames when I downloaded them).

So is there any hope of using my Graphics Card? And how shall I go about installing my wireless card? (Now that I see it is in the list).

---

### Post by Sutekh on 2006-03-07
[QUOTE=KeepingTheFaith]Well, I tried the unmounting stuff for the harddrive. Some of the syntax the site provided dint work so I played aroudn until I figured it out. It worked alright! Im really liking the whole DOS comman-line type deal works. Anyway, it would be great if I knew how to make an alias so I can put it on my desktop.
[/QUOTE]If you found any errors post them here, the author of the guide [aysiu]("http://www.ubuntuforums.org/member.php?u=21941") might get a chance to see them.

By alias do you mean a shortcut to the partitions on your Desktop?

Two ways to do this

1 - a symbolic link, which is pretty much a shortcut, follow this general syntax
```
ln -s /<path of partition> <name of link> 
```
Changing <path of partition> to the 'mount point' (/windows?) you set up in the /etc/fstab, and <name of link> to whatever you like

2 - if the mount folder of the partition is under /media, ie /media/windows, then the partition should automatically show on the desktop.  

If not you can change this by opening the **Configuration Editor** in the Applications-> Accessories Menu.  Open the tabs on the left and look for apps -> nautilus -> desktop and click the check-box : **volumes_visibe**

For this to work the partition must be mounted under /media



[QUOTE=KeepingTheFaith]
As far as installing the C+ compiler, the method for installing it offline did not work because I am using the A64 architecture. At least that's the error it gave me. (And it did mention x386 on the package filenames when I downloaded them).

So is there any hope of using my Graphics Card? And how shall I go about installing my wireless card? (Now that I see it is in the list).[/QUOTE]
Ok you should be able to still do this, those .debs were for the i386 architecture but the AMD64 are available too.

These are the same files but AMD64 architecture

[http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-3.4/cpp-3.4_3.4.4-6ubuntu8_amd64.deb]("http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-3.4/cpp-3.4_3.4.4-6ubuntu8_amd64.deb")

[http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-3.4/cpp-3.4_3.4.4-6ubuntu8_amd64.deb]("http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-3.4/cpp-3.4_3.4.4-6ubuntu8_amd64.deb")

[http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-3.4/cpp-3.4_3.4.4-6ubuntu8_amd64.deb]("http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-3.4/cpp-3.4_3.4.4-6ubuntu8_amd64.deb")

See how that goes

When you try the NVIDIA howto pay attention to anything regarding the 64 bit  versions.

---

### Post by Sutekh on 2006-03-07
I think you're priority should be the wireless though.  Once you have internet setting up stuff in Ubuntu is soo much easier.

If you can follow this, it should get you going (not that I have *any* experience with Wifi yet)

[Ubuntu Wiki - Ndiswrapper on AMD64 Ubuntu]("https://wiki.ubuntu.com/HowtoUseNdiswrapperOnAmd64Ubuntu")

---

