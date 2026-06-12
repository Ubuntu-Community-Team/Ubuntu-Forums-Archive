---
title: "Xubuntu - Making it work - journey to the lighter side of *buntu"
date: 2008-07-09
forum: Desktop Environments
---

### Post by jimmy the saint on 2008-07-09
I just switched to Xubuntu and for the most part I find it to be pretty good.  I like the Ubuntu/Debian back-end.  As a newer *nix user, it is nice to have good package management and reasonably comprehensive features that make the learning curve just a little less steep.  Unfortunately, Xubuntu seems to receive a little less attention that Ubuntu in the development process and in the support forums.  Some applications that work in Ubuntu don't seem to work in Xubuntu, and getting help in the forums can be tough because so few people seem to use Xubunu.
    Since I am not a *nix guru and I know there are a lot of people out there like me who would like a lighter desktop but don't have the skills to hack their way to perfection, I figured I would start a thread where I post the things I did to make Xubuntu work for me.  If anyone else finds solutions to common issues please share your experiences as well.  
    This is not to be a comprehensive support thread.  Please try to restrict posts to issues you have solved or questions regarding the solutions posted.  

Thanks!

JTS

---

### Post by jimmy the saint on 2008-07-09
For some reason Tomboy doesn't seem to work in Xubuntu.  I have searched for a solution but I can't find any.  If you run the program from the terminal the icon works, but I still can't seem to get the general management app to work.  This makes it difficult to see all of my notes, since only the most recent ones are displayed via the icon.

My search for a good alternative led me to land on zim.  It seems to be light, effective, and has a panel icon that makes note management almost as easy as tomboy in gnome.  Another alternative is NoteCase, which you can install from via synaptic, but it is crippleware.  The free options work well, but most of the better ones, including bullets which I use frequently, require paying 35 euros.  Given the current strength of the American dollar I think that is approximately $5000 dollars, or will be soon.  

I settled on zim.  It is a desktop Wiki that has similar formating options as tomboy, a few good plugins and the ability to organize your notes into notebooks, plus it is much lighter on resources.  There is a script that allows you to import your notes from tomboy, but I haven't tried it yet and I have read there may be issues.  When I try it, I will post how well it worked.  The one drawback seems to be lack of printing support, but you can export to html with a "printing" template, so it is simply an extra step.  There is a newer version at the zim website than in the Ubuntu repos, but the new features don't seem to vital so I didn't bother.

If anyone has found a better one than zim, let us know.  

JTS

---

### Post by jimmy the saint on 2008-07-09
This is a simple solution that has been posted elsewhere, but I figure it goes well here too.

install libpam-gnome-keyring via synaptic and then check the new check box that appears in the prompt.  I have an 64-bit system and this worked for me.  I read that on 32-bit systems the dialog just goes away.  I can't confirm this though, so don't take my word for it!

---

### Post by jimmy the saint on 2008-07-13
For a while, every time I logged in, Synaptic would be started, but would pop up an error about not having administration privileges.  What an irritation!!  It was an easy, but quirky fix so I though it was just me.  I found a few other people with the same issue though, so I will post the fix here.

Application>Settings>Settings Manager, click the Sessions and Startup button.  Once the dialog opens Uncheck the "Automatically save session on logout" box and check the "Prompt on logout" box.  For some reason, the saving sessions box isn't enough.  The next time you log out, make sure that the "Save session for future logins" box is NOT checked.  This worked for me.

JTS

---

### Post by jimmy the saint on 2008-07-13
When I used the LiveCD I couldn't use gparted to format the drive manually because it wouldn't unmount the partitions.  It kept auto mounting them and opening several windows for each one.  I ended up having to use the Ubuntu cd instead for the partitioning, then switch to Xubuntu for the install.  Post install the same behavior persisted and I couldn't unmount certain external drives.  Then I found the problem!!  Thunar is set to manage volumes and yet gnome-mount is installed.  I think that gnome-mount does the same job, which means that each time a drive was connected, it would have a mount operation done on it twice, same with unmounting.

Fix:
Applications>settings>settings manager, click on the File Manager button.  Go to the advanced tab and uncheck "enable volume management"
Everything still gets mounted and unmounted just fine.  In fact, it eliminates the errors.

