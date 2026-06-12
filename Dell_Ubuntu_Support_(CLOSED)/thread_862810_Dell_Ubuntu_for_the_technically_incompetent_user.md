---
title: "Dell Ubuntu for the technically incompetent user"
date: 2008-07-17
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Janeleaper on 2008-07-17
I'm posting this for anyone like me, who has bought, or is thinking of buying a Dell Ubuntu pc for personal use, but does not have any technical knowledge. 

I unpacked my Inspiron Ubuntu two days ago and having got it up and running I'm very happy with my purchase. I'm particularly delighted by the way Ubuntu found my internet connection and connected itself to my home network without me having to do anything except connect the ethernet cable. Magic!

Points to note:

Dell are not doing enough (in my opinion) to warn customers that most of their printers will not work with Ubuntu. The information is there on their website, but you need to look for it.  If you do buy the wrong printer - there is a 30 day money back guarantee.

Dont' try to get technical advice on Ubuntu from Dell's dreaded call centre (they don't know anything). If you haven't paid for advice from Canonical, use this forum, or the other Ubuntu support links bookmarked in Firefox.

The installed Firefox web browser has BBC headlines bookmarked but Real Player is not installed, which you need to listen to BBC radio or watch BBC news.  However, I found a download quite easily and had no problems with installation.

French chanson is probably a more esoteric taste than BBC news, but I still can't find a linux compatible media player that will play Radio Canada's french radio station Espace Musique.

I transferred my favourites from Windows, but can't get Firefox's Bookmarks manager to import them.  I'm going to have to enter them manually. However that is the only problem I've had transferring my data from Windows.  Open Office has no problem with any of my documents and the photo software is excellent.

I expected most difficulty in integrating the Ubuntu pc into my home network and bought on the basis that I'd do without a network if necessary.
So, I'm very happy to have a network, even though it doesn't work perfectly.  The Ubuntu computer is connected by ethernet cable to the router.  Our two Windows XP pcs can connect to the internet wirelessly, but can't access the shared folder on the Ubuntu machine (but can access the shared folder on each others). The Ubuntu machine can access the shared folders on the XP machines, but can't print off the printer attached to one of the XP machines. Apparently the shared file problem is solveable, but it is not a big enough issue for me to spend more time trying to solve it.

Ubuntu does have the software to open pdf documents.  I'm saying this because I got messages when I was opening email attachments telling me I needed Adobe.  I didn't.

I hope  all this is helpful to someone.

---

### Post by anjilslaire on 2008-07-18
To get your bookmarks the easy way:

On Windows, in IE, choose File > Export. Then export your bookmarks to an html file (usually bookmarks.html)

Take this file to your Ubuntu system (usb drive, email, whatever) and open Firefox. Go to Bookmarks > Organize Bookmarks > Import * Backup.

Follow the wizard, and point it to your bookmarks html file. It should import them just fine.

I just did this last week for my Uncle's new Ubuntu Inspiron :)

---

### Post by Potatoj316 on 2008-07-18
For your shared directories on Ubuntu you have to install SAMBA.  In a terminal type (no quotes) "sudo aptitude install samba" When creating the shared directories you may have to specify a Windows share.

---

### Post by Janeleaper on 2008-07-18
Samba came pre-installed with my computer, and I took some advice from this forum (the Absolute Beginners forum) for it.  It didn't work, but frankly Samba is a bit too technical for me.  I don't feel confident working with terminal.

---

### Post by Janeleaper on 2008-07-18
An amendment to my previous post.  This am I followed the updater's suggestion that I downloaded and installed the newest version of Ubuntu - Hardy Heron.  It did not work, and has taken up most of my day sorting it out.  I've had to reinstall version 7.10, supplied by Dell, and now have to import my windows data, set up my network again and so on.  Very annoying.

---

### Post by Janeleaper on 2008-07-19
Just to say that thanks to this post: [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

I have RealPLayer and MPlayer installed and embedded in Firefox, so I can now listen to Radio Canada's Espace Musique as well as the BBC.

---

### Post by RedRat on 2008-07-20
As to Dell support, did you call the LINUX SUPPORT line?? Their regular Dell Support knows nothing of linux and I am not surprised if you got hold of them. If you are calling from North America try using the following number: 866-622-1947.

As to running Hardy (8.04), I am running Hardy on a Dell 530n which came with 7.10 pre-installed. Through my own fault, I wiped the disk accidentally trying to install Ubuntu-Studio and had to install plain old vanilla Ubuntu 7.10, I upgraded to 8.04 in April. I have had no problems running either version. I did have some initial problems with the NVidia card and getting Compiz to work, but with the upgrade to Hardy, those problems seem to have gone away.

Stick with it and keep trying, you will find Ubuntu to be quite a useful operating system. I pretty much have given up on Windows.

---

### Post by Janeleaper on 2008-07-21
Thanks for that.  What method did you use to upgrade to 8.04?  I've tried the upgrader four times now and it stalls.  That kind of thing annoys me so I tried downloading 804 onto a disc.  I did it from my old Windows XP.  When I put it in the Ubuntu machine it refused to boot from the disc.  So, I've given up for the time being.

---

### Post by worx101 on 2008-07-21
> **Janeleaper said:**
> Thanks for that.  What method did you use to upgrade to 8.04?  I've tried the upgrader four times now and it stalls.  That kind of thing annoys me so I tried downloading 804 onto a disc.  I did it from my old Windows XP.  When I put it in the Ubuntu machine it refused to boot from the disc.  So, I've given up for the time being.

Best just stick with 7.10.  But you probably just have a bad cd-image file.  If you must have 8.04(for whatever reason) try to redownload it.

---

### Post by mehtdosa11 on 2008-07-21
> **worx101 said:**
> Best just stick with 7.10.  But you probably just have a bad cd-image file.  If you must have 8.04(for whatever reason) try to redownload it.
try burning the ubuntu iso on your linux machine. i had major problems burning iso's on my windows machine. however they seem to work everytime using linux.

also a fresh install of 8.04 worked far better than when i did my original upgrade.

---

### Post by lunkupe on 2008-07-21
hii gies i will want to offer u support on the dell for ubuntu.so just get me a private messages and i will respond to all your needs.thank u

---

### Post by Potatoj316 on 2008-07-21
When I tried to upgrade from 7.10 to 8.04 the updater messed up and I had to start over with a clean install of 8.04 (from a CD I burned)

---

### Post by RedRat on 2008-07-21
> **Janeleaper said:**
> Thanks for that.  What method did you use to upgrade to 8.04?  I've tried the upgrader four times now and it stalls.  That kind of thing annoys me so I tried downloading 804 onto a disc.  I did it from my old Windows XP.  When I put it in the Ubuntu machine it refused to boot from the disc.  So, I've given up for the time being.

As I noted in my post, I loaded 7.10 from the Ubuntu disk that Dell shipped with my machine. This is straight Ubuntu without and Dell special favors, if you will. Because I made a terrible botch up of installing Ubuntu Studio, and also being a novice, I wiped my hard drive clean, got rid of all the partitions and installed brand new from scratch, so to speak. So my installation was pretty vanilla Ubuntu. 

For my upgrade, I did it through Synaptic Manager. I got notices from Synaptic that the new release was available and just went ahead and allowed synaptic do the install. I have a broadband connection so did not need the 8.04 disk.

I have seen both here and also in the Ubuntu newsgroups, that installation from the disk can sometimes be tricky. If you download the iso-file and you must do at least two things: 1) run the checksum on the download, and 2) burn the disk at a lower speed than the maximum. In regard to the latter, when I burned disks before I let them burn at max and did not seem to have a problem. This may have more to do with your particular machine, specifically how much memory you have and how fragmented you disk might be. 

