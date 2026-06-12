---
title: "I need help"
date: 2009-03-04
forum: General Help
---

### Post by Mr. Bean on 2009-03-04
I am trying out ubuntu is virtualbox and in trying to install the guest additions I get am error.  I went through this in the Virtual box forums and I have given up on them so I am now here, this is what happened at VB


    * Edit post
    * Report this post
    * Reply with quote

Ubuntu guest add-ons in a windows XP host.

Postby classified » Sun Feb 22, 2009 5:47 am
I realize this topic is covered in the forums numerous times, and before anybody jumps down my throat and tells me to read the FAQs I half. I also have done what the FAQ says. Also tried other responses in the forms. I've also spent time on the phone with somebody who is familiar with Ubuntu. and have yet to get a result. Every time I attempted to install the guest add-ons Ubuntu I get an error message saying that I need to log in as an administrator. Even though I am the only administrator. I have tried to re-download my ISO, and install from scratch with the same results. Any help would be greatly appreciated.

classified
     
    Posts: 6
    Joined: Sun Feb 22, 2009 5:17 am

        * Private message

Top

    * Report this post
    * Reply with quote

Postby TerryE » Sun Feb 22, 2009 2:46 pm
OK so when you step through the FAQ - Installation Questions, what is the exact error message at what point?
Read the Forum Posting Guide
Google your Q site:VirtualBox.org or search for the answer before posting.

TerryE
     
    Posts: 2764
    Joined: Wed May 28, 2008 8:40 am

        * Private message
        * Website

Top

    * Report this post
    * Reply with quote

Postby Sasquatch » Sun Feb 22, 2009 8:10 pm
Run the installer with sudo in front of it. That is what the FAQ says, 'run it as root, or use sudo'.
Search before opening a topic.
VB FAQ
User Howto and tutorials
User Manual: Read first, ask later.

Sasquatch
     
    Posts: 6154
    Joined: Mon Mar 17, 2008 1:41 pm
    Location: Netherlands

        * Private message

Top

    * Edit post
    * Report this post
    * Reply with quote

Postby classified » Mon Feb 23, 2009 12:24 am
when I try to open and run in terminal I get a message that says they logged in as an administrator press return to close this window, I am usually a person able to access the computer. Upon running the installer with sudo in front of an idea what appears to be a list of help topics i.e. "mount device to see tree" there are about a dozen or so options such as this that appear on the screen.

classified
     
    Posts: 6
    Joined: Sun Feb 22, 2009 5:17 am

        * Private message

Top

    * Report this post
    * Reply with quote

Postby TerryE » Mon Feb 23, 2009 8:58 am
The wonderful thing about terminal sessions is that cut and paste works. Instead of paraphrasing what you did and what errors were posted just copy the whole sequence so we can actually understand what is going on here.
Read the Forum Posting Guide
Google your Q site:VirtualBox.org or search for the answer before posting.

TerryE
     
    Posts: 2764
    Joined: Wed May 28, 2008 8:40 am

        * Private message
        * Website

Top

    * Edit post
    * Report this post
    * Reply with quote

Postby classified » Tue Feb 24, 2009 5:27 am

