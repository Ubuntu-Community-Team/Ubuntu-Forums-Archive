---
title: "Simple solution for Add/Remove, update manager, synaptic package manager VANISHING"
date: 2009-10-08
forum: Desktop Environments
---

### Post by L plates on 2009-10-08
Hi, :mrgreen:, I am very green, be nice please.

I take no credit for this at all, this was a solve in archives from aysiu in 2007.

I am very green, been with Ubuntu for 3 days, attempted install of KTorrent, at the end of install i am asked to put in Ubuntu disk, i do so, desktop crashes and when i restart my add/remove, update manager and synaptic vanish just after they attempt to load.

I searched through as many forums as possible and found this solve posted from 
aysiu in 2007. I still had to trouble shoot a little, so this is why i posted this thread.

I don't want to waste the time of veterans, i want to help newbies like myself is all, i saw that there were 'patches' for this issue/bug, but i did not know how to use 'patches', i will learn though now after this event.

Also, have your Distro disc at the ready, as you will be asked to use it.

FYI: you will get to a point when you put the in disc and press enter and it appears as though nothing is happening, this message came up like three or four times:
"Media change: please insert the disc labelled
 'Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090421.3)'
in the drive '/cdrom/' and press enter"

Just press enter once each time that you see the above message, eventually this happens:
"(Reading database ... 151093 files and directories currently installed.)
Unpacking libgeoip1 (from .../libgeoip1_1.4.4.dfsg-3_i386.deb) ...
Setting up libgeoip1 (1.4.4.dfsg-3) ...

Setting up ktorrent (3.2.1+dfsg.1-0ubuntu3) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Processing triggers for menu ..."

Below is the original solve, follow each step and combine it with my above notes>>

NOTE to newbies: to copy from here and paste into terminal, you copy as normal, but when you paste into the terminal, you have to hold ctrl+shift+v, as opposed to just ctrl+v. Alternatively, just right click and paste, or edit-paste.

Here tis. as posted by aysiu.
 

  aysiu
May 29th, 2007, 09:40 PM

