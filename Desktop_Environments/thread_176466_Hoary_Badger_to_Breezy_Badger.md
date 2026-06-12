---
title: "Hoary Badger to Breezy Badger?"
date: 2006-05-14
forum: Desktop Environments
---

### Post by ronniet on 2006-05-14
Yes, ***Hoary Badger***. Thats what i'm calling my Linux at the moment.

I've tried God only knows how many times to upgrade from Hoary to Breezy but all i'm getting now are errors, slow internet, KDE isn't loading and my login prompt (coz thats all i get) still saying Hoary Hedgehog!  ](*,) 

So i think i've got a Hoary/Breezy hybrid... :confused: 

**My question is this :**
If I download the Breezy Badger ISO and install it using boot from CDROM, will it install Breezy over Hoary **_WITHOUT_** losing my data and settings??  :-k 

Or will i end up with a triple boot (Windows/Hoary/Breezy)?

My linux is in such a state that i'm having to use my Windows again  :mad: 

Any advice would be _much_ appreciated.

---

### Post by aysiu on 2006-05-14
[QUOTE=ronniet]
I've tried God only knows how many times to upgrade from Hoary to Breezy but all i'm getting now are errors, slow internet, KDE isn't loading and my login prompt (coz thats all i get) still saying Hoary Hedgehog!  ](*,) [/quote] Can you describe the upgrade steps you took?

> If I download the Breezy Badger ISO and install it using boot from CDROM, will it install Breezy over Hoary **_WITHOUT_** losing my data and settings??  :-k  Only if you have a separate /home partition.

> 
Or will i end up with a triple boot (Windows/Hoary/Breezy)? If you choose the resize the current partition and use free space option, then, yes.

Why don't we concentrate on trying to get the upgrade to work?

---

### Post by ronniet on 2006-05-14
[QUOTE=aysiu]Can you describe the upgrade steps you took?

Why don't we concentrate on trying to get the upgrade to work?[/QUOTE]

**Hi, thanks for taking the time to read my rating post... ** :D 

Ok, Initially I installed Ubuntu.
Then I installed the Kubuntu-Desktop.
With Gnome taking up space, i used Synaptic to remove most of the Gnome stuff.
With (false) courage I attempted an upgrade from Hoary to Breezy, had to download about 200mb of stuff so left it overnight. On returning I could see from the prompt that there were a few errors, stuff it couldn't replace. But it was still showing itself as Hoary.
I tried a 'from prompt' upgrade using apt-get (update/distro upgrade), again, 200mb so left it this afternoon. Again, a few errors (sorry, i didnt write down the errors as i assumed all would go well anyway, used to that in Windows ;)  )
On rebooting i can see it saying starting KDE it then TRIES to sort out a resolution (i assume!) and pops back to the prompt.
I've tried dpkg reconfigure on xserver, still no joy.
Even tried installing the nVidia drivers (Method 1), nothing.

Among the errors I'm getting (on 'startkde') :
[I]ksplash : cannot connect to X server
kdeinit : Aborting $DISPLAY is not set
ERROR : couldn't attach to DCOP server[/I]

