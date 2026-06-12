---
title: "Migrate data/packages to new machine"
date: 2013-11-15
forum: Desktop Environments
---

### Post by pmasson on 2013-11-15
I have been using Ubuntu 10.04 LTS and 12.04 LTS over the past four years on the same machine. I now have a new machine (due to a new employer). I would like to migrate / transfer my data (files, settings, config, etc.) and packages to the new machine. Ubuntu 12.04 LTS is installed (and updated) on both the current and the new machine, however my profile (user account) is not the same.

Can someone please point me to a current resource/tutorial to transfer/migrate my content?

Thanks,
Patrick

(I have searched for "migration guide, migration, migration howto, transfer, data transfer" as both keywords and tags across all forums).

---

### Post by TheFu on 2013-11-15
I've written about this as a backup-restore method in these forums. Going between machines isn't too much difference, just the udev stuff will need to manually handled ... provided there isn't any odd hardware involved.  Look for dpkg --get-selections and dpkg --set-selections as the main trick, plus having backups of /etc, /home and certain areas of /var ... depending on the stuff you've loaded.  /usr/local might be handy too, if you've gone off-the-reservation.

You didn't mention whether both systems are 32 or 64-bit. It matters for some parts of this.

I'll search, but the forum search facility has never worked too well for me. Sorry.  I'll look some.

