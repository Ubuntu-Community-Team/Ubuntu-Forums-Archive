---
title: "Did I make a big mistake?"
date: 2012-06-13
forum: Desktop Environments
---

### Post by RogerDavis on 2012-06-13
I installed Wine 1.5 with the following commands:

        sudo add-apt-repository ppa:ubuntu-wine/ppa
        sudo apt-get update
        sudo apt-get install wine1.5
        sudo apt-get install winetricks

and got the following errors:
W: Duplicate sources.list entry [http://ubuntu.mirror.cambrium.nl/ubuntu/](http://ubuntu.mirror.cambrium.nl/ubuntu/) precise/main i386 Packages (/var/lib/apt/lists/ubuntu.mirror.cambrium.nl_ubuntu_dists_precise_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://ubuntu.mirror.cambrium.nl/ubuntu/](http://ubuntu.mirror.cambrium.nl/ubuntu/) precise/universe i386 Packages (/var/lib/apt/lists/ubuntu.mirror.cambrium.nl_ubuntu_dists_precise_universe_binary-i386_Packages)
W: Duplicate sources.list entry [http://ubuntu.mirror.cambrium.nl/ubuntu/](http://ubuntu.mirror.cambrium.nl/ubuntu/) precise/main i386 Packages (/var/lib/apt/lists/ubuntu.mirror.cambrium.nl_ubuntu_dists_precise_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://ubuntu.mirror.cambrium.nl/ubuntu/](http://ubuntu.mirror.cambrium.nl/ubuntu/) precise/universe i386 Packages (/var/lib/apt/lists/ubuntu.mirror.cambrium.nl_ubuntu_dists_precise_universe_binary-i386_Packages)
W: Duplicate sources.list entry [http://ubuntu.mirror.cambrium.nl/ubuntu/](http://ubuntu.mirror.cambrium.nl/ubuntu/) precise/main i386 Packages (/var/lib/apt/lists/ubuntu.mirror.cambrium.nl_ubuntu_dists_precise_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://ubuntu.mirror.cambrium.nl/ubuntu/](http://ubuntu.mirror.cambrium.nl/ubuntu/) precise/universe i386 Packages (/var/lib/apt/lists/ubuntu.mirror.cambrium.nl_ubuntu_dists_precise_universe_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems

I tried apt-get update, no help

Anyway, Wine seems to be installed, but I can't figure out how to install programs.  Also, it has locked up my machine once in about 20 minutes.

I need Quicken 2001 to work.  The Wine app database says "platinum".

I need Internet Explorer to work (It is needed for an online site need to use.)  The program called IE with the install won't even load the site.

When I checked for Wine install in Software Center, it was unclear which one to use, so I found the above instructions on line.  Should I uninstall this one and use the one in Software Center?  If so:
- How do I uninstall it?
- Which one (or all?!?) of the three different ones (Microsoft Windows Compatibility Layer, Q4Wine, Wine Windows Program Loader) in the Software Center do I install?

Help!?!

Update - I got the site to load, but when attempting to get to the page I need, I got the below:

CAUTION: The software on your computer does not meet the minimum requirements for using Diabetes AssistantSM Program.

The following table compares the minimum requirements with the software and settings on your computer. Before continuing, we recommend that you log out of Diabetes Assistant Program and upgrade the items shown in red.

Minimum Requirements: [COLOR="Red"]Your Computer[/COLOR]:
Operating System: Windows 98, Windows ME, Windows NT, Windows 2000, or Windows XP Home	[COLOR="Red"]Linux[/COLOR]
Web Browser: Microsoft Internet Explorer 5.5 Service Pack 1&2, Microsoft Internet Explorer 6. [COLOR="Red"]Netscape[/COLOR]
Cookies: Enabled Enabled
Java: Enabled Enabled

If I can get a "real" version of IE loaded and running, will it solve the above problems, including hiding Linux from the site?

---

### Post by taylorkh on 2012-06-15
I had the duplicate sources issue a while back. If you look in the file indicated > /var/lib/apt/lists/ubuntu.mirror.cambrium.nl_ubuntu_dists_precise_mai n_binary-i386_Packagesfor the offending entry e.g. > [http://ubuntu.mirror.cambrium.nl/ubuntu/](http://ubuntu.mirror.cambrium.nl/ubuntu/) precise/main i386 Packagesyou will find it more than once. You can, by running your editor with sudo, comment out or delete the extraneous entries. I think that is what I did if not something more drastic. Keep a backup of the original file if you want to be extra careful.

As to wine... When I wish to install a program I use the following technique.

1 - If wine is newly installed run from the menu Wine; "Configure Wine" It does not visibly do anything but it seems to setup some stuff in background.

2 - Place the Windows install file in a convenient location such as Desktop. For example I recently installed GrabIt on my new Linux installation on my netbook. The installer is called GrabIt172b6.exe

3 - Open a terminal and navigate to the location where the installer is located

4 - In my example, type > wine GrabIt172b6.exe [Enter]and allow the installer to run as it would on Windows. 

As to what version of wine... I loaded the current version 1.5.  It worked except that GrabIt would not connect to a Usenet server over ssl. It used to with wine 1.2.  I also installed wine 1.2 from the software center and it still did not work. I uninstalled wine 1.5 and nothing worked. I ended up doing a workaround outside of wine. Bottom line, wine is great but there are limitations and depending on how serious the limitations are and how tedious to resolve, I tend to take the path of lesser resistance.

Here is a path of lesser resistance I might recommend for your IE and IE specific web sites.  If you have sufficient resources on your PC you might install VMWare Player (free) and build a Windows virtual machine. It will be able to run the true Internet Explorer from a true Windows environment. I have an XP virtual machine which I use to run a couple of programs which do not run under wine and for which I have not found Linux replacements.

Feel free to ask if you need advise on VMWare. 

Ken

---

### Post by RogerDavis on 2012-06-15
I have run Configure, and managed to get my CD to show up.  However, it shows as CD ROM, and not as DVD or writer.  

CD is ok for now, if I can get it to go there and run an install from CD.

I need to install Quicken 2001, which is shown as "platinum", but how to do this from CD is a BIG blank spot for me.

VMWare could be useful.  Please tell me more about it.  Does it cost for individual use?  My budget is not huge.  I presume it will run in Ubuntu?  I can see the client in the Software Center, but I don't think this is what I need?

Thanks!

---

### Post by RogerDavis on 2012-06-15
I'm getting this error message over and over in Winetricks:

sha1sum mismatch! Rename /home/roger/.cache/winetricks/irfanview/iview428_setup.exe and try again.

Might this be a problem with Wine 1.5?  What should I do now?

If I open Uninstall Wine Software, there is a choice to install.  I select this, there is an Install option.  I select this, try to point it to the CD, but find the install disk at H: ?!?, and the test started to load.  How did the CD get to H:, when I set it at D: ?

---

### Post by taylorkh on 2012-06-15
I cannot tell you about winetricks. I have not played with that. VMWare I can tell you about.

There are 3 VMWare products which are of most interest to an individual.  

VMWare Workstation - Costs a couple of hundred $US. It lets you build virtual machines which are "guest" operating systems running on a host operating system.  I started with Windows XP as the host and tried various Linux distros as guest operating systems. This worked on a Pentium 4 with 3 GB of RAM. Not real fast but usable. Workstation has a lot of neat tools to do snapshots, rollbacks, clones etc. But I never took advantage of them.

Then I discovered VMWare Player which is FREE, no charge, no obligation. But I kept my Workstation license upgraded $$$ because I thought I needed it to create new virtual machines. Then I found that was not true.

VMWare Player will allow you to create a new virtual machine. The process is very simple. Launch Player, click on "Create a New Virtual Machine", follow the prompts. You can install the guest OS from a CD or DVD just as you would on a physical machine. Or, if you have download an iso file, just point the VM creator to the file. It will create the VM in a jiffy.

If you have a router on your home network I would recommend setting the Network Adapter of the VM to "Bridged".  This can be done by Customizing Hardware during the creation or after the fact. By using Bridged the VM will ask the router for an IP address just as a physical machine would. Just seems a little more strait forward to me.

The third product I have used is VMWare Converter. It allowed me to take a physical XP machine and scrunch it into a VM (a collection of files actually) which I copied onto my host PC. I was able to run the exact instance of Windows virtually. (Had to do with some coupon printing software which would not install in a virtual environment - to quote Inspector Lestrade of Shelock Holmes fame "There are those that are cunning and those that are cunninger)

As to host requirements... I am running a Core i860 with 8 GB of RAM and Ubuntu 10.04 64 bit as the OS. I have built and run Win XP, Win Vista, Win 7 and about every variety of Linux which I wanted to try as guests. I can run 3 or 4 guests at the same time and not run out of memory or processor provided I don't try to stress test all the guests.

Have a look here [https://my.vmware.com/web/vmware/evalcenter?p=player&ie=utf-8&oe=utf-8&client=ubuntu&channel=fs]("https://my.vmware.com/web/vmware/evalcenter?p=player&ie=utf-8&oe=utf-8&client=ubuntu&channel=fs") You will need to create an account at VMWare. You will get occasional offers, invites to seminars etc. Other than that they have never bothered me.

linuxquestions.org has a forum dedicated to virtualization [http://www.linuxquestions.org/questions/linux-virtualization-90/]("http://www.linuxquestions.org/questions/linux-virtualization-90/")

Give it a try, you may like it.  Do be sure to get the correct version for your PC 32 od 64 bit. uname -a will tell you which you are running if you are not sure.  

Good luck,

Ken

---

