---
title: "Deactivate encryption for /home folders &amp; change mountpoint for /home folder"
date: 2009-04-23
forum: General Help
---

### Post by chnorth on 2009-04-23
Hello!

I have just installed the new release of ubuntu 9.04. 
While installing I chose to have my /home folders encrypted.
Now I would like to get rid of this encryption as I am to afraid to somehow lose my data and never be able to decrypt it.

And - I would like to move my /home folder to a seperate partition.

Both things I should probably have done while setting up.

Is there a way to change things from a running system?

Thanks a lot!

chnorth

---

### Post by chnorth on 2009-04-24
No ideas how to turn of the home folder encryption?

Might it be enough to take the user out of the FUSE-Group?
with 
$ sudo fuse deluser username

??
Or is this to much?

Thank you for any help!

chnorth

---

### Post by bajun on 2009-05-24
I have the same question. I need to move my encrypted /home to separate partition. Can I simply move my /home without extra steps?

Update..- I have moved my /home to separate partition inside live CD (another distribution), old /home and new partition was mounted and encrypted data was just placed on new partition without any problems (by copying). fstab was edited. Everething works.

---

### Post by rominet7777 on 2009-06-05
Hi,

Just had the same problem, and just found the solution...

1st thing to do : **_BACKUP YOUR HOME_**
I can't say it louder... basically undoing encryption is equivalent to resetting (rm -rf) your home, which is in fact hidden by a mount.

2nd step : log out of any desktop manager and go to a virtual console (CTRL-ALT-F1)

Finally : for details :

$ ecryptfs-setup-private --undo

In the event that you want to remove your eCryptfs Private Directory setup,
you will need to very carefully perform the following actions manually:

 1. Obtain your Private directory mountpoint
   $ PRIVATE=`cat ~/.ecryptfs/Private.mnt 2>/dev/null || echo $HOME/Private`
 2. Ensure that you have moved all relevant data out of your $PRIVATE directory
 3. Unmount your encrypted private directory
   $ ecryptfs-umount-private
 4. Make your Private directory writable again
   $ chmod 700 $PRIVATE
 5. Remove $PRIVATE, ~/.Private, ~/.ecryptfs
    Note: THIS IS VERY PERMANENT, BE VERY CAREFUL
   $ rm -rf $PRIVATE ~/.Private ~/.ecryptfs
 6. Uninstall the utilities (this is specific to your Linux distribution)
   $ sudo apt-get remove ecryptfs-utils libecryptfs0

I would say step 5 is a bit wrong : there's no need to delete $PRIVATE, which was for me my home....

After .Private and .ecryptfs deletion, just restore your home :]

Cheers

---

### Post by Aviendha09 on 2009-11-02
Yikes! I want to get rid of the encryption but I don't understand the procedure...stuck after the command : 
```
1. Obtain your Private directory mountpoint
$ PRIVATE=`cat ~/.ecryptfs/Private.mnt 2>/dev/null || echo $HOME/Private`
```
expected a return (?)...didn't get any...what now?

---

### Post by undecim on 2009-11-05
> **Aviendha09 said:**
> Yikes! I want to get rid of the encryption but I don't understand the procedure...stuck after the command : 
```
1. Obtain your Private directory mountpoint
$ PRIVATE=`cat ~/.ecryptfs/Private.mnt 2>/dev/null || echo $HOME/Private`
```expected a return (?)...didn't get any...what now?

That's because the output of cat is going to the PRIVATE variable. If you want to check it, type "echo $PRIVATE"

---

### Post by Aviendha09 on 2009-11-10
Worked, phew! Learned something the hard way!:KS

---

### Post by Demosthenesaus on 2009-12-08
I installed full disk encryption on 9.01 on a netbook and enabled /home encryption as well - I now think this was a bad idea?  Should I go through the hassle of removing it as above or just re-install the whole thing again as an easier option?

---

### Post by Aviendha09 on 2009-12-08
The procedure is fairly straigthforward after that point where I hesitated. Higher up in this post there's a link to another one on the subject with more details. 

I think one is better to encrypt small, unimportant folders at first, just to get around the first difficulties one will encounter, without the stress that losing important files generates.

---

### Post by jemmrich on 2010-02-22
> **rominet7777 said:**
> Hi,

Just had the same problem, and just found the solution...

1st thing to do : **_BACKUP YOUR HOME_**
I can't say it louder... basically undoing encryption is equivalent to resetting (rm -rf) your home, which is in fact hidden by a mount.

2nd step : log out of any desktop manager and go to a virtual console (CTRL-ALT-F1)

Finally : for details :

$ ecryptfs-setup-private --undo

In the event that you want to remove your eCryptfs Private Directory setup,
you will need to very carefully perform the following actions manually:

 1. Obtain your Private directory mountpoint
   $ PRIVATE=`cat ~/.ecryptfs/Private.mnt 2>/dev/null || echo $HOME/Private`
 2. Ensure that you have moved all relevant data out of your $PRIVATE directory
 3. Unmount your encrypted private directory
   $ ecryptfs-umount-private
 4. Make your Private directory writable again
   $ chmod 700 $PRIVATE
 5. Remove $PRIVATE, ~/.Private, ~/.ecryptfs
    Note: THIS IS VERY PERMANENT, BE VERY CAREFUL
   $ rm -rf $PRIVATE ~/.Private ~/.ecryptfs
 6. Uninstall the utilities (this is specific to your Linux distribution)
   $ sudo apt-get remove ecryptfs-utils libecryptfs0