---  Updates as I find stuff.
* [http://askubuntu.com/questions/101931/restoring-all-data-and-dependencies-from-dpkg-set-selections](http://askubuntu.com/questions/101931/restoring-all-data-and-dependencies-from-dpkg-set-selections)
* [http://askubuntu.com/questions/9135/best-way-to-backup-all-settings-list-of-installed-packages-tweaks-etc](http://askubuntu.com/questions/9135/best-way-to-backup-all-settings-list-of-installed-packages-tweaks-etc)
Found it!
* [http://ubuntuforums.org/showthread.php?t=2057932&highlight=thefu+dpkg+restore](http://ubuntuforums.org/showthread.php?t=2057932&highlight=thefu+dpkg+restore)
Hope these help.

--- more updates.
Completely forgot to mention about the userid change part.  This can be almost trivial or very hard to handle. It all depends on how the files in the HOME are setup. Are they relative off the HOME or do they spell out the /home/old-user-id/ path?  If relative from HOME, life is easy.  Just use recursively change the ownership of all files in your HOME on the new system to be the new userid and group.  That should take just a few seconds with **sudo chown -R newuser:newgroup ~/**, right?

Do you think we've covered everything? Anything major missed?

---

### Post by pmasson on 2013-11-15
Thanks "TheFu,"

I am going from a 32-bit to 64-bit environment.

I'm also looking over the links you've point to - thanks again.

I also found this: [http://eggsonbread.com/2010/01/28/move-ubuntu-to-another-computer-in-3-simple-steps/](http://eggsonbread.com/2010/01/28/move-ubuntu-to-another-computer-in-3-simple-steps/) --Any thoughts?

---

### Post by TheFu on 2013-11-15
> **pmasson said:**
> Thanks "TheFu,"

I am going from a 32-bit to 64-bit environment.

I'm also looking over the links you've point to - thanks again.

I also found this: [http://eggsonbread.com/2010/01/28/move-ubuntu-to-another-computer-in-3-simple-steps/](http://eggsonbread.com/2010/01/28/move-ubuntu-to-another-computer-in-3-simple-steps/) --Any thoughts?

There are lots of complaints in the comments about the amount of time involved too - seems foolish to update everything when most of the already installed packages will be current. I don't like waste. 

The comment from **kele** is good, however.

Reading the comments more ... it is unclear whether anyone really knew where extra settings, data or programs can be installed.  /opt is seldom used, IME. One of 30 servers I manage has something in /opt/ ... and I put it there. Most of the time, stuff ends up in /var and /usr/local/.  Some packages put stuff in /usr/share/ too.  What that means is that only the admin for the box knows all the places where important settings and data are stored.

Then there are machines with manually installed packages. These introduce a wrinkle that can't be predicted. If you've ever installed a .deb file or a .tgz/tar.gz or similar program ... all bets are off. The best answer for those is to reinstall on the new box manually.

So, YOU need to know where things are located. Definitely get /etc and where ever the HOME dirs are stored, but you might need many more places.  Grabbing everything on the system might be nice, but when switching between machines, especially 32-64-bit ... dangerous.

---

### Post by pmasson on 2013-11-15
Thanks again "TheFu,"

From only using the first two steps from the link included above ([http://eggsonbread.com/2010/01/28/move-ubuntu-to-another-computer-in-3-simple-steps/](http://eggsonbread.com/2010/01/28/move-ubuntu-to-another-computer-in-3-simple-steps/)), I was able to migrate all of my content--files, config files, firefox bookmarks, thunderbird accounts--everything(!), as well as all of my applications (packages) along with their appropriate/current configurations/preferences. The only thing that did not make it over (that I have discovered so far) was my CIsco VPNC configuration for VPN in the network manager. However this article proved successful: [http://www.ed.ac.uk/schools-departments/information-services/computing/desktop-personal/vpn/vpn-cisco-client/vpn-cisco-ubuntu](http://www.ed.ac.uk/schools-departments/information-services/computing/desktop-personal/vpn/vpn-cisco-client/vpn-cisco-ubuntu)

Here are my steps:
[h=2][SIZE=3]Prerequisites:[/SIZE][/h] Source machine:
Dell Latitude 13 running Ubuntu 12.04 LTS / 32-bit
External drive

Target machine
HP EliteBook 9470m running Ubuntu 12.04 LTS
Fresh Installation via USB Stick per these instructions: [https://help.ubuntu.com/community/Installation/FromUSBStickQuick](https://help.ubuntu.com/community/Installation/FromUSBStickQuick)
(NOT via wubi.exe as described here: [http://www.ubuntu.com/download/desktop/install-ubuntu-with-windows](http://www.ubuntu.com/download/desktop/install-ubuntu-with-windows))
Created user account on target machine to mirror source machine account (same user/account name, login/password, etc.)


 [h=2][SIZE=3]Step 1: Store the list of installed packages[/SIZE][/h] As suggested, I ran the following command on the source machine to store the installed packages names in a file: ~/pkglist:
sudo dpkg --get-selections | sed "s/.*deinstall//" | sed "s/install$//g" > ~/pkglist

 [h=2][SIZE=3]Step 2: Transfer your config[/SIZE][/h] On source machine navigated via Nautilus to /home/'myaccount' selected all and manually copied (drag and dropped) 'myaccount' directory to external drive to transfer my home directory, 
On source machine navigated via Nautilus to /etc/apt/ and manually copied (drag and dropped) the source list (/etc/apt/sources.list) to the same external drive (not in the same home directory copied earlier).
Removed external drive from source machine and connected it to the target machine.
On target machine, navigated via Nautilus to /home/'myaccount' and on external drive navigated to /'myaccount'
On target machine copied (drag and dropped) all content from the /'myaccount' directory into the /home/'myaccount' of the target machine.
When promoted regarding duplicate directories, selected "Merge"
When prompted regarding existing files, selected "Replace"
On target machine, navigated via Nautilus to /etc/apt and on external drive navigated to / to find sources.list
On target machine copied (drag and dropped) /sources.list to /etc/apt
**Due to permissions conflict error, opened terminal and entered, sudo cp /media/'driveName'/sources.list /etc/apt/

Restarted my machine and everything auto-magically worked!

Did not need step 3...

 [h=2][COLOR=#808080][SIZE=2]Step 3: Install packages[/SIZE]
[/COLOR][/h][COLOR=#808080]On the target machine run the following command in a failsafe terminal session to install your packages:
[/COLOR][COLOR=#808080]sudo aptitude update && cat pkglist | xargs sudo aptitude install -y[/COLOR]

---

### Post by TheFu on 2013-11-16
If you didn't do something like step 3, then there was NO point to step 1. BTW, I think step 3 should be performed differently ... as in the comment that is mentioned above.

But ... if you are happy, that's all that matters.  Perhaps the company setup the new box with software that you used already?  I suspect you will discover a few packages that were not already installed ... keep that list-of-packages ... you will likely want them later.

---

### Post by TheFu on 2013-11-16
If you didn't do something like step 3, then there was NO point to step 1. BTW, I think step 3 should be performed differently ... as in the comment that is mentioned above.

But ... if you are happy, that's all that matters.  Perhaps the company setup the new box with software that you used already?  I suspect you will discover a few packages that were not already installed ... keep that list-of-packages ... you will likely want them later.

---

### Post by pmasson on 2013-11-16
TheFu, you're absolutely correct... I did not need to do step one, but as--sequentially--the directions had me do it, I did want to be specific in my update. Also to your point, I have discovered missing packages for example, GIMP, Tomboy, Skype, etc. However as my configs are in my Home dir, once I install those and run them, each app is populated with my settings.

Thanks again for your help, it is very comforting to have someone looking over my shoulder.

---