---

### Post by j1mc on 2008-07-19
> **jimmy the saint said:**
> This is a simple solution that has been posted elsewhere, but I figure it goes well here too.

install libpam-gnome-keyring via synaptic and then check the new check box that appears in the prompt.  I have an 64-bit system and this worked for me.  I read that on 32-bit systems the dialog just goes away.  I can't confirm this though, so don't take my word for it!

I had to check the box on my 32-bit system, but it does work.  Thanks, Jimmy.

---

### Post by jimmy the saint on 2008-07-20
so there are quite a few threads popping up regarding various power managment features including, suspend password, screensaver, and various screen related issues.  the problem seems to be that gnome-power-manager relies on gnome-screensaver in order to have any impact on the system and by default, it doesn't seem to be activated. The solution is to create a new autostart entry for gnome-screensaver.  Once this is done, set the settings as you wish and they will actually start to affect the system.  Exciting huh!!

HOW:  Applications>settings manager> click on Autostarted apps button.
click add.  give it a name, a description and for command type 
"gnome-screensaver".  click ok and then CTRL-ALT-BACKSPACE.  log back in and your power settings will actually work, including suspend password, screensaver and whatever screen settings you have selected.

---

### Post by Dai84b on 2008-07-20
I'm preparing a hard drive on our best computer with the windows HDD's disconnected. It's for a PC that used to run Win98SE and the idea is to try Xubuntu with all the old computer bits going in to make a no cost second computer. During install the Xubuntu partition editor won't give me a satisfactory manual patitioning of the clean HDD such that I reduce the root drive to 25% of storage space and create a second ext3 partition for /home. So I have to go with a guided single partiton of the whole drive.  

I feel like throwing in the towel with trying to partition xubuntu [per the tutorials] in GPartED. I've found the setting mentioned above to prevent automatic remounting of the disk drives. Good. In Xubuntu Live CD that meant the mount command was already greyed out. The resizing operation reached its furthest point and stopped saying 'Please run e2fsk -f /dev/sda1' . What does that mean please? 

Wouldn't it be good if the installer had a partitioning scheme for / and /home as default ? All the leading lights say this is a good idea after all. 

Cheers
David

---

### Post by jimmy the saint on 2008-07-20
Dai84b

When I was installing Xubuntu I had similar issues.  Did you disable the Volume management in Thunar?  If you follow the advice above first, then exit the installer, run partition manager from the applications menu.  Make sure to unmount all the partitions, then erase them all.  Create partitions as you see fit.  What I did was create a 300 MB partition for boot, one for / and one for /home and one for swap.  When this is done, you can install with the manual method and simply assign the partitions as what you want.  Just make sure to format all but swap as ext3.  If it continues to give you problems, I ended up using the Ubuntu live cd for the partitioning and installing from the Xubuntu cd.

---

### Post by j1mc on 2008-07-20
Per bug #243848, the gnome-power-manager settings do not display in xubuntu, even though the application is installed by default.  

To get gnome-power-manager to display in the menu, you must edit the /usr/share/applications/gnome-power-preferences.desktop file to indicate that the application should display in Xfce.  Specifically, change, "OnlyShowIn=GNOME;" to "OnlyShowIn=GNOME;XFCE;" and then regenerate the menu with the command, "sudo update-desktop-database."  

Once you do that, menu will show the power management application under Applications > Settings > Power Management.

See the following bug for more info:  [https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/243848](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/243848)

---

