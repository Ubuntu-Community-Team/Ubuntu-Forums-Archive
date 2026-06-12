---
title: "Is Ubuntu Right fro Me?"
date: 2008-09-28
forum: Desktop Environments
---

### Post by CHGN on 2008-09-28
I've always been kind of curious about what Linux is like, and now that I'm in University, i finely got a pretty good look at it in the Computer lab. I also just recently got a new Vista Laptop to play all my games on so that means I have an older desktop XP computer just basically laying around not doing much. I use it for the following:

-File Sharing via a USB Wifi Adapter with a Windows XP x32 and a Vista x64 Computer
-File Sharing a NTFS Hard Drive
-Playing the Following games: Fable The Lost Chapters, Halo Combat Evolved, and Maplestory
-Using a Microsoft Office Program

I'm just wondering that if I install Ubuntu, or another Linux platform, if i would still be able to do all these things. I suspect, more or less, I would be, but my main concerns are if my NTFS Hard drive would still work, if my Windows PCs would still be able to connect to a Linux and one, having a Word and PowerPoint Program compatible with Office 2007/XP, and , if possible, play all my old games.

Also, the main reason I'm looking for a switch is because my current system is really slow and I've heard that Linux is less demanding than Vista, I'm just wondering if it's less demanding than XP too.

Thanks for your help

---

### Post by ad_267 on 2008-09-28
I'm not sure about file sharing over wifi but I can't imagine that would be too much of a problem. There may be problems with some wireless adapters working with Linux. If you say what type of adapter it is someone should tell you if it will work fine.

File sharing with ntfs will be no problem. Ubuntu can read and write ntfs fine, but Windows can't read and write ext3 (the file system used by most linux distributions) without some addons.