I would say step 5 is a bit wrong : there's no need to delete $PRIVATE, which was for me my home....

After .Private and .ecryptfs deletion, just restore your home :]

Cheers


Not to bring up an old thread but in case anyone has errors trying to follow these instructions, here is what I did.

1. Backup the home directory while you are logged in
sudo cp -rp /home/user /home/user.backup
1.1. Check that your home backup has everything!!!
2. reboot into root via grub
3. Delete your home directory
rm -rf /home/user
4. Remove the packages
apt-get remove ecryptfs-utils libecryptfs0
5. Restore your home directory
mv /home/user.backup /home/user
6. reboot
7. Remove any of those .Private .ecryptfs folders
rm -rf ~/.Private
rm -rf ~/.ecryptfs
8. Yay!

This worked for me. Home folder file permissions stay intact and does not bugger up Dropbox or git repos. Some reason my fresh install on Ubuntu 9.10 would not do the first command. Just make sure you think the process through when using rm -rf.

Just wanted to post this not only for my record, but anyone else who encounters problems.

:popcorn:

---

### Post by webdevelopment1 on 2010-10-06
i accidentally removed all my packages in synaptic so now i dont have a GUI it just lets me log into the command prompt as my username... 

while logged in i can access my encrypted data, but i can't get it out of my /home/user directory

any tips?

i'd like to copy the encrypted data out onto another hard drive but its not letting me do that...

---

### Post by webdevelopment1 on 2010-10-06
> **webdevelopment1 said:**
> i accidentally removed all my packages in synaptic so now i dont have a GUI it just lets me log into the command prompt as my username... 

while logged in i can access my encrypted data, but i can't get it out of my /home/user directory

any tips?

i'd like to copy the encrypted data out onto another hard drive but its not letting me do that...

what i did was from within shell i typed


sudo cp -a /home/user /media/disk1

then i entered the password required for sudo and then it copied it all to an unencrypted place on the hard drive that i can read now

so its just 2 steps:

1) type

sudo cp -a /home/user /media/disk1

2) copy /media/disk1 to wherever you want it

this will restore your data

---

### Post by vcrpex on 2010-11-13
> **jemmrich said:**
> Not to bring up an old thread but in case anyone has errors trying to follow these instructions, here is what I did.

1. Backup the home directory while you are logged in
sudo cp -rp /home/user /home/user.backup
1.1. Check that your home backup has everything!!!
2. reboot into root via grub
3. Delete your home directory
rm -rf /home/user
4. Remove the packages
apt-get remove ecryptfs-utils libecryptfs0
5. Restore your home directory
mv /home/user.backup /home/user
6. reboot
7. Remove any of those .Private .ecryptfs folders
rm -rf ~/.Private
rm -rf ~/.ecryptfs
8. Yay!

This worked for me. Home folder file permissions stay intact and does not bugger up Dropbox or git repos. Some reason my fresh install on Ubuntu 9.10 would not do the first command. Just make sure you think the process through when using rm -rf.

Just wanted to post this not only for my record, but anyone else who encounters problems.

:popcorn:

Thanks Jemmrich for the steps. Just followed your steps to remove the encryption on my home drive. it was simply too slow when i read virtualbox on the encrypted drive. Thanks alot.

---

### Post by lorriman on 2010-12-03
> **jemmrich said:**
> Not to bring up an old thread but in case anyone has errors trying to follow these instructions, here is what I did.

1. Backup the home directory while you are logged in
sudo cp -rp /home/user /home/user.backup




For anyone following [jemmrich]("http://ubuntuforums.org/member.php?u=272742")'s advice you may get stuck at this point due to a hidden '.gvfs' (FUSE) mount point that results in an access denied failure of the copying even despite the -p flag.

The solution is to use rsync with an exclusion. See here [http://ubuntuforums.org/showthread.php?t=791693.]("http://ubuntuforums.org/showthread.php?t=791693") It worked for me.

---

### Post by ozone702 on 2011-03-06
> **jemmrich said:**
> 

2. reboot into root via grub


FYI - Logging in with another user and going into Terminal sudo su will work too.  I found that out on another forum and it worked for me.

---

### Post by wuxiz on 2011-05-31
Worked fine for me following jemmrich steps with lucid lynx...
thanks!
Nonetheless note that when I removed ecryptfs-utils I had to rename /home/user.backup/.ecrypts as I got an error from 'apt-get remove' saying that ecryptfs seemed to be used as there exists a .ecryptfs folder in the /home/ folder.

---

### Post by fleamour on 2011-07-24
> **jemmrich said:**
> 2. reboot into root via grub

Not sure what this meant. Tried steps while still logged in & using sudo before each command.  At least I have a backup but step 5 went awry. I guess because I did not understand step 2. For whatever reason only some files were copied back across to home directory.

I am now manually copy & pasting /home/user.backup into /home/user.  Can I salvage this?  I also had some directories that would not delete namely alsa-utils.  This is probably because I did not follow step 2.  Please explain step 2.

---

### Post by frogotronic on 2011-12-20
Will this work for 10.10?

Thanks

---