### Post by Dai84b on 2008-08-03
Thanks Jimmy. I found the setting that stops automatic mounting of a HDD. Live CD and GParted worked well then. I was working through getting /home onto the new partition [http://www.psychocats.net/ubuntu/separatehome]("http://www.psychocats.net/ubuntu/separatehome")
I didn't succeed. The disappointment was that the 1999 Win98 PC that I acquired through Freecycle did not accept the large hard drive. I think I will have to try my copy of Seagate's Disc Wizard to see if the computer will be fooled by that. It worked a few year's ago for the same HDD in another similar vintage computer in my life before Ubuntu. 
In the meantime I completed an Alternate CD install of Xubuntu onto the old 128MB RAM computer and am quite pleased with the results. It doesn't like too many things running at once but a free PC, freecycle Monitor, loads of parts from my scrap box and Xubuntu means this is no complaint. 
David

---

### Post by wandalalakers on 2008-11-28
> **jimmy the saint said:**
> so there are quite a few threads popping up regarding various power managment features including, suspend password, screensaver, and various screen related issues.  the problem seems to be that gnome-power-manager relies on gnome-screensaver in order to have any impact on the system and by default, it doesn't seem to be activated. The solution is to create a new autostart entry for gnome-screensaver.  Once this is done, set the settings as you wish and they will actually start to affect the system.  Exciting huh!!

HOW:  Applications>settings manager> click on Autostarted apps button.
click add.  give it a name, a description and for command type 
"gnome-screensaver".  click ok and then CTRL-ALT-BACKSPACE.  log back in and your power settings will actually work, including suspend password, screensaver and whatever screen settings you have selected.

You fixed my Xubuntu screensaver problem for a laptop that I'm installing for my cousin.
Can you please increase jimmy the saint's thank you counter?  Thx!

---

### Post by jegel on 2009-02-06
thanks for the help. i tried to fix the mount/unmount problem but now i have another problem: i disable thunar volume management but now no cd is getting mounted! i tried re-enabling it but things dont change. hard drive get mounted/unmounted even if i still get the error message (as someone already said somewhere else it's probably because thunar tries to eject the drive instead of unmonting it). anyway, now i'm stuck with a computer unable to read from a cd drive! :(
any help?

---

### Post by jegel on 2009-02-06
sorry, i just had to restart...
the error is still there though.
thank you so much!

---

### Post by adamlau on 2009-02-06
If Xubuntu worked like Ubuntu, I would not use it. The move away from GNOME is what sets Xubuntu apart from its big brother and why I continue to use recommend and recommend it.

---

### Post by dox_drum on 2009-02-06
> **adamlau said:**
> If Xubuntu worked like Ubuntu, I would not use it. The move away from GNOME is what sets Xubuntu apart from its big brother and why I continue to use recommend and recommend it.

Which are the real advantages of Xubuntu? Besides space. Sorry for the question, but I'm rather new on this.

Thanks.

---

### Post by jimmy the saint on 2009-02-06
Xubuntu is less resource intensive.  It is a simpler, less "everything you could ever want and a bag of chips" than Ubuntu (Gnome).  It runs a little better on older hardware and I found it ran a lot faster (and got better battery life) on my laptop.

---

### Post by dox_drum on 2009-02-08
> **jimmy the saint said:**
> Xubuntu is less resource intensive.  It is a simpler, less "everything you could ever want and a bag of chips" than Ubuntu (Gnome).  It runs a little better on older hardware and I found it ran a lot faster (and got better battery life) on my laptop.

Thank you!

Perhaps I'll try it in my old laptop.

---

### Post by Clancy_s on 2010-01-07
> **jimmy the saint said:**
> so there are quite a few threads popping up regarding various power managment features including, suspend password, screensaver, and various screen related issues.  the problem seems to be that gnome-power-manager relies on gnome-screensaver in order to have any impact on the system and by default, it doesn't seem to be activated. The solution is to create a new autostart entry for gnome-screensaver.  Once this is done, set the settings as you wish and they will actually start to affect the system.  Exciting huh!!

HOW:  Applications>settings manager> click on Autostarted apps button.
click add.  give it a name, a description and for command type 
"gnome-screensaver".  click ok and then CTRL-ALT-BACKSPACE.  log back in and your power settings will actually work, including suspend password, screensaver and whatever screen settings you have selected.

Thanks - that fixed suspend for me running Xubuntu 8.4.1 LTS on an IBM T22.  If I suspend by closing the laptop lid it wakes up again with a password needed, if I suspend manually from the shutdown button I need to hold down the power button for a second or so to wake but it doesn't want a password, which is mildly odd but functional for me. 

In case anyone else goolges by: an old fix, suggested for 8.4 which involved switching to apm didn't work, it made things worse since at least log-out, stop and restart worked OOTB with 8.4.1, switching to apm stopped all shutdown options working except for hold the power button down for > 2 seconds...

---

