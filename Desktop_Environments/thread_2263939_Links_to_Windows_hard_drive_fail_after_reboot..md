---
title: "Links to Windows hard drive fail after reboot."
date: 2015-02-04
forum: Desktop Environments
---

### Post by lukon on 2015-02-04
While in Ubuntu 14.04.1 nautilus, I navigate to a folder or file on my Windows NFTS hard drive. I opt to create a link. It creates a link in the same directory. So I drag it to the Ububtu desktop. And I delete the original link in the directory.

I test the link. It works perfectly.

Then I reboot back into Ubuntu and find that the links no longer work.

 When I click on it, I get message box 'The link “so and so folder or file” is broken. Move it to Trash?'

Message box also displays the path that is targeted by the link. The path is correct.

The option buttons displayed by the message box are "Cancel" and "Move link to trash."

A few more attempt at using the link makes the link icon stuck in hilighted selected mode and unresponsive.

Any clue how I can get links to Windows files and folders to last more than one session?

---

### Post by SeijiSensei on 2015-02-04
You need to mount the filesystem at boot using the techniques described here:  [https://help.ubuntu.com/community/MountingWindowsPartitions#Configuring_.2BAC8-etc.2BAC8-fstab](https://help.ubuntu.com/community/MountingWindowsPartitions#Configuring_.2BAC8-etc.2BAC8-fstab)

---

### Post by lukon on 2015-02-04
Oh. I thought the Windows drives were already mounted at bootup. Icons for the Windows drives (I have several) appear in the launcher.

Opening a Windows drive from the launcher works. Does this mean the drive is already mounted, or that the drive gets mounted upon my clicking on the icon?

Well, I would assume that the Windows drive is mounted after I open it from the launcher.

But the link still does not work after I open the Windows drive from the lanucher.

But now here is a really weird thing about this:

The link doesn't work. But if I move the link to another position on the desktop, then try it, it works.

---

### Post by SeijiSensei on 2015-02-04
No, the drives are not mounted at boot.  They are only mounted when you double-click the icon.  They'll be mounted to directories under /media/username.  When you reboot, the mounts will be removed.  Just follow the guide I referenced to add entries to /etc/fstab.  Then they'll always be available at the locations you specify.

---

### Post by lukon on 2015-02-04
Ok. I got the Windows drive in question to be automatically mounted at bootup.

The link still does not work.

And now the trick of moving the link icon to a different place on the desktop has also ceased to work.

And I guess when I added the mounting command into the fstab file, I changed the permissions such that I can no longer make new links to files and folders on that Windows drive.

---

### Post by SeijiSensei on 2015-02-04
On my 14.04 system, the NTFS partition is mounted to /windows with an fstab entry like this:
```
UUID=xxxxxxxxxx /windows        ntfs    defaults,umask=007,gid=46   0  0
```
That was what Ubuntu created during installation.  The partition is mounted as user root with group plugdev (GID=46).  The umask 007 grants root and members of the plugdev group full permissions on that filesystem, while others have no rights at all.  My username is a member of the plugdev group. 

Run the command "groups username" with your username and see what groups you belong to.  If you're not a member of plugdev, add yourself with
```
sudo adduser username plugdev
```
then change the entry in /etc/fstab to one like mine with the appropriate UUID or device specification.  To list the UUIDs for all the devices on your system run the command "blkid".

---

### Post by lukon on 2015-02-04
Thank you, SeijiSensei.

The code you suggest does restore my wright permissions to the Windows drive. I can now make new links again.

However, my original problem remains. My links to files and folders on the Windows drive get broken after reboot. More precisely, the problem is that links made while the Windows drive had been mounted get broken if that drive is then unmounted and re-mounted again.

I found an acceptable solution.

Instead of creating links to Windows folders and files, I create launchers on the desktop.

First, I had to install a thing that allows me to create such launchers. I lost the web page that showed me how to do that, but my terminal history has the command as:

sudo apt-get install --no-install-recommends gnome-panel

Then, I use this command each time I want to create a desktop launcher:

gnome-desktop-item-edit ~/Desktop/ --create-new

This command opens a little window where I get to name the launcher and insert a command.

To make the launcher open a windows folder, the command I put in was:

nautilus /media/SLURP/Luke

This command starts the Nautilus file browser at the path specified after the word “nautilus.”

“SLURP “ is the name of my Windows hard drive. “Luke” is the name of the folder I want Nautilus to open there.

Opening a specific file, I needed to put into the launcher command box the command for opening the application I want to open the file with, like this:

libreoffice -o /media/SLURP/Luke/Nice\ \Times.doc

Most of the time I want to open a file on my Windows hard drive using the LibreOffice program. So the word “libreoffice” comes first.

“-o” is the LibreOffice command parameter for opening a file with the ability to edit. Somewhere on the web is a page that lists other LibreOffice commands.

“/media/SLURP/Luke/Nice\ \Times.doc” is the path to the file on my Windows hard drive that I want LibreOffice to open.

For all launcher commands that specify a path to a Windows drive folder or file, you need to surround spaces in the names of such folders or files with “\”. Notice how the Windows folder called “Nice Times” must be written “Nice\ \Times”.

This basically solves my problem. While links don't work after un-mounting and re-mounting a Windows hard drive (such as when rebooting), these launchers do.

Oh, and these launchers only work if the Windows hard drive they target is mounted at the time you click on them. So yes, it is a good idea to make the Windows hard drive automatically mount on bootup.

---

### Post by yancek on 2015-02-05
> sudo apt-get install --no-install-recommends gnome-panel

This has been the standard method for several versions of Ubuntu, might be since the Unity Desktop but it's always worked for me.

If you have a path with spaces in it, you can also put quotes around the path although the backslash also works as you have found.

---

