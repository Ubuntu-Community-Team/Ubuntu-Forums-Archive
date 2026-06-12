---
title: "Module could not be loaded"
date: 2006-02-16
forum: Desktop Environments
---

### Post by Atholm on 2006-02-16
Aloha..
I have a problem with my Kubuntu.
When i'm trying to change the settings like Disc and filesystem it tells me:

The module Disc and filesystem could not be loaded.
The diagnostics is:
Possible reasons

-  An error occurred during your last KDE upgrade leaving an orphaned control module
- You have old third party modules lying around.

What can i do?

plz help thanks

Anders Holm

---

### Post by uhlive on 2007-05-07
I"m having the same problem

---

### Post by hellblade on 2007-05-07
> **Atholm said:**
> Aloha..
I have a problem with my Kubuntu.
When i'm trying to change the settings like Disc and filesystem it tells me:


What do you mean Disc and filesystem? Where/what are these settings?? Never heard of them.

---

### Post by uhlive on 2007-05-07
its in kde.. its like a control panel

---

### Post by hellblade on 2007-05-07
Check if you have kde-guidance installed. Also installing kubuntu-desktop might help.

---

### Post by uhlive on 2007-05-07
they are installed.. every thing else works.. but when you try to load the disk and file systems module you get an error as stated in his first post

---

### Post by hellblade on 2007-05-08
First try this:
```
sudo aptitude reinstall kde-guidance
```
If it doesn't work try:
```
sudo dpkg-reconfigure kde-guidance
```

If it doesn't work either, create a new user and try it there. That would exclude a broken user configuration.

---

### Post by yurtos on 2007-05-13
i got a same issue in my Kubuntu Feisty after full upgrade. all updates in place at this moment.
under System Settings-> Disk & Filesystems 
i get error:
The module Disk & Filesystems could not be loaded

Possible reasons:
-An error occured during your last kde upgrade leaving an orphaned control module
-You have old third party modules lying around


i have reinstalled, reconfigured kde-guidance and reinstalled pykdeextentions but i still do have the error. 
creating separate user didn't help ether.
i really dont feel like reinstalling everything.
any ideas?

---

### Post by hellblade on 2007-05-13
If you want, file a bug report at launchpad. It could be an upgrader bug.

---

### Post by yurtos on 2007-05-16
still can't get it to work...
looks like i will have to reinstall the system to get it fixed :(

thank you hellblade for trying to help

in any case ubuntu is great ;) i still do love it :)
cheers

---

### Post by geek2330 on 2007-05-17
I am having the same error as well, mine is a new install of 7.04 with KDE, I have installed a couple apps.....

Any solution to this?

.

---

### Post by geek2330 on 2007-05-18
Any help with this!!!!!!!!!!

I reinstalled Kubuntu 7.04 (formatted partition and reinstalled), everything working ok until I plugged in the SATA drive to the mainboard and changed grub to include the XP option in the list.

Nothing else....

I disconnected the SATA, changed grub back to defaults, rebooted but STILL SAME ISSUE ...!!:mad:

Can't believe nobody has resolved this issue before and know the reason of this error....

---

### Post by gsiliceo on 2007-05-30
Same problem here, but i can access my hard disk managment, what i can not is the "Monitor and Display Settings"

I tried reinstalling that package guidence, but it didnt worked for me.

---

### Post by mithion on 2007-06-06
I have the same problem.  I am guilty of one thing though.  I started playing with system services in order to try to optimize kubuntu.  I must have killed the wrong one or something and now when I run the KDM, it won't let me modify the services and set them to default again.  Also tried the kde-guidance thing, but it didn't work for me.  If someone can tell me how to set to default the processes that are suppose to run for a correct linux session, I think that might be helpful.

---

### Post by urvaius on 2007-06-13
i have the same problem with monitor and display

---