Code: Select all   Expand viewCollapse view
    josh@josh-desktop:~$ sudo mount /media/cdrom/cd /media/cdrom/sudo ./VboxAdditions-x86.run
    [sudo] password for josh:
    Usage: mount -V                 : print version
           mount -h                 : print this help
           mount                    : list mounted filesystems
           mount -l                 : idem, including volume labels
    So far the informational part. Next the mounting.
    The command is `mount [-t fstype] something somewhere'.
    Details found in /etc/fstab may be omitted.
           mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
           mount device             : mount device at the known place
           mount directory          : mount known device here
           mount -t type dev dir    : ordinary mount command
    Note that one does not really mount a device, one mounts
    a filesystem (of the given type) found on the device.
    One can also mount an already visible directory tree elsewhere:
           mount --bind olddir newdir
    or move a subtree:
           mount --move olddir newdir
    One can change the type of mount containing the directory dir:
           mount --make-shared dir
           mount --make-slave dir
           mount --make-private dir
           mount --make-unbindable dir
    One can change the type of all the mounts in a mount subtree
    containing the directory dir:
           mount --make-rshared dir
           mount --make-rslave dir
           mount --make-rprivate dir
           mount --make-runbindable dir
    A device can be given by name, say /dev/hda1 or /dev/cdrom,
    or by label, using  -L label  or by uuid, using  -U uuid .
    Other options: [-nfFrsvw] [-o options] [-p passwdfd].
    For many more details, say  man 8 mount .
    josh@josh-desktop:~$

classified
     
    Posts: 6
    Joined: Sun Feb 22, 2009 5:17 am

        * Private message

Top

    * Report this post
    * Reply with quote

Postby TerryE » Tue Feb 24, 2009 3:03 pm

    classified wrote:sudo mount /media/cdrom/cd /media/cdrom/sudo ./VboxAdditions-x86.run


It does look from the error message that you did type this on one line. There's three separate commands here. Put them on three separate lines or use ";" delimiters.

Code: Select all   Expand viewCollapse view
    sudo mount /media/cdrom/
    cd /media/cdrom/
    sudo ./VboxAdditions-x86.run

Read the Forum Posting Guide
Google your Q site:VirtualBox.org or search for the answer before posting.

TerryE
     
    Posts: 2764
    Joined: Wed May 28, 2008 8:40 am

        * Private message
        * Website

Top

    * Report this post
    * Reply with quote

Postby Sasquatch » Tue Feb 24, 2009 11:26 pm
Or use && to execute it in one go.

Code: Select all   Expand viewCollapse view
    sudo mount /media/cdrom && sudo /media/cdrom/VBoxLinuxAdditions-x86.run

Search before opening a topic.
VB FAQ
User Howto and tutorials
User Manual: Read first, ask later.

Sasquatch
     
    Posts: 6154
    Joined: Mon Mar 17, 2008 1:41 pm
    Location: Netherlands

        * Private message

Top

    * Edit post
    * Report this post
    * Reply with quote

Postby classified » Wed Feb 25, 2009 7:26 am

Code: Select all   Expand viewCollapse view
    josh@josh-desktop:~$ sudo mount /media/cdrom && sudo /media/cdrom/VBoxLinuxAdditions-x86.run
    [sudo] password for josh:
    mount: block device /dev/scd0 is write-protected, mounting read-only
    mount: /dev/scd0 already mounted or /media/cdrom0 busy
    mount: according to mtab, /dev/scd0 is already mounted on /media/cdrom0
    josh@josh-desktop:~$

classified
     
    Posts: 6
    Joined: Sun Feb 22, 2009 5:17 am

        * Private message

Top

    * Report this post
    * Reply with quote

Postby TerryE » Wed Feb 25, 2009 7:16 pm
Josh, All this says is that you've already mounted the ISO, so you can skip to the step:

Code: Select all   Expand viewCollapse view
    sudo /media/cdrom/VBoxLinuxAdditions-x86.run


You know that this stuff isn't to do with Virtualbox. It's just basic Linux familiarity. Perhaps you should buy yourself an "Introduction to Linux" book.
Read the Forum Posting Guide
Google your Q site:VirtualBox.org or search for the answer before posting.

TerryE
     
    Posts: 2764
    Joined: Wed May 28, 2008 8:40 am

        * Private message
        * Website

Top

    * Edit post
    * Report this post
    * Reply with quote

Postby classified » Thu Feb 26, 2009 4:36 pm
I go to run the guest additions and get
Verifying archive integrity... All good.
Uncompressing VirtualBox 2.1.4 Guest Additions for Linux installation...........................................................................................................................................................................................................
VirtualBox 2.1.4 Guest Additions installation
This program must be run with administrator privileges. Aborting
Press Return to close this window...

this goes back to the original problem, is this a Linux or a virtualbox issue?

classified
     
    Posts: 6
    Joined: Sun Feb 22, 2009 5:17 am

        * Private message

Top

    * Report this post
    * Reply with quote

Postby TerryE » Thu Feb 26, 2009 5:54 pm
Its a Linux issue. You forgot the sudo prefix. In Linux unlike XP you run as an ordinary user all the time and basically don't have the privileges to do anything unless you prefix the command with sudo.
Read the Forum Posting Guide
Google your Q site:VirtualBox.org or search for the answer before posting.

TerryE
     
    Posts: 2764
    Joined: Wed May 28, 2008 8:40 am

        * Private message
        * Website

Top

    * Edit post
    * Report this post
    * Reply with quote

Postby classified » Thu Feb 26, 2009 6:15 pm
this is the results when I right click the file and have it run in terminal. I was told to do that by Linux people.

classified
     
    Posts: 6
    Joined: Sun Feb 22, 2009 5:17 am

        * Private message

Top

    * Report this post
    * Reply with quote

Postby vbox4me2 » Thu Feb 26, 2009 7:51 pm
Then you have a problem, either listen to the linux people and keep having a problem or listen to TerryE and be a happy camper...
[This space is intentionally left blank] Please read/search the VirtualBox Manual first

vbox4me2
     
    Posts: 409
    Joined: Fri Nov 21, 2008 8:27 pm
    Location: Rotterdam

        * Private message
        * Website

Top

    * Report this post
    * Reply with quote

Postby Sasquatch » Fri Feb 27, 2009 1:29 pm

    vbox4me2 wrote:Then you have a problem, either listen to the linux people and keep having a problem or listen to TerryE and be a happy camper...


Ehm, small correction. Don't listen to only TerryE, but all of us who are helping you. I already told you to use SUDO a week ago.

So please help

---

### Post by malakhi on 2009-03-04
In your Ubuntu virtual machine go to Applications > Accessories > Terminal. Type exactly what you see below, pressing <Enter> after each line. If it asks for your password, enter your password. **Don't** use the right-click menu. Just type it in as you see it below.

```

sudo mount /media/cdrom
sudo /media/cdrom/VBoxLinuxAdditions-x86.run

```

---

### Post by Mr. Bean on 2009-03-06
Thank you very much

---