Thats my story so far...  :(

---

### Post by aysiu on 2006-05-14
[QUOTE=ronniet]
With (false) courage I attempted an upgrade from Hoary to Breezy, had to download about 200mb of stuff so left it overnight. On returning I could see from the prompt that there were a few errors, stuff it couldn't replace. But it was still showing itself as Hoary.[/QUOTE] See... this is the part I'm if-fy about. Do you have Hoary repositories right now or Breezy repositories. When you said you "attempted an upgrade" what were the exact steps and commands you used? Can you post the output of this command? ```
cat /etc/apt/sources.list
```

---

### Post by ronniet on 2006-05-14
[QUOTE=aysiu]See... this is the part I'm if-fy about. Do you have Hoary repositories right now or Breezy repositories. When you said you "attempted an upgrade" what were the exact steps and commands you used? Can you post the output of this command? ```
cat /etc/apt/sources.list
```[/QUOTE]

**I'm 110% positive of my sources being Breezy.**
I can be so sure since I copied and pasted the sources from the wiki into the sources.list file myself. Absolutely 100% sure.

I just seem to have a couple of files that don't seem to want to upgrade or be over written. Without doing another attempted upgrade i've no idea what they were... and even then... the display whizzes past and I can't look back. Is there a log file somewhere that would list what had failed?

I reckon (and i'm a bit of a n00b here so don't take my word as gospel!) that it's maybe something to do with the xserver and/or a display thing. Coz it looks like its trying to go into a resolution, can't (as my monitor is about to say 'no source') and it flicks back to the prompt...  ](*,)  ](*,)  ](*,) 

I know it sounds like i'm chickening out (and i **AM**! :D ) but would it be easier to upgrade from CD? I can download the ISO through BitTorrent...

---

### Post by aysiu on 2006-05-14
Well, just to be extra sure, can you paste these commands into the terminal? That way I know that you not only have Breezy repositories but that none of them conflict with each other: ```
wget -c http://www.psychocats.net/ubuntu/breezy.list
sudo mv /etc/apt/sources.list /etc/apt/sources.list_backup
sudo mv breezy.list /etc/apt/sources.list
sudo apt-get update
sudo apt-get dist-upgrade
```

---

### Post by ronniet on 2006-05-14
[QUOTE=aysiu]Well, just to be extra sure, can you paste these commands into the terminal? That way I know that you not only have Breezy repositories but that none of them conflict with each other: ```
wget -c http://www.psychocats.net/ubuntu/breezy.list
sudo mv /etc/apt/sources.list /etc/apt/sources.list_backup
sudo mv breezy.list /etc/apt/sources.list
sudo apt-get update
sudo apt-get dist-upgrade
```[/QUOTE]

Ok, did all that, still no joy.
Since I couldn't write down all the output, i did take some photos.
(sad, i know, but i'm desperate here... :D )

So, [here I am sitting at my (now familiar) prompt, KDE has tried to display but dumped me back here. Note how it still says Hoary Hedgehog]("http://img.photobucket.com/albums/v375/rtj666/01010005.jpg").

Typed in the first and second lines and am [now getting an update (you can see your breezy.list mentioned at the top of the screen]("http://img.photobucket.com/albums/v375/rtj666/01010006.jpg")...

Do i want to continue and [install a load of stuff i know nothing about?]("http://img.photobucket.com/albums/v375/rtj666/01010007.jpg") Yep...

Agghh! [Errors were encountered.]("http://img.photobucket.com/albums/v375/rtj666/01010008.jpg") Damn! Dammit!...  ](*,) 

Incase its not very readable there, the main error message says:
[I]unpacking replacement gvlc
dpkg : error processing /var/cache/apt/archives/gvlc_0.8.4-svn20050920-3+hol0ubuntu3_i386.deb (--unpack)
trying to overwrite '/usr/share/applications/gvlc.desktop', which is also in package vlc
E: Sub-process /usr/bin/dpkg returned an error code (1)[/I]

And [if i do 'startkde' I just get some messages about $DISPLAY]("http://img.photobucket.com/albums/v375/rtj666/01010009.jpg")...

**I really appreciate you taking the time here to help me.**

I don't want to have to return to 'the dark side' (aka: windows) [-(

---

### Post by aysiu on 2006-05-14
Yeah, I don't know what else to do except maybe ```
sudo apt-get -f install
```

---

### Post by ronniet on 2006-05-15
[QUOTE=aysiu]Yeah, I don't know what else to do except maybe
```
sudo apt-get -f install
```[/QUOTE]

I'll give that a shot when i get home from work.

If that doesn't work, how would I go about installing the Breezy ISO over my current setup? Or would I be as well installing the latest Dapper?

I have two partitions on one drive. One for Windows XP the other is for Ubuntu.

My original intention was to clean up my Gnome/KDE drive now i've ended up with a drive just as messed up. :-?  Luckily I have a small 'swap' drive where I can backup my stuff to before I try any installs.

Oh... one more thing, I have three different Ubuntu's in my dual boot list. How do i delete the two older ones? (think its 2.5, 2.6 and 2.10 if i remember rightly).

---

### Post by aysiu on 2006-05-15
[QUOTE=ronniet]
If that doesn't work, how would I go about installing the Breezy ISO over my current setup?[/quote] Back up your important files, and then select **Manually edit the partition table** instead of erase the entire hard drive. You may want to create a separate /home partition, too, so that future reinstalls will be less involved. For more details, go here: [http://users.bigpond.net.au/hermanzone](http://users.bigpond.net.au/hermanzone) > Or would I be as well installing the latest Dapper? If you don't use Ubuntu for work (only for home general use), I would recommend Dapper.

> 
Oh... one more thing, I have three different Ubuntu's in my dual boot list. How do i delete the two older ones? (think its 2.5, 2.6 and 2.10 if i remember rightly). If you're reinstalling anyway, it's a non-issue, but for the record those are called *linux-image* something or other and can be uninstalled through Adept, Synaptic, or apt-get or aptitude...

---

### Post by ronniet on 2006-05-15
[QUOTE=aysiu]Back up your important files, and then select **Manually edit the partition table** instead of erase the entire hard drive. You may want to create a separate /home partition, too, so that future reinstalls will be less involved. For more details, go here: [http://users.bigpond.net.au/hermanzone](http://users.bigpond.net.au/hermanzone) If you don't use Ubuntu for work (only for home general use), I would recommend Dapper.[/QUOTE]

I'll maybe try *Dapper *then.

Sorry to bug you but, one more question; what about my existing email? How can I back them up? I was using Thunderbird. Well, assuming that the manua edit of the partition table will destroy all my data... ??

I'm from the world of Windows, is it possible to do 'a Microsoft' and install Dapper over my current (read: broken) Hoary? Or would I just get the same error?? :confused: 

**Thanks again for all your help, you've been really patient with n00b me...**  :KS

---

### Post by aysiu on 2006-05-15
> **ronniet]
Sorry to bug you but, one more question said:**
>  Your Thunderbird settings *and* emails live in /home/ronniet/.thunderbird or /home/ronniet/.mozilla-thunderbird (depending on which version of Thunderbird you're using--Ubuntu's or Mozilla's. If you are in Konqueror, press Alt-V, then H, and you'll see all the hidden directories. > Well, assuming that the manua edit of the partition table will destroy all my data... ?? It will destroy your previous Hoary/Breezy installation, yes, but if you do it correctly, it should leave your Windows partition intact.

[quote]
I'm from the world of Windows, is it possible to do 'a Microsoft' and install Dapper over my current (read: broken) Hoary? Or would I just get the same error?? :confused:  Yes, in fact, that's what you *should* do. When you manually edit the partition table, do not format the Windows partition and *do* format the previously Hoary/Breezy partition.

This may help you out:
[http://www.psychocats.net/ubuntu/windowstoubuntu.html](http://www.psychocats.net/ubuntu/windowstoubuntu.html)

---

### Post by ronniet on 2006-05-15
[QUOTE=aysiu]Yes, in fact, that's what you *should* do. When you manually edit the partition table, do not format the Windows partition and *do* format the previously Hoary/Breezy partition.[/QUOTE]

Ah, sorry... by 'doing a Microsoft' I meant installing a new OS over the old OS without formatting or losing any data, the new install repairing anything previously broken. But i suppose its things like that that make Windows so unstable at times... :D 

Ok, now i'm scared. If I screw this partition table up i'll lose ALL my data, Windows, **and** my internet connection! :o  :-?

---

### Post by aysiu on 2006-05-15
[QUOTE=ronniet]Ah, sorry... by 'doing a Microsoft' I meant installing a new OS over the old OS without formatting or losing any data, the new install repairing anything previously broken. But i suppose its things like that that make Windows so unstable at times... :D [/quote] Well, theoretically, you can do a dist-upgrade, but... that apparently didn't work out for you, so it's probably a clean reinstall.

> 
Ok, now i'm scared. If I screw this partition table up i'll lose ALL my data, Windows, **and** my internet connection! :o  :-? Just be very careful. If you're ever in doubt, quit the installer before you commit changes. The new Dapper live/installer CD makes it easy for you to quit before the installation's done. It also makes it easy for you to take screenshots.

If you want to play it safe, go through the installation process for Dapper, select Manually edit the partition table, take a screenshot of the partition table and then take a screenshot of the next screen, too. Post those screenshots here, and I'll try to help you with what options to select.

---

### Post by ronniet on 2006-05-15
[QUOTE=aysiu]...take a screenshot of the partition table and then take a screenshot of the next screen, too. Post those screenshots here, and I'll try to help you with what options to select.[/QUOTE]

:???: 
This is going to sound really bad but... how do i take a screenshot in the installer? I'd need to save the screenshot to either my Windows partition (NTFS) or my swap drive partition (FAT32)...

I'm d/l the Dapper flight7 ISO now, i'll install it when i get home...

---

### Post by aysiu on 2006-05-15
[QUOTE=ronniet]:???: 
This is going to sound really bad but... how do i take a screenshot in the installer? I'd need to save the screenshot to either my Windows partition (NTFS) or my swap drive partition (FAT32)...[/QUOTE] Well, the new Dapper installer is basically run within a live session--so it's an application within the desktop environment. So to take a screenshot in Ubuntu, you just press the PrtScn button. To take a screenshot in Kubuntu, press Alt-F2 and type ```
ksnapshot
```. To take a screenshot in Xubuntu, press Alt-F2 and type ```
gimp
```, then go to File > Acquire > Screenshot.

---

### Post by ronniet on 2006-05-15
Thanks for that, i knew how to do it in Windows just not while installing with Linux :D

Sounds all very complicated this new LiveCD/install thing...  :D
All going well with the download i'll try installing Dapper b7 tonight.

---

### Post by aysiu on 2006-05-15
[QUOTE=ronniet]
Sounds all very complicated this new LiveCD/install thing...  :D[/QUOTE] It *sounds* complicated, but it's not really that bad when you *look* at it. Go ahead--take a look:

[http://www.psychocats.net/ubuntu/windowstoubuntu.html](http://www.psychocats.net/ubuntu/windowstoubuntu.html)

---

### Post by Wr8EYilK8Y on 2006-05-15
I'd like to know about this too. I've had to reinstall twice because Linux stopped booting to a GUI and started booting to a command prompt with no way back.

---

### Post by link141 on 2006-05-15
Sounds like you have a Hoary-able situation (ouch! bad pun!:)) on your hands ronniet.  I just wanted to state how I chose to do a fresh install with Dapper instead of upgrading from Breezy, I've heard nightmares with upgrades of any OS.  First, I backed up all of my data to an external hard drive.  I then Deleted my linux partitions with the G-parted live CD <http://gparted.sourceforge.net/livecd.php>, and installed Dapper over that.  The Dapper installer worked fine with the free space I left it.  Finnally, I loaded all my data back into the fresh install, and reinstalled all of my software.  Though the idea of reinstalling all of your software may sound annoying, it's probably one thing that makes a fresh install more stable than an upgrade.  Despite my apprehensions about it totally messing up grub, it actually wrote over the old boot entries with the Dapper ones fine, no boot problems!  Just wanted to share that info.  By the way, I'm a noob myself :), and I've been annoying this forum with questions for a while :)...  If I were you, at this point I'd just start with a clean install of Dapper.  Kubuntu Dapper is much more stable than Kubuntu breezy.  Thanks for reading.

---

### Post by ronniet on 2006-05-15
**Thanks for the support guys, its much appreciated.**

I had a look at your psychocats link, thanks mate, it does look easy enough and i'm a seasoned pro at installing Windows i'm just dubious of screwing up the Windows partition. If that went then i'd lose ***AAAA****AALL* my stuff completely. But i'll be careful with my mouse pointer.

And i totally agree with you **link141**, i've upgraded a Windows OS many a time and the upgrade has just bloated the computer to overkill. Ends up the damn thing is so unstable its near unuseable! Infact, if my memory serves me right, Microsoft themselves state that every year or so you should back up your files, format and reinstall Windows! And thats the makers! Outrageous.

Needless to say; when i get Dapper f7 installed i'll be _VERY_ dubious about upgrading it to the final thing in a few weeks... think i'll wait a while before my next upgrade venture!   :D

I think it was probably my uninstalling of some Gnome progs that pushed it over the edge to destruction... ah well... you live and learn...  :)

---

### Post by ronniet on 2006-05-16
**First, i want to thank you, aysiu, for all your help.**

I'm writing this post using Konqueror and in Dapper Flight7! :D 
***Yaaayyyyy!!** * :cool: 

I didn't get a nice graphical installer like in the screenshots but i plodded through the installer. Only problem I came across was that a couple of times the partitioner wouldn't continue. I'd set it all up, click to finish and apply changes and it wouldn't do anything. Anyway... a quick abort and restart did fine. Boot menu is also rewritten so gone are the three Linux entries.

My only quibble seems to be my browsing speed. It's really quite slow. And that's on a fresh install, untouched by my grubby hands
(**grub! Hah!** I made a funny! ;)  )

I had the slow browsing before in Ubuntu, fixed it, then it happened again so i'm really not sure whats causing it but... at least i've got my linux back. Just need to reinstall Firefox, GIMP, few other progs and copy my backups back and i'm in business...

Happy days!
:mrgreen:

---

