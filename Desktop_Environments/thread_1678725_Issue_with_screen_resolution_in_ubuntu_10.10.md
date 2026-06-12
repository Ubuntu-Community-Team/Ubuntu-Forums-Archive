---
title: "Issue with screen resolution in ubuntu 10.10"
date: 2011-01-30
forum: Desktop Environments
---

### Post by SILENT_Running on 2011-01-30
Hi, I recently decided it was about time I started using linux as i'd heard so many good things about it. I decided to use Ubuntu 10.10 on recommendation of a friend. Unfortunately I am unable to increase the screen resolution beyond 800x600. Following a bit of advice from an IRC chat friend I ran a few commands through the terminal, relating to the display settings. They are as follows:

unicron@Silent-Running:~$ lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 671MX
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS968 [MuTIOL Media IO] (rev 01)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] 191 Gigabit Ethernet Adapter (rev 02)
00:05.0 IDE interface: Silicon Integrated Systems [SiS] SATA Controller / IDE mode (rev 03)
00:0f.0 Audio device: Silicon Integrated Systems [SiS] Azalia Audio Controller
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 771/671 PCIE VGA Display Adapter (rev 10)
unicron@Silent-Running:~$ lspci -nn | grep VGA
01:00.0 VGA compatible controller [0300]: Silicon Integrated Systems [SiS] 771/671 PCIE VGA Display Adapter [1039:6351] (rev 10)
root@Silent-Running:/home/unicron# xrandr -q
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 640 x 480, current 800 x 600, maximum 800 x 600
default connected 800x600+0+0 0mm x 0mm
   800x600        61.0* 
   640x480        60.0  

I have also uploaded my Xorg.0.log file here [http://www.mediafire.com/?1puzpdrbdjvgcod](http://www.mediafire.com/?1puzpdrbdjvgcod) (incase that helps).
Any help would be greatly appreciated, or even a referral to a guide somewhere.
oh, and apologies in advance if i've posted this in the wrong place or have done something else a stupid and heinous.

---

### Post by cloudsconnection on 2011-02-25
Hey people, I've got the same problem, I'm using Ubuntu 10.10 my lspci is :

00:00.0 Host bridge: Silicon Integrated Systems [SiS] 671MX
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS968 [MuTIOL Media IO] (rev 01)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] 191 Gigabit Ethernet Adapter (rev 02)
00:05.0 IDE interface: Silicon Integrated Systems [SiS] SATA Controller / IDE mode (rev 03)
00:06.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:07.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:0f.0 Audio device: Silicon Integrated Systems [SiS] Azalia Audio Controller
00:1f.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 771/671 PCIE VGA Display Adapter (rev 10)
03:00.0 System peripheral: JMicron Technology Corp. SD/MMC Host Controller
03:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller
03:00.3 System peripheral: JMicron Technology Corp. MS Host Controller

How can I fix to use a better resolution??

---

### Post by houseworkshy on 2011-02-25
First I haven't used 10.10 yet as I now stick to the long term support versions ( 10.04.1 plus updates has sorted out the bugs which 10.04 had on being freshly released and is now superb IMHO, by the way )
Second the problem you describe has been one I have had to wrestle with on most of the recent .0 releases.
It has usually been an issue with the propriety hardware graphics driver.  

So the first thing to do is find out if yours is supported yet.  It is easy to find out if it is in the repros.  Go to System>Administration>Hardware Drivers and click it.  After you have entered your password your system will search for an appropriate driver online.  If it finds one ( which will depend on whether the manufacturer has put one there for 10.10 or not ) you will have the option to install it, if there is a choice of several go for recommend, then reboot as asked and that's it.  Done.
If not don't despair as there are probably choices anyway which will vary from card to card.  You'll need to know the details of your hardware so I'd recommend installing sysinfo.  Even if you do know the details it is easier to copy and paste than type it all out every time if you need to post...a handy tool to have around anyway, it grabs a bit more knowlage than you've posted and easily.  
You can do that via Applications>Software centre.  It will put a menu link in Applications>System Tools.  Use that and save it as whatever you want to call it and wherever is handy.  Once you know your card post again, with the info, if you don't find a solution elsewhere.  With luck someone will then be able to help. 

I notice that you are new to the forum, welcome in.  These guides are both free and very helpful if you are new to Ubuntu.

A good basic overview of Ubuntu in particular is available here

[http://ubuntu-manual.org/](http://ubuntu-manual.org/)

And there is another here

[http://www.ubuntupocketguide.com/download_main.html](http://www.ubuntupocketguide.com/download_main.html)

 Both free PDF downloads.

There is also this 


[http://sourceforge.net/projects/linuxcommand/files/TLCL/09.12/TLCL-09.12.pdf/download](http://sourceforge.net/projects/linuxcommand/files/TLCL/09.12/TLCL-09.12.pdf/download)


That's for in depth knowledge about linux in general should you wish for it sometime, and it is another freebie.

This is not related but if you haven't already then open a teminal and enter "sudo ufw default deny" it will ask for your password,  then enter "sudo ufw enable".  The ufw is the Ubuntu firewall, though this is installed by default it is not turned on ( well it may be in 10.10 but it wasn't in all previous versions, don't know why not ).  The guides will tell you about all that anyway but as you may be altering your system whilst online may as well be cautious.  Amother very useful command is "man"  this typed in front of any command brings up it's manual page, eg "man ufw" will tell you about ufw.

I'd recommend working through either of the more basic guides as a good way to start.   When I knew nothing at all that's what I did with the pocket guide one and after a couple of hours not only did I know the basics I had my system set up as I liked too.

Good luck with it all.

---