You probably can't play most Windows games because they are Windows applications and most aren't available for Linux. It is possible for some games with something called wine. You can see here if your games will work: [http://appdb.winehq.org/](http://appdb.winehq.org/). Also there are some really good free games available for Linux you could try like Savage, Urban Terror, Nexuiz, Tremulous, Vegastrike and Alien Arena.

Again you can't run Windows applications in Linux but you may be able to get Office to run in Wine. That isn't really necessary though as Ubuntu comes with OpenOffice which supports .doc, .xls etc and will have much better support for .docx etc in the next version (3.0).

You can download the Ubuntu CD and boot your computer with the CD in the drive and try it without having to install anything onto your computer. Give it a go and see what you think.

I've found Ubuntu to be less demanding than XP, especially because you don't have to run an antivirus and firewall which hog resources. There are also more lightweight versions like Xubuntu you can try.

---

### Post by CorvisRex on 2008-09-28
Where to begin... Well first remember that one can always dual boot, which is always the best way IMHO if you are just starting out, or testing different distros to see which one you like.  but for you prerequisites..  

File sharing really is no problem.  either using it as a server or a client, there are many different ways for Linux to talk to windows and share files.  Obviously, Samba is the tried and true method.  But there are other ways.  Usually, since I only share files between my two machines only occationally, (my second machine is really just a test machine, I don't keep any critical data on it) Samba and SSH ( which really  just sets up a secure FTP connection) work well. Setting Linux up as a Samba server would allow you Vista machine to log on to it easily.  

Office apps:  Well, Open office comes with virtually every distro of linux, and works damn well.  I think (don't quote me) that the new version 3.0 is supposed to have better support for office 2007.  Personallly, I have never had any problems switching files back and forth.  But I also don't ever use powerpoint, so I couldn't help you there.

As far as games... Well, there is always Wine and Cedega, support for various windows games varies from game to game check out [http://www.winehq.org/](http://www.winehq.org/), or VirtualBox.  But for older machines, often times I just reboot into XP, just depends on the game.  If you set up to dual boot it is not really an issue.

And yeah, I think Linux runs alot better and faster on my older machine.

Hope it helps.

---

### Post by CHGN on 2008-09-28
Sounds like good news then. Dual Booting looks like the best way from your suggestions. However, I don't have much knowledge on  the subject. Is a disk Partition required? Can I readjust/Remove it after I partition it?
On the Networking Side, I'm just wondering if it is easier to set up permissions for other network users?(I want to give the Vista Full privileges and the XP read/write only) Also, I've had some Printer Sharing issues between my x64 Vista PC and my x86 PC and was hoping that I wouldn't have the same issue with Linux x86 and Vista x64.
The Wifi Adapter that I have is a Linksys WUSB54GC.

---

### Post by binbash on 2008-09-28
-Playing the Following games: Fable The Lost Chapters, Halo Combat Evolved, and Maplestory


No way to play maplestory without dualboot

---

### Post by ad_267 on 2008-09-28
Setting up the dual boot depends on how your partitions are set up already. If you just have one partition taking up an entire hard drive for Windows then the Ubuntu installer can resize this and make partitions for itself. Otherwise you really need to do the partitioning yourself using the partition editor on the LiveCD. You can resize and remove partitions easily later on. There's a partitioning guide at [http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

According to this page your wireless should work fine: [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsLinksys](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsLinksys)

What printer do you have? HP have very good Linux support, as do Epsom, but some of the others aren't so good.

---

### Post by CHGN on 2008-09-28
Well, first of all, I'm liking this community. I mean damn, this is the first forum (among dozens) where so many people have actually replied with something useful for me like links and such. Back on topic, I have a Epson RX500/600/or something like that. Also, I torrent a lot so a good program for that would be nice, since I'll probably use Ubuntu more since I only need XP for a few Apps/Games. Another thing is, if I Dual Boot, will I have to restart everytime I want to switch OSs or is it more of a Log off/Log on Situation?

---

### Post by ad_267 on 2008-09-28
Ubuntu has drivers for the Epson Stylus Photo RX500 and 600 and heaps of others there so looks like you should be able to set up the printer fine. I haven't had much experience with network printers but I don't think that should be a problem. This page might help: [https://help.ubuntu.com/community/NetworkPrintingWithUbuntu](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu)

Ubuntu has a torrent client installed by default (Transmission) but it is pretty basic and there are a lot of others available, have a look at [https://help.ubuntu.com/community/BitTorrent](https://help.ubuntu.com/community/BitTorrent)

Dual booting involves a restart to switch between operating systems. And yeah these forums are pretty great and a really good resource for information on Ubuntu. There is a lot of good information out there on Ubuntu and usually a google search gets what you need straight away. The wiki and community documentation are also very useful.

---

### Post by CHGN on 2008-10-01
OK, I've set up and installed Ubuntu (runs great) but I'm having trouble networking all of my shares and printers with Samba. Could someone give me a link for a guide for networking Ubuntu and Vista x64?
EDIT:
Okay, I fixed that myself. Sharing from Ubuntu to Vista is working fine. The new (and hopefully last) problem is that I can't access the files on my Vista machine onto my Linux machine. How do I fix this?

---

### Post by ad_267 on 2008-10-02
I'm not sure why you can't access your Vista machine files. The samba guide might help if you haven't read it already: [https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

---

### Post by CHGN on 2008-10-02
I think know what the problem is... My network discovery settings for the Vista Computer is set to Custom and the box that allows Network Discovery (letting computers in the network to see each 't other) is not ticked and whenever I select to change it, it doesn't save. Think this might be it?(Custom could mean that its enabled  guess.)

---

### Post by jack_the_nimble on 2008-10-02
I've done the same thing and had the same problem.  There are two things you can do here: one is to give up on Samba and use ssh.  You can grab putty for windows and that'll work, though I've never gone that route.  The other way is that if you using home premium, than there is a registry key you need to edit (I swear it's not that hard).  I'll try to remember where the key is and post back for you.

Edit: The need to edit the registry key could exist on other versions.  I had to edit mine, but a friend didn't have to on his, and we both run home premium.  It's kinda odd.

---

### Post by jack_the_nimble on 2008-10-02
1. Run the registry editor and open this key:

*Edit: In case you don't know, the easiest way to access the registry editor is to type "regedit" in the search bar under the start menu.*

    HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Lsa

1. If it doesn't already exist, create a DWORD value named
LmCompatibilityLevel

3. Set the value to 1

4. Reboot 

4 1/2 .  For me, sometimes after restarting the computer it's taken like five minutes or so for the computers to see each other.

4 3/4. Also in the location bar in the Gnome file manager try typing this (once you've changed the key) smb://*nameofcomputer*/*username* .  It should then prompt you for the user password and let you access that users documents.

---

### Post by CAPLinux on 2008-10-02
First off, Welcome to the Ubuntu Community CHGN.  I want to commend you in taking the plunge into a very exciting world.

I have been using Ubuntu for about the last two years and I still consider myself a Newbie, I am now using Ubuntu as my only Operating System and I am completely impressed.  I must also add, that I am an IT pro with 11 years of Microsoft troubleshooting and help desk experience, and I constantly find better support and help on the Ubuntu Forums then I ever do on any Microsoft site.  That in and of itself is worth the change to Ubuntu, not having any virus or security threats is a close second.  

If you have any questions feel free to contact me or just post in the forums, Everyone here is Awesome, and will help get you up and running!!

Again, Welcome to the team. :)

---

### Post by CHGN on 2008-10-02
> **jack_the_nimble said:**
> 
4 3/4. Also in the location bar in the Gnome file manager try typing this (once you've changed the key) smb://*nameofcomputer*/*username* .  It should then prompt you for the user password and let you access that users documents.

You are a Genius.:KS

But, now that I can access the other computer, whenever I try to open a file off of it, it tells me" [Whatever the default program is] does not know how to open remote file." Then it asks if I want to download the file to a temporary folder. Anybody have this problem before?

---

### Post by jack_the_nimble on 2008-10-02
Copy and paste your samba configuration file here. It's located at /etc/samba/smb.conf

My guess is that you don't have the right options set on the configuration file, and it's not really set up for what you're trying to do by default.  I'll try to get back here later tonight.

---

### Post by CHGN on 2008-10-02
Here's my configuration:

[global]
    ; General server settings
	netbios name = GAGANPC
	server string = 
	workgroup = parmar systems
	announce version = 5.0
	socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

	passdb backend = tdbsam
	security = user
	null passwords = true
	username map = /etc/samba/smbusers
	name resolve order = hosts wins bcast

	wins support = yes

;	printing = cups
	printcap name = CUPS

;	syslog = 1
	syslog only = yes
;	encrypt passwords = yes
;	guest ok = no
;	guest account = nobody

; NOTE: If you need access to the user home directories uncomment the
; lines below and adjust the settings to your hearts content.
;[homes]
    ;valid users = %S
    ;create mode = 0600
    ;directory mode = 0755
    ;browseable = no
    ;read only = no
    ;veto files = /*.{*}/.*/mail/bin/

; NOTE: Only needed if you run samba as a primary domain controller.
; Not needed as this config doesn't cover that matter.
;[netlogon]
    ;path = /var/lib/samba/netlogon
    ;admin users = Administrator
    ;valid users = %U
    ;read only = no

; NOTE: Again - only needed if you're running a primary domain controller.
;[Profiles]
    ;path = /var/lib/samba/profiles
    ;valid users = %U
    ;create mode = 0600
    ;directory mode = 0700
    ;writeable = yes
    ;browseable = no

; NOTE: Inside this place you may build a printer driver repository for
; Windows - I'll cover this topic in another HOWTO.
[print$]
	path = /var/lib/samba/printers
;	browseable = yes
	guest ok = yes
	writeable = yes
	write list = root
	create mask = 0664
	directory mask = 0775

[printers]
	path = /tmp
	printable = yes
	guest ok = yes
	browseable = no

; Uncomment if you need to share your CD-/DVD-ROM Drive
;[DVD-ROM Drive]
    ;path = /media/cdrom
    ;browseable = yes
    ;read only = yes
    ;guest ok = yes

[MyFiles]
	path = /home/samba/
;	browseable = yes
	read only = no
;	guest ok = no
	create mask = 0644
;	directory mask = 0755
	force user = ubuntu
	force group = ubuntu

[CHGN]
	comment = Portable Hard Drive
	path = /media/CHGN
	writeable = yes
;	browseable = yes
	guest ok = yes

---

### Post by jack_the_nimble on 2008-10-02
Okay, I think the file is a little more advanced for what you're trying to do.  Now I'm not quite an authority on the subject, but I recommend reading the man page for the file; just type man smb.conf at the terminal, but considering it's a little over seven-thousand lines of text it's quite a bit of a read.  Here's an easier option: 
1. Copy smb.conf to your home directory for backup purposes and rename it smb.conf-backup (or whatever).
2. Edit smb.conf to say this:

[global]
	workgroup = *your workgroup*
	security = SHARE
	auth methods = guest
	domain master = No
	wins support = Yes


[*whateveryouwanttocallyourshare]
	comment = mi home
	path = /home/*yourusername*
	writeable = yes
	guest ok = yes
	browseable = yes


If you've modified your registry than this should work, I know it works for me.  Samba is really cool and you should definitely read up on it.  The reason it works the way it does is that Windows uses the same protocol that samba uses (smb protocol) so this application is very powerful.

---

### Post by CHGN on 2008-10-02
That didn't work for me, but whatever, my Linux machine being able to have files transfered to it is the important thing. It's not like my Vista machine has anything I need to access from the Linux one.

A new thing I'm working on is installing a media transcoder onto my Linux machine so I can watch the movies/songs i put on it on my Wii, Xbox 360, and a bunch of Windows machines( something like Tversity). Any suggestions?

---

### Post by jack_the_nimble on 2008-10-03
Here's a couple of things you could try really quick before you give up:  

Before trying to mount the shares on either machine give it like five minutes or so from a fresh restart on both, and in the location bar on the file manager on the Linux box type smb://*yourcomputer*/*yourusername*

---

### Post by CHGN on 2008-10-03
The problem isn't not being to access it, the problem is i cannot remotely access files. I need to save them to the Linux machine before i can open/play them.

Also, whenever I play a video on the Linux machine, it comes out all pixelated (very blocky) while when i play it on Windows, it comes out really smoothed and, well, not pixelated (blocky)

---

### Post by ad_267 on 2008-10-03
> **CHGN said:**
> The problem isn't not being to access it, the problem is i cannot remotely access files. I need to save them to the Linux machine before i can open/play them.

Also, whenever I play a video on the Linux machine, it comes out all pixelated (very blocky) while when i play it on Windows, it comes out really smoothed and, well, not pixelated (blocky)

What kind of videos? Flash videos on the internet? Do you have the adobe flash player and ubuntu-restricted-extras?

---

### Post by jack_the_nimble on 2008-10-04
I'm not net+ or anything, but I would think that would have more to do with your throughput speed than anything else, and unfortunately, there isn't too much you can do to change that.  Or at least not too much I know to do.  You could try upgrading to wireless "n" protocol, assuming your hardware supports it (and assuming that one of you connections is wireless as it would be the limiter)

---

### Post by CHGN on 2008-10-05
It's just regular .avi files (Xvid) saved on my hard drive. I tried messing with some codecs ( by removing all the ones that came with the system) but that didn't fix it. I actually found another forum   post about it (lost the link) that said the problem was fixed by an Ubuntu update so I guess I just need to find it and install it(shouldn't it update by itslef?). Any ideas about how to do this?

---

