---
title: "Virtualbox problems, USB drives and Internet connection"
date: 2009-05-12
forum: General Help
---

### Post by lls666 on 2009-05-12
Hi,

I am running Jaunty as the host machine and Win XP as guest.

Installed Guest additions so shared folders work even though not perfectly (I can drag and drop from the `network location but programs don't want to open/save directly from the network location) and seamless mode works as well.

I can't get the guest to see any attached USB drives though. I have created a filter for the USB and set the remote to `any` but that didn't help.

Also can't access the internet from the guest.

Would really appreciate all help :)

---

### Post by netwarriorwy on 2009-05-12
Hi lls666!

I have a Jaunty fresh install on a HP Pavilion dv6000. 

I also installed virtualbox and created a virtual machine with the following characteristics:
> 
1. 5GB Hard Drive.
2. 512MB RAM.
3. 32MB Video.
4. Audio:Enable audio. Host audio driver: pulse audio. Audio controller: ICH AC97.
5. USB:Enable USB controller. Enable USB 2.0 (EHCI) controller.

This VM has Windows XP as guest.

I installed the guest additions. After doing that I followed this guide for the shared folders.

[http://bioscreencastwiki.com/Setting_up_shared_folders_in_Virtualbox_:_Ubuntu_host_,_Win-XP_guest]("http://bioscreencastwiki.com/Setting_up_shared_folders_in_Virtualbox_:_Ubuntu_host_,_Win-XP_guest")

[COLOR="Blue"]I have no problems at all. Whats more, I can even convert .wav files to .mp3 in the host system using a convertor installed in the guest system.
I hope it helps![/COLOR]:P

---

### Post by lls666 on 2009-05-12
tnx for the reply but it didn't help in my case...

I can open files through windows explorer and then save them, but the `open file` box of the office programs don't want to enter the network place....

OneNote tells me when I try to import the folder with my notes
`You do not have access to this folder. See your system administrator for access to this folder.`

I also still need access to the net via the guest :D

awaiting replies :D

---

### Post by Legace on 2009-05-12
If you have VirtualBox OSE (open source edition), USB won't work. Get the "full" version of VirtualBox from virtualbox.org if you have the OSE version now..

---

### Post by lls666 on 2009-05-12
downloaded. directly from virtualbox' site...

how do I check if it is the OSE?? maybe i managed to download that by mistake  :D

---

### Post by lls666 on 2009-05-12
downloaded the right version from virtualbox again and it says `same version is already installed`.

And I did download it from their website the first time around...

---

### Post by lls666 on 2009-05-12
installed another version of Win XP and the internet works now... 

USB drives aren't recognized though...

anyone??

---

### Post by El Zoido on 2009-05-12
Patience, this isn't a chat you know? ;)

Try this guide, maybe it helps you:

[How to pass through USB devices]("http://tusforyou.com/virtualbox-2-how-to-pass-through-usb-devices-to-guests-on-an-ubuntu-810-host-3/")

Hm, I also remember having to edit some Ubuntu system-file, but I'm not sure if it's still necessary in Jaunty.

---

### Post by lls666 on 2009-05-12
sorry about the numerous posts...

new excited ubuntu user :D

I have followed that link, the problem is that when I right click on the usb icon all the devices are `greyed out` so I can't use them for the guest... they are `inaccessible`...

found this on virtualbox help

>   p, li { white-space: pre-wrap; }  11.5.7. USB not working
 If USB is not working on your Linux host, make sure that the current user is a member of the [FONT= ]vboxusers[/FONT] group. On older hosts, you need to make sure that the user has permission to access the USB filesystem ([FONT= ]usbfs[/FONT]), which VirtualBox relies on to retrieve valid information about your host's USB devices. The rest of this section only applies to those older systems.
 As [FONT= ]usbfs[/FONT] is a virtual filesystem, a [FONT= ]chmod[/FONT] on [FONT= ]/proc/bus/usb[/FONT] has no effect. The permissions for [FONT= ]usbfs[/FONT] can therefore *only* be changed by editing the [FONT= ]/etc/fstab[/FONT] file.
 For example, most Linux distributions have a user group called [FONT= ]usb[/FONT] or similar, of which the current user must be a member. To give all users of that group access to usbfs, make sure the following line is present:
 [FONT= ]# 85 is the USB group[/FONT] [FONT= ]none     /proc/bus/usb     usbfs      devgid=85,devmode=664    0    0[/FONT] Replace 85 with the group ID that matches your system (search [FONT= ]/etc/group[/FONT] for "usb" or similar). Alternatively, if you don't mind the security hole, give all users access to USB by changing "664" to "666".
 The various distributions are very creative from which script the [FONT= ]usbfs[/FONT] filesystem is mounted. Sometimes the command is hidden in unexpected places. For SuSE 10.0 the mount command is part of the udev configuration file [FONT= ]/etc/udev/rules.d/50-udev.rules[/FONT]. As this distribution has no user group called [FONT= ]usb[/FONT], you may e.g. use the [FONT= ]vboxusers[/FONT] group which was created by the VirtualBox installer. Since group numbers are allocated dynamically, the following example uses 85 as a placeholder. Modify the line containing (a linebreak has been inserted to improve readability)
 [FONT= ]DEVPATH="/module/usbcore", ACTION=="add",[/FONT] [FONT= ]    RUN+="/bin/mount -t usbfs usbfs /proc/bus/usb"[/FONT] and add the necessary options (make sure that everything is in a single line):
 [FONT= ]DEVPATH="/module/usbcore", ACTION=="add",[/FONT] [FONT= ]    RUN+="/bin/mount -t usbfs usbfs /proc/bus/usb -o devgid=85,devmode=664"[/FONT] Debian Etch has the mount command in [FONT= ]/etc/init.d/mountkernfs.sh[/FONT]. Since that distribution has no group [FONT= ]usb[/FONT], it is also the easiest solution to allow all members of the group [FONT= ]vboxusers[/FONT] to access the USB subsystem. Modify the line 
 [FONT= ]domount usbfs usbdevfs /proc/bus/usb -onoexec,nosuid,nodev[/FONT] so that it contains 
 [FONT= ]domount usbfs usbdevfs /proc/bus/usb -onoexec,nosuid,nodev,devgid=85,devmode=664[/FONT] As usual, replace the 85 with the actual group number which should get access to USB devices.
 Other distributions do similar operations in scripts stored in the [FONT= ]/etc/init.d[/FONT] directory.


could that be the problem??

can anyone help me to check & fix the issue mentioned above??

running Jaunty and don't have much experience in ubuntu... would appreciate something more step by step :)

cheers

---

### Post by El Zoido on 2009-05-12
Go to Users and Groups in your Systems menu.
There you can administer the groups on your system.
If the needed groups exist make sure that your user-name belongs to that group.

---

### Post by netwarriorwy on 2009-05-12
I installed a Win XP merged with SP2 and installed the VirtualBox version 2.2 trough the command line, doing this:

> 
1. Open a terminal and run this:
wget -q [http://download.virtualbox.org/virtualbox/debian/sun_vbox.asc](http://download.virtualbox.org/virtualbox/debian/sun_vbox.asc) -O- | sudo apt-key add -
This will add the necessary key to your Software Sources.
2. Now open System->Administration->Software Sources, choose the tab Third Party and choose the button Add. Put the following command in the little window that opens.
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) jaunty non-free
This will let you install from repositories.
3. Close The Software Sources, it will ask you to update, do it.
4. If you have previous virtualbox versions installed uninstall them from a terminal, you can us this command:
sudo apt-get purge virtualbox*
5. Install the latest version:
sudo apt-get install virtualbox-2.2


I didn't have to add users to any group. I also didn't have to do anything to use my usb from the host, because I can connect my Zune to the host and use it from the guest.:popcorn:

---

### Post by lls666 on 2009-05-14
I looked at the user groups but couldn't find the usb user... and don't know how to check if my user is part of the other users... 

you guys have a `howto` link about user group basics?? I'll google later in the day when I have time :)

want to try the method that netwarriorwy mentioned but I already put in some time building the current gues machine... could I just save the image of the guest and reload it once I have the newer version (if it will be newer:D) installed and in place??

edit: just saw the scrrenshot above... will have a look at the user groups in win xp as well... maybe I am missing something there...

---

### Post by lls666 on 2009-06-04
solved the problem... was connected to the Group settings in Ubuntu...

I wrote a little howto on a thread that I was hijacking... so if anyone has the same problem have a look here:
[http://ubuntuforums.org/showthread.php?p=7400270#post7400270](http://ubuntuforums.org/showthread.php?p=7400270#post7400270)

---