### Post by Billy_McBong on 2007-06-17
[COLOR="Blue"]i also get the error when i try to view the monitor and display settings:(
EDIT:the 
```
sudo dpkg-reconfigure kde-guidance
```
did work for me[/COLOR]

---

### Post by AlmaTlust on 2007-06-20
monitor settings can not be loaded on my computer.
Anyway, I know why: I installed (and then removed, because they didn't work) the proprietary ati drivers. That's when the problem started.

---

### Post by 5ER on 2007-06-20
> **uhlive said:**
> I"m having the same problem

me too!

I can't believe no one can fix this! :evil:

---

### Post by pesalomo on 2007-06-23
Hi,

I rearranged my disk setup using gparted, and then I experienced this problem. The solution was to edit /etc/fstab manually to represent my new disk setup. Then the Disk & Filesystem control panel also worked. 

cheers,

Peter

---

### Post by AlmaTlust on 2007-06-25
After reinstalling xserver-xorg the monitor and display applet worked again.

---

### Post by jvin248 on 2007-09-08
I had the same problem (same error message about missing modules)

fixed with 
Code:
sudo dpkg-reconfigure kde-guidance


Thanks!
J

(this may help on my problem with lost USB thumbdrive automount after installing digicam as this seemed to be an issue about the same time - off to check it out)

---

### Post by jaygo on 2007-10-14
[QUOTE=hellblade;2618382]First try this:
```
sudo aptitude reinstall kde-guidance
```

This worked for me. Thx much.

---

### Post by gefenm11 on 2007-10-24
using
```
sudo dpkg-reconfigure kde-guidance
```
is sufficient

---

### Post by cjfester on 2007-12-26
I have this same prob. I downloaded de Kubuntu gutsy 7.10 livecd and the alternatecd, for 64bits, and this thread occur in all of this versions.

Later, i tryed to download de hardy 8.04 version, in the same two ways (live and alternate cd), and the problem stay.

I disconected all Hard Drives, except one (were the system is), with just the linux dist in 2 partitions only ( /  and swap), the problem continue.

I tried edit fstab, the module disk & filesystem stay dont working.

I used the comands "sudo aptitude install kde-guidance" and "sudo dpkg-reconfigure kde-guidance", it stay dont work.

Nothing work to correct this thread for me and i dont wanna install older versions to keep tis open.

WHAT REALY CAN I DO TO CORRECT THIS ERROR ??

---

### Post by visionary on 2008-02-26
> **Atholm said:**
> Aloha..
I have a problem with my Kubuntu.
When i'm trying to change the settings like Disc and filesystem it tells me:

The module Disc and filesystem could not be loaded.
The diagnostics is:
Possible reasons

-  An error occurred during your last KDE upgrade leaving an orphaned control module
- You have old third party modules lying around.

What can i do?

plz help thanks

Anders Holm



Ok this is a solution i applied.....


I guess most of us would have encountered this error after we try to apply some ubuntu tweaks to speed up the systems.

To reset do this..

**1)back up /etc/fsta**b
[B]
2)sudo gedit /etc/fstab (GNOME USERS) or sudo kate /etc/fstab (For KDE users)[/B]
[B]
3)Look for a line which looks like this[/B]

defaults, errors =remount-ro,data=writeback,noatime 0

Now we need to remove WRITEBACK and NO TIME entries.So delete those two words only.
Make sure the line now looks something like this

nouser,defaults,errors=remount-ro,atime,auto
[B]
I am NOT saying u copy my line above, instead asking you to remove WRITEBACK and NO TIME entries from the line found in your system.[/B]

Now save the file.
Go back to KCONTROL and back into disk & file system. Hopefully that would have resolved your issue.Else reboot your system once and try again,.

Good luck pal.

---

### Post by calibre97 on 2008-07-20
Apparently I've found yet another cause for the Disk and Filesystems module going AWOL.

I have VMWare Server installed and so I added the following line to /etc/fstab so that I can see connected USB drives in my XP guest:
usbfs /proc/bus/usb usbfs auto o o

When that line is active, no joy with Disk and Filesystems. 
When I comment out that line, mucho joy with Disk and Filesystems. 
I have an external USB drive (3.5" drive in a tray in an enclosure) while I do this, so maybe that's the cause but whatever, now I have a work-around:

When I need to do any Disk and Filesystem administration, comment out the usbfs line in /etc/fstab. When I'm done administering, uncomment the line and I'm in business in the VM. 

Hope this helps someone else. I tried everything else including dpkg-reconfigure kde-guidance and apt-get install --reinstall kde-guidance.

---

### Post by gsiliceo on 2008-07-21
Thats a bug easy to fix for the developers you should report it calibre97 im sure it will do much help

---

### Post by calibre97 on 2008-07-22
> **gsiliceo said:**
> Thats a bug easy to fix for the developers you should report it calibre97 im sure it will do much help

That's a good point and I suppose I should...but against whom and how? I suppose it'd be against KDE itself but where do I do that...KDE.org?

---

### Post by hellblade on 2008-07-23
That would be [bugs.kde.org]("http://bugs.kde.org")

Go there and create an account. Then click on "Enter new wish, bug or crash" (top of the page) and follow their guide. If you are not sure which product to submit against, choose "systemsettings" and they will reassign it if necessary.

---

