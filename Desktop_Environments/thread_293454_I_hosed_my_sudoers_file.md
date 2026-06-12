---
title: "I hosed my sudoers file"
date: 2006-11-05
forum: Desktop Environments
---

### Post by Paulr-55 on 2006-11-05
I was trying to set Firestarter to start at login by following the instructions at their website. I could not save my edits to sudoers because it is 'read only'.

So I [ sudo chmod u+rw /etc/sudoers ] and now I can't sudo anything.

How can I undo this damage?

I am running 6.10

---

### Post by mlind on 2006-11-05
Use **visudo** wrapper always to edit /etc/sudoers file

---

### Post by boban on 2006-11-05
It won't be easy in Ubuntu... I just followd your instructions and... bam - no sudo for me too... First of all - you can't touch sudoers file... To edit it use: 

```

sudo visudo

```This file should have read only permissions for root:root. Now - I was lucky, because I had chrooted gentoo in one of terminal... But you'll have to run from Ubuntu live cd (or recovery mode if you haven't disabled it in grub boot  menu). Or if you have enabled root account login, then login as root.

Then mount your / partition somewhere ( sudo mount /dev/your_root_dev dir_to_mount). In rescue mode it should be already mounted...

then type:
```

chmod 0440 /etc/sudores

```(or if mounted, then replace /etc/sudoers with dir_to_mount/etc/sudoers)

Reboot. You should be ok...

---

### Post by Paulr-55 on 2006-11-05
Thank you. But I am still stuck. How can I log in as root so I can change things. Sudo command does not work now.

Is this fixable?

---

### Post by Paulr-55 on 2006-11-05
I posted that last at the same time as you - so I will try that, thanks.

---

### Post by boban on 2006-11-05
> **Paulr-55 said:**
> I posted that last at the same time as you - so I will try that, thanks.

Good luck :)

---

### Post by mlind on 2006-11-05
> **Paulr-55 said:**
> Thank you. But I am still stuck. How can I log in as root so I can change things. Sudo command does not work now.

Is this fixable?

Boot in recovery mode (select recovery option from GRUB boot menu), or alternatively append **1** as a kernel parameter for your current kernel in /boot/grub/menu.lst.


(Example)
```

title           Ubuntu, kernel 2.6.17-10-generic
root            (hd0,0)
kernel          /vmlinuz-2.6.17-10-generic root=/dev/mapper/VolGrp00-LVEdgyRoot ro nosplash **1**
initrd          /initrd.img-2.6.17-10-generic
savedefault
boot


```

---

### Post by Paulr-55 on 2006-11-05
Ok. Recovery mode allowed me to change permissions back to 0440 on /etc/sudoers.

Thanks very much! :)

---

### Post by boban on 2006-11-05
> **mlind said:**
> Boot in recovery mode (select recovery option from GRUB boot menu), or alternatively append **1** as a kernel parameter for your current kernel in /boot/grub/menu.lst.



It's not that easy... Without root permissions you won't be able to change menu.lst. If he has deleted recovery mode from menu.lst he will have to append 'single' to line you pointed from within Grub... but if he has locked Grub... then only livecd is his only rescue...

---

### Post by boban on 2006-11-05
> **Paulr-55 said:**
> Ok. Recovery mode allowed me to change permissions back to 0440 on /etc/sudoers.



Cool! :)

---

### Post by Karbonik on 2006-11-25
What happens if your sudoers file is completely completely hosed, as in I get this as the output:

karbonik@biosolar-laptop:~$ sudo apt-cache search smb
>>> sudoers file: syntax error, line 0 <<<
>>> sudoers file: syntax error, line 1 <<<
>>> sudoers file: syntax error, line 2 <<<
>>> sudoers file: syntax error, line 3 <<<
>>> sudoers file: syntax error, line 4 <<<
>>> sudoers file: syntax error, line 5 <<<
>>> sudoers file: syntax error, line 6 <<<
>>> sudoers file: syntax error, line 7 <<<
>>> sudoers file: syntax error, line 8 <<<
>>> sudoers file: syntax error, line 9 <<<
sudo: parse error in /etc/sudoers near line 0


I get that whenever I try and do anything with sudo
Tried booting into recovery mode and editing it with visudo, and it looks as if the first line is something like:

X Error - something something something
...
...
...
#SMB4k Do not edit
something something

The problems started while I was trying to configure SMB4k, and I don't know exactly what happened.

I'm going to try using the live cd to mount the partition, and then replacing the sudoers file with the one from the live cd, but I'd like to do this without having to do a fresh install.  If needs be, I will however.

EDIT:
Ahh, I must have been thinking ahead, and I saved most of the output, minus the SMB4k stuff to a new file, which I can still access.  Here's the corrupted /etc/sudoers file I have here:

X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults

Defaults    !lecture,tty_tickets,!fqdn

# User privilege specification
root    ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

---

### Post by CatKiller on 2006-11-25
You could use the Recovery mode to start the computer as root, and then use visudo to remove the top of the sudoers file. I don't know how that stuff got there, but mine starts with 
# /etc/sudoers

---

### Post by Karbonik on 2006-11-25
[quote=CatKiller;1806655]You could use the Recovery mode to start the computer as root, and then use visudo to remove the top of the sudoers file. 

Actually, after trying to do the copy/paste from the livecd (which didn't work, as I don't see how to get root privileges on the livecd, hence unable to read locked files) I did exactly that  - I simply ctrl-k (cut) the offending lines down to where the commented lines started, also deleted the Smb4k lines, and now it works again smoothly.

Now I get to check into configuring smb4k (or whatever will work) to be able to mount and read/write to FAT32 shares on the local network (ideally when running ubuntu edgy server, but currently running winXP so that at least my roomates can use it in the time being until I figure the whole samba share thing out.

Yay!

---

### Post by CatKiller on 2006-11-25
> **Karbonik said:**
> Actually, after trying to do the copy/paste from the livecd (which didn't work, as I don't see how to get root privileges on the livecd, hence unable to read locked files)

Normally you can use sudo on the live cd - it just doesn't ask for your password. The sudoers file is designed to not even be writable by root though.

Glad you got it sorted. I don't know anything about Samba to be able to help you with that.

---

### Post by Karbonik on 2006-11-25
> **CatKiller said:**
> Normally you can use sudo on the live cd - it just doesn't ask for your password. The sudoers file is designed to not even be writable by root though.
I actually didn't try to use the konsole on the livecd - I just assumed that since I didn't get the option of opening the file as root then I would be able to do it that way either.  I'll check that out.

On the plus side, this little ordeal made me realize the way to tighten up security on an ubuntu install is to first thing set 

:$ passwd root
(enter your new root password here)

which then saves the worry of anyone coming by your machine and booting into root from the recovery on boot.  Something the Ubuntu developer that handles that aspect may want to look into - forcing a new install to set a root password, even if it is always going to be using sudo, is a basic security measure that I can't imagine would be so hard to incorporate into the next distribution.

Anyway, Catkiller, thanks for the speedy advice.

Hope this helps someone else out down the road.
Just my 2 cents

---

### Post by CatKiller on 2006-11-25
> **Karbonik said:**
> I actually didn't try to use the konsole on the livecd - I just assumed that since I didn't get the option of opening the file as root then I would be able to do it that way either.  I'll check that out.

On the plus side, this little ordeal made me realize the way to tighten up security on an ubuntu install is to first thing set 

:$ passwd root
(enter your new root password here)

which then saves the worry of anyone coming by your machine and booting into root from the recovery on boot.  Something the Ubuntu developer that handles that aspect may want to look into - forcing a new install to set a root password, even if it is always going to be using sudo, is a basic security measure that I can't imagine would be so hard to incorporate into the next distribution.

Actually, it's already even better than that. It generates a random password for root, and then doesn't even tell **you** what it is. Harder to crack than whatever the user would come up with, in all likelihood. But it doesn't matter since there's only one root account. Physical access to the machine is root access. Regardless of what you think you might do to prevent it. There are already many posts on that topic.

---

### Post by Detonate on 2007-02-11
This is kind of an old thread, but it saved me today.  I screwed up my sudoers file.  Instead of merely changing the permissions to get it back, I used vi from the root prompt after booting in recovery mode and edited the file to remove the offending entry I had previously entered.  Next time I do anything to this file, I will change the permissions on it temporarily until I see if it is going to work.

---

### Post by mlind on 2007-02-12
> **Detonate said:**
> This is kind of an old thread, but it saved me today.  I screwed up my sudoers file.  Instead of merely changing the permissions to get it back, I used vi from the root prompt after booting in recovery mode and edited the file to remove the offending entry I had previously entered.  Next time I do anything to this file, I will change the permissions on it temporarily until I see if it is going to work.

You should always use **visudo** to edit /etc/sudoers. It makes sure file structure is valid and permissions are set correctly before you can save the contents.

---

### Post by rudelerius on 2007-05-02
Once I figured out (with help of kvonb on these forums) that the problem I was having was with a corrupt sudoers file, I searched the forum and found a post from aysiu that posted a link to the following web page, which I found very straightforward and helpful for fixing my problem with the sudoers file: [http://www.psychocats.net/ubuntu/sudo]("http://www.psychocats.net/ubuntu/sudo")

---