Hm. Found out you're not alone:
[https://answers.launchpad.net/ubuntu/+question/6872](https://answers.launchpad.net/ubuntu/+question/6872)

Can you try pasting these commands into the terminal { and then pasting the output back here?} - L plates says "don't bother pasting this info, this is an archive, just inpu these commands,o ne by one, paste though, do not retype, copy and paste!!"

sudo rm -f /var/cache/apt/*.bin
sudo apt-get update
sudo apt-get dist-upgrade
gksudo gnome-app-install 

You will be asked
"After this operation, 1356kB of additional disk space will be used.
Do you want to continue [Y/n]?" say yes of course with a Y and enter.


Each line is a separate command that should have the Enter key pressed afterwards.

Warning: paste the commands in. Do not retype the commands, especially that first one. If you mess up typing that first command, you can accidentally delete your entire installation. Paste. Do not retype.

Hope this helps Newbies, sorry if i have wasted the time of gurus, that was not my intention.

Further; here is the link to the original solve [http://ubuntuforums.org/archive/index.php/t-458548.html](http://ubuntuforums.org/archive/index.php/t-458548.html)



And here is my terminal screen dump if you need to see my steps.

Me@Me-laptop:~$ sudo apt-get update
[sudo] password for Me: 
Ign cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090421.3) jaunty/main Translation-en_AU
Ign cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090421.3) jaunty/restricted Translation-en_AU
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) jaunty Release.gpg                            
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) jaunty/main Translation-en_AU                 
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) jaunty/restricted Translation-en_AU           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release.gpg                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Translation-en_AU          
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty Release.gpg                            
Ign [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Translation-en_AU              
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) jaunty/universe Translation-en_AU   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Translation-en_AU    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Translation-en_AU      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Translation-en_AU    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release                         
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) jaunty/multiverse Translation-en_AU 
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty Release                                
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) jaunty-updates Release.gpg                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Packages                   
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) jaunty-updates/main Translation-en_AU         
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Packages                       
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) jaunty-updates/restricted Translation-en_AU   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Sources                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Sources              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Packages               
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) jaunty-updates/universe Translation-en_AU     
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) jaunty-updates/multiverse Translation-en_AU   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Sources                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Sources              
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) jaunty Release                                
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) jaunty-updates Release                        
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) jaunty/main Packages                          
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) jaunty/restricted Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) jaunty/main Sources       
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) jaunty/restricted Sources 
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) jaunty/universe Packages  
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) jaunty/universe Sources   
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) jaunty/multiverse Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) jaunty/multiverse Sources 
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) jaunty-updates/main Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) jaunty-updates/restricted Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) jaunty-updates/main Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) jaunty-updates/restricted Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) jaunty-updates/universe Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) jaunty-updates/universe Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) jaunty-updates/multiverse Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) jaunty-updates/multiverse Sources
Reading package lists... Done                              
Me@Me-laptop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libgeoip1
Suggested packages:
  geoip-bin
The following NEW packages will be installed:
  libgeoip1
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/640kB of archives.
After this operation, 1356kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Media change: please insert the disc labelled
 'Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090421.3)'
in the drive '/cdrom/' and press enter

Media change: please insert the disc labelled
 'Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090421.3)'
in the drive '/cdrom/' and press enter

Media change: please insert the disc labelled
 'Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090421.3)'
in the drive '/cdrom/' and press enter

Media change: please insert the disc labelled
 'Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090421.3)'
in the drive '/cdrom/' and press enter

Media change: please insert the disc labelled
 'Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090421.3)'
in the drive '/cdrom/' and press enter

Err cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090421.3) jaunty/main libgeoip1 1.4.4.dfsg-3
  Unable to unmount the CD-ROM in /cdrom/, it may still be in use.
Get:1 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) jaunty/main libgeoip1 1.4.4.dfsg-3 [640kB]
Fetched 640kB in 17min 38s (605B/s)                                            
(Reading database ... 151093 files and directories currently installed.)
Unpacking libgeoip1 (from .../libgeoip1_1.4.4.dfsg-3_i386.deb) ...
Setting up libgeoip1 (1.4.4.dfsg-3) ...

Setting up ktorrent (3.2.1+dfsg.1-0ubuntu3) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Processing triggers for menu ...
Me@Me-laptop:~$

---

### Post by wojox on 2009-10-08
Open a terminal and paste back the results of:

```
cat /etc/apt/sources.list
```

---

### Post by drs305 on 2009-10-08
I can't really tell if you fixed your problem or not. The issue appears to be the system is trying to access the installation CD. You can remove that from the repository by opening Synaptic or Software Sources. Then Settings, Repositories. 

At the bottom of the Ubuntu Software tab it lists your install CD. De-select that one and hit Reload to refresh the repository list.

If still selected, the system asks for the original install CD, even if you have updated to a newer release. So if you installed Hardy, but upgraded to Jaunty, it would still want you to insert your Hardy CD any time you access your sources.list. (Another reason to untick the CD as a source).

---

### Post by regala on 2009-10-08
> **drs305 said:**
> I can't really tell if you fixed your problem or not. The issue appears to be the system is trying to access the installation CD. You can remove that from the repository by opening Synaptic or Software Sources. Then Settings, Repositories. 

At the bottom of the Ubuntu Software tab it lists your install CD. De-select that one and hit Reload to refresh the repository list.

If still selected, the system asks for the original install CD, even if you have updated to a newer release. So if you installed Hardy, but upgraded to Jaunty, it would still want you to insert your Hardy CD any time you access your sources.list. (Another reason to untick the CD as a source).


IOW, this was surrealistic, nonsensical, but quite made my day.

---

### Post by L plates on 2009-10-09
Thank you for your replies this far. 

to respond to [wojox]("http://ubuntuforums.org/member.php?u=802919"), I am currently at work, unable to do anything til i get back tonight, i will post the results to 
cat /etc/apt/sources.list

tonight.

to answer [drs305]("http://ubuntuforums.org/member.php?u=223945") question, I can now access my add/remove, synaptics and 
update manager, however, i am still asked for a disc whenever i install
new open source software. So in a way it did work, but issue is not fully
fixed, i am going to go into the settings and do as you said.

Thank you to both of you for your effort, you can probably tell from my 
original post that i am not even at baby steps yet, but i have had a 
couple of issues now with Ubuntu, and each time i have been able to find 
a solution in the forum, bit different to the useless gammit of useless
non translatable talk that I have had with Windows.

to [regala]("http://ubuntuforums.org/member.php?u=604020"), I don't quite understand how your posting helped, Did it?

I will post my sources.list tonight, and change the settings in the 
repository, thank you for explaining things in steps.

On the road to a better understanding, I am already addicted. As dumb as 
I feel, it is still much better than my 15 year windows fling

L plates:guitar:

---

### Post by L plates on 2009-10-09
Here are the results from: cat /etc/apt/sources.list

peaceful@peaceful-laptop:~$ cat /etc/apt/sources.list
#deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090421.3)]/ jaunty main restricted
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) jaunty main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) jaunty universe
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) jaunty universe
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) jaunty-updates universe
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu

L plates

---

### Post by drs305 on 2009-10-09
> **L plates said:**
> Here are the results from: cat /etc/apt/sources.list

peaceful@peaceful-laptop:~$ cat /etc/apt/sources.list
#deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

[COLOR="Red"]deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090421.3)]/ jaunty main restricted[/COLOR]


This is the CD that you want to disable via the method I described in an earlier post.

You can also manually edit sources.list and place a comment symbol at the start of that line:
```

gksu gedit /etc/apt/sources.list

```

> 
[COLOR="Red"]# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090421.3)]/ jaunty main restricted[/COLOR]


Save the file, then Reload Synaptic or
```

sudo apt-get update && sudo apt-get upgrade

```

---

### Post by L plates on 2009-10-10
Hi, I did as you said,
I changed the settings in synaptics, saved the new file in terminal like you said and entered the lines in terminal as suggested, this was the outcome.

peaceful@peaceful-laptop:~$ gksu gedit /etc/apt/sources.list
peaceful@peaceful-laptop:~$ sudo apt-get update && sudo apt-get upgrade
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) jaunty Release.gpg
Get:1 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) jaunty/main Translation-en_AU [2734B]       
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) jaunty/restricted Translation-en_AU           
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) jaunty/universe Translation-en_AU             
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) jaunty/multiverse Translation-en_AU           
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty Release.gpg                            
Ign [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Translation-en_AU              
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) jaunty-updates Release.gpg          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release.gpg                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Translation-en_AU          
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) jaunty-updates/main Translation-en_AU
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) jaunty-updates/restricted Translation-en_AU   
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty Release                                
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) jaunty-updates/universe Translation-en_AU     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Translation-en_AU    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Translation-en_AU
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Translation-en_AU
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release               
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) jaunty-updates/multiverse Translation-en_AU
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) jaunty Release                                
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) jaunty-updates Release                        
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Packages                       
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) jaunty/main Packages                          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Packages                   
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) jaunty/restricted Packages                    
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) jaunty/main Sources                           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Sources                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) jaunty/restricted Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) jaunty/universe Packages                      
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) jaunty/universe Sources                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Sources                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Sources              
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) jaunty/multiverse Packages                    
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) jaunty/multiverse Sources 
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) jaunty-updates/main Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) jaunty-updates/restricted Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) jaunty-updates/main Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) jaunty-updates/restricted Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) jaunty-updates/universe Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) jaunty-updates/universe Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) jaunty-updates/multiverse Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) jaunty-updates/multiverse Sources
Fetched 2734B in 4s (676B/s)                               
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
peaceful@peaceful-laptop:~$ 

I installed a new app and i was not asked for the distro disc, i hope that this means that it is fixed

---

### Post by drs305 on 2009-10-10
> **L plates said:**
> 
I installed a new app and i was not asked for the distro disc, i hope that this means that it is fixed

It looks like it.  :-)  Assuming you'd already updated and just reran it to get the commands again, since there was nothing to update.

If you don't have any more issues, would you please mark the thread SOLVED via the Thread Tools link at the top right of the first post. You can also remove the SOLVED tag from the same link if necessary...

---