Hope that this helps.

---

### Post by RedRat on 2008-07-21
To those who might be experiencing problems with the disk, you can buy for a nominal price the disks fron Canonical. I think they are about $10US or so. This way you are guaranteed a good quality disk.

[https://shop.canonical.com/index.php?cPath=17&osCsid=cf0f21e28d71b5864f1025ca6e93107d](https://shop.canonical.com/index.php?cPath=17&osCsid=cf0f21e28d71b5864f1025ca6e93107d)

---

### Post by Janeleaper on 2008-07-21
Thanks for these comments.  Difficulty with burning cds on my XP machine is nothing new, and I am going to try on the Ubuntu machine.  Can you tell me if it matters whether I use a CD R or CD RW ?

---

### Post by falcon61102 on 2008-07-21
I've heard people having problems with RW versions of both CD's and DVD's when burning Ubuntu discs.  My recommendation is to use an CD-R and burn it slow if you are worried about problems.  

Also, be sure you run the Check CD prompt when you boot from the LiveCD the first time to ensure you have a good copy before trying to install.

---

### Post by RedRat on 2008-07-21
> **Janeleaper said:**
> Thanks for these comments.  Difficulty with burning cds on my XP machine is nothing new, and I am going to try on the Ubuntu machine.  Can you tell me if it matters whether I use a CD R or CD RW ?

I would suggest you use a CD-R or CD+R, which one should not make a difference. If you machine is older and/or the CD burner is older, that might present some problems. The reason for the slower speed, especially under Windows, is that the disk can be badly fragmented and therefore the head is doing a lot of searching for the file fragments while trying to burn the disk. I would suggest that you de-frag you hard drive that might help. CD burners do crap out, I have a very flaky Plextor on my XP machine which really needs to be replaced. Certainly do a checksum on the downloaded file as others have suggested. Also see my other post (above) that you might think about just ordering a disk from Canonical.

---

### Post by Szyfrow on 2008-07-22
If yor machine doesn't boot from the install CD, try the 'alternate CD': [=http://releases.ubuntu.com/8.04/ubuntu-8.04.1-alternate-i386.iso](=http://releases.ubuntu.com/8.04/ubuntu-8.04.1-alternate-i386.iso)

---

### Post by Szyfrow on 2008-07-22
Further to my previous quote, see also [https://help.ubuntu.com/community/Installation#Installation%20using%20the%20Alternate%20CD](https://help.ubuntu.com/community/Installation#Installation%20using%20the%20Alternate%20CD)

---

### Post by Melindrea on 2008-07-22
A problem I had... Have you checked that it actually boots from CDs? My Dell laptop (Vostro 1000, XP preinstalled) needed that set.

In the beginning of bootup, there'll be an option to go to the bootmenu, though I can't remember which button you use for it.

Good luck!

---

### Post by Janeleaper on 2008-07-22
My pc will boot from a cd if I tell it to -- F12 Boot menu

I've made two attempts to burn a cd from my Gutsy Gibbon computer.  Neither worked. Both had errors.  I'm going to order the cd!

---

### Post by RedRat on 2008-07-22
> **Janeleaper said:**
> My pc will boot from a cd if I tell it to -- F12 Boot menu

I've made two attempts to burn a cd from my Gutsy Gibbon computer.  Neither worked. Both had errors.  I'm going to order the cd!

Out of curiosity are you trying to burn with Brasero or GnomeBaker? I have had difficulties burning with Brasero but not GnomeBaker.

---

### Post by Janeleaper on 2008-07-22
I don't know which application this pc uses to burn discs and don't know how I'd find out. Sorry.

---

### Post by RedRat on 2008-07-22
> **Janeleaper said:**
> I don't know which application this pc uses to burn discs and don't know how I'd find out. Sorry.

You said you were burning these files under Ubuntu, is that what you meant? Or are you burning under Windows XP? I assumed that you were running Gutsy (7.10). 

If you are using Windows, you will need a burning program such as Roxio or Nero. If you are running Ubuntu 7.10, I would suggest that you use GnomeBaker (you can download it from Synaptic).

---

### Post by Janeleaper on 2008-07-22
Sorry, but I don't have any technical knowledge and I don't know how to tell which programme I used to burn the disc.  I burned the last disc on the 7.10 machine. That's all I know. I downloaded, put a disc in the machine and followed the instructions to burn.

I know how to get up a list of installed programmes on Windows but I don't know how to do it on Ubuntu.

---

### Post by falcon61102 on 2008-07-22
Go to Applications>Add/Remove and open up that.

Once it starts up, you will see that the screen is divided into three sections.

Make sure that All is highlighted in the section on the left, and then you should see a drop-down menu box that has a number of options.  One of those options should be something like Show Installed Items Only.  Once you click on that, only installed applications will be shown in the righthand top section.  You can further narrow the search by clicking on the categories in the left section.

---

### Post by RedRat on 2008-07-22
> **Janeleaper said:**
> Sorry, but I don't have any technical knowledge and I don't know how to tell which programme I used to burn the disc.  I burned the last disc on the 7.10 machine. That's all I know. I downloaded, put a disc in the machine and followed the instructions to burn.

I know how to get up a list of installed programmes on Windows but I don't know how to do it on Ubuntu.

If you are running 7.10 you can upgrade from the Synaptic Manager, at least I was able to do that. Synaptic Manager should have told you that you can upgrade to Ubuntu 8.04 LTS and give you the option to do that. I would only recommend doing it with some form of broadband connection. When I did my upgrade, that is how I did it. It did take some time because the repositories were quite busy so I just let it run overnight. It took quite a few hours. But now that most people have upgraded, I would think it should go pretty fast. 

Since you are just beginning, I would suggest that you use Synaptic Manager for upgrading and adding programs from the appropriate repositories. You might try using it to download Gnomebaker. Several points here: When you open Synaptic, first click on the RELOAD button in the upper left corner, then click on all in the left panel, then do a search for Gnomebaker. You will see gnomebaker in the lower panel, click the little box and then go up above and APPLY. This will then install the program. 

Once you have Gnomebaker installed you will then be presented with the options of making a DATA DVD, DATA CD, AUDIO CD. Depending on whether you downloaded the Live CD or the DVD click the appropriate button. Then use the window to find your iso image file and drag it or merely click on the file and then click the ADD button. Put your disk in your burner and then click BURN (IN THE LOWER RIGHT CORNER). It does all the rest.

---

### Post by Janeleaper on 2008-07-22
When you said this before - about Synaptic, I did a Google search and found the Synaptic home page, which might as well have been written in Mandarin chinese, for all the sense it made to me.

When I used the words 'technically incompetent' in the title of this thread I meant it. When I see sentences like: "It provides the same features as the apt-get command line utility with a GUI front-end based on Gtk+." I am completely lost.  I don't know what an apt-get command line is, or a GUI front-end on Gtk+. So, there is not much point in my even attempting to use Synaptic.

I've ordered the 8.04 disc and a book on Ubuntu. Hopefully, once I've read it, some of this stuff will start to make sense.

---

### Post by pablo180 on 2008-07-22
> **Janeleaper said:**
> Samba came pre-installed with my computer, and I took some advice from this forum (the Absolute Beginners forum) for it.  It didn't work, but frankly Samba is a bit too technical for me.  I don't feel confident working with terminal.

Had a similar problem on my Dell with Samba, it was pretty easy to fix without using the terminal. You may have already done this but if not...

Open System > Admin > Shared Folders

Click Add and choose the folder you want to share (Other in path and then Navigate to it). Make sure Share Through Windows Networks (SMB) is chosen. 

Give it a name and make it read only (or not), then press OK. It should appear in the window now. 

If you click the next tab - General Properties - you can set your domain/workgroup which should be the same as the domain/workgroup on your windows PCs (this should be WORKGROUP if you haven't changed it in windows). 

That should be it, your windows PCs should now be able to access your Ubuntu share and vice versa.

To check go to Places > Network - your Ubuntu Share should appear there now. 

Another problem that I had was Samba not working when resuming from hibernation, going to System > Services and then unticking Folder Sharing Service (samba) and then ticking it again sorts this out.

---

### Post by RedRat on 2008-07-22
> **Janeleaper said:**
> When you said this before - about Synaptic, I did a Google search and found the Synaptic home page, which might as well have been written in Mandarin chinese, for all the sense it made to me.

When I used the words 'technically incompetent' in the title of this thread I meant it. When I see sentences like: "It provides the same features as the apt-get command line utility with a GUI front-end based on Gtk+." I am completely lost.  I don't know what an apt-get command line is, or a GUI front-end on Gtk+. So, there is not much point in my even attempting to use Synaptic.

I've ordered the 8.04 disc and a book on Ubuntu. Hopefully, once I've read it, some of this stuff will start to make sense.

Sorry, I didn't realize you are a beginner--more power to you for even trying!! Synaptic Package Manager is a part of your Ubuntu installation. In your Ubuntu Window, look up at the very top of the screen at the tool bar on the top (if you have the default installation) and you will see three words:
APPLICATION, PLACES, SYSTEM. 
Click on SYSTEM, you will get a drop down menu and you should see at the top of the menu PREFERENCES and ADMINISTRATION. Click on ADMINISTRATION and scan down the drop down list. You should find SYNAPTIC MANAGER OR SYNAPTIC PACKAGE MANAGER. Click on that and that will open the Synaptic Package Manager. You will be prompted for your password. Enter that and the manager will open.

---

### Post by Sef on 2008-07-22
> Go to Applications>Add/Remove and open up that.

Once it starts up, you will see that the screen is divided into three sections.

Make sure that All is highlighted in the section on the left, and then you should see a drop-down menu box that has a number of options. One of those options should be something like Show Installed Items Only. Once you click on that, only installed applications will be shown in the righthand top section. You can further narrow the search by clicking on the categories in the left section.

Applications > Add/Remove > Show: Change to 'All Available Applications' > Search: GnomeBaker > Check on the box next to Gnomebaker > Apply Changes > Apply > Close

---

### Post by Janeleaper on 2008-07-23
Progress report:

I discovered that I did not have Flash installed (I thought I did).  With flash installed my media problems seem to have disappeared. 

That just leaves me with the network problem, which does not cause me much inconvenience anyway.  When I'm feeling strong enough I'll start grappling with Samba.

---

### Post by Szyfrow on 2008-07-26
Hi Janeleaper, Once again, why not try the alternate CD? I chose that road when installing 7.04. There is also an alternate CD for 8.04. Here is the link to the installation instrcutions (it's for 7.04 but I expect it to be the same for 8.04): [Installation I386](https://help.ubuntu.com/community/Installation/I386).

---

### Post by Janeleaper on 2008-07-26
Thanks for the link, but I've already ordered the cd.

---

### Post by Szyfrow on 2008-08-09
> **Janeleaper said:**
> Thanks for the link, but I've already ordered the cd.
Got it yet?

---

### Post by Janeleaper on 2008-08-11
Yes, I have the cd.  In fact I ended up with two because I got another copy with 'Ubuntu for non-geeks'.  I've also been looking at this thread in the installations forum: 	

Go to first new post [ubuntu] Hardy 8.04 update freezes on generating locales (Multi-page thread 1 2 3 ... Last Page) 

It describes what happened to my machine when I tried to upgrade.

I can't do anything with the cd.  Nothing happens when I put it in my machine.  I'm not bothered. I've got too much stuff on my machine now to want to lose it all if the upgrade does not work, so I'll stick with 7.10.

---

### Post by Szyfrow on 2008-08-12
Sounds reasonable if 7.10 answers your needs. Just remember that there is such a thing as an alternate CD for installing Ubuntu ... you never now. Please also note that in case your operating system gets mixed up all hope is not lost. In that case you throw in a bootable Linux CD which enables you to access your data on a PC with a corrupt operating system. One user-friendly (yes non-geek :)) example is Knoppix  [(see this link)](http://www.knopper.net/knoppix/index-en.html), which I used once to access data on a PC that didn't want to boot anymore (a Windows system by the way - Knoppix understands both Windows and Linux file systems. Keep this in mind should that dark and stormy night arrive that you are fearing so much ;). Or, better even, try it out in advance to see how it works. I wish you success!

---

