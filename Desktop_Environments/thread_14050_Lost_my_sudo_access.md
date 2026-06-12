---
title: "Lost my sudo access"
date: 2005-02-04
forum: Desktop Environments
---

### Post by paul cooke on 2005-02-04
I changed my user name using user manager and now I can't use sudo, even to add my new name to the sudo users file...  :oops: 

launching any of the system tools which require a password has no effect and attempting to launch a command with the terminal that needs sudo gives the following message:

[INDENT]paul_c@cooke-base:~ $ gksudo users-admin

paul_c is not in the sudoers file.  This incident will be reported.[/INDENT]

is there an easy way to correct this?

---

### Post by valadil on 2005-02-04
You need to add yourself to the sudoers file.

Without being root there are a couple of ways to do this.  The easiest would be to boot failsafe mode.  I think that gives you root, but I'm not sure.

The way that I know will work is if you boot off the Ubuntu CD, let it scan your devices, then choose to execute a shell.  mount your hard drive and edit etc/sudoers in there.

---

### Post by paul cooke on 2005-02-04
[QUOTE=paul cooke]I changed my user name using user manager and now I can't use sudo, even to add my new name to the sudo users file...  :oops: 

launching any of the system tools which require a password has no effect and attempting to launch a command with the terminal that needs sudo gives the following message:

[INDENT]paul_c@cooke-base:~ $ gksudo users-admin

paul_c is not in the sudoers file.  This incident will be reported.[/INDENT]

is there an easy way to correct this?[/QUOTE]

solved...

used some tips from this unofficial guide:

[http://www.ubuntuguide.org/#gainrootwithoutlogin](http://www.ubuntuguide.org/#gainrootwithoutlogin)

# Boot-up your computer into Ubuntu Installation CD
# Follow the instructions on screen till (do NOT go further than this)

[!!] Partition disks

and made damned sure I did stop here...

# Press 'Ctrl + Alt + F2'
# Press 'Enter' to activate the console
#

~ # mkdir /ubuntu
~ # fdisk -l /dev/discs/disc0/disc

(which gave a list of my partitions)

~ # mount <wherever your Ubuntu root device is> /ubuntu/
~ # chroot /ubuntu/
sh-2.05b#

now did this:

~ # visudo

which brought up vim editing the sudo file...
(good job I know the basics of using vim ;) )

now found my old username at the bottom and changed it to my new username

then did :w to write the file followed by :q to quit the editor...

then did visudo again to check my changes had been made and just :q to get out

removed the disc from the cd drive (using the end of a paperclip into the little hole trick)
 and rebooted

:)

---

