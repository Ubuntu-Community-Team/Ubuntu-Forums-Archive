---
title: "User home redirected to /root"
date: 2009-03-14
forum: General Help
---

### Post by jbuczek on 2009-03-14
I posted this 5 hours ago but it seems to have disappeared.  Regrets if it's still around and I missed it somewhere.

Using Ubuntu Desktop 8.10

I was following a tutorial to move /home to a new partition.

I booted from the "live CD" and did everything on the list.
-mkdir /mnt/oldhome
-mount /dev/sda5 /mnt/oldhome
mkdir /mnt/newhome
mount /dev/sda6 /mnt/newhome

With sudo where needed.  Then I moved every thing to newhome using a complicated line involving find | cpio

Then               mv /mnt/oldhome/home /mnt/oldhome/home.safe

Then I edited /mnt/oldhome/etc/fstab to add the line for the new partition.

But!!!! I now know, I missed 

mkdir /home

which, I now know, is needed to give the system a place to mount the new partition.  

I rebooted and when I attempted to log in (as john) I got messages more or less like this:

>Unable to find /home/john.  Apparently it does not exist.  Logging in 
          with /root as the home folder.
>Users $Home/.dmrc file is being ignored.  
>Could not update ICE authority file /home/john/.iceauthority
>{something about fonts}

And wound up with an empty desktop from which I could do nothing.

So I checked my tutorial, found the mistake, rebooted from the live CD, corrected it and rebooted again.

Logged in and got those same error messages again although not the message about redirecting to /root and wound up in the same place.

<Ctrl+Alt+F1> to a command line and verified that the new /home and all it's contents is there, mounted, readable, etc.

So how do I cancel this redirection?

I checked the /etc/passwd file, and everything else I could think of, and it still says my home is /home/john.

Googled my head off for two hours and got not a hint.  Can't find the right keywords I suppose.

Help!

BTW, in an attempt to get a little more control, I looked up and used the appropriate command line commands to create a new "system" user ("super").

Logged in as "super" and discovered that "system" users can't sudo.

??? !!!! ???

"Permission denied. User is not in sudoers file. This will be reported!"

What's a system user good for if he/she can't even sudo?

I tried "man sudoers" and got thirty some pages of incomprehensible gibberish telling me how to give restricted powers to restricted groups in a 50,000 workstation net with 1500 servers protecting billions worth of assets but not a hint how to give one lonely user the same priveleges that the install gives to the initial user.

Maybe I exaggerate a bit but not much.  Why can't we have "server" man pages that give every possibility known to science and "desktop" pages that give answers tailored to a small net with ONE administrator and just a few users?

Never mind.  Just venting.

 So can anyone help?

---

### Post by circa82 on 2009-03-14
Would you mind posting a link to the tutorial you followed?

---

### Post by jbuczek on 2009-03-14
I was mostly working from this one with a few minor changes from others.

I ignored the gparted section since I already had a spare partition available.

[https://lists.ubuntu.com/archives/ubuntu-sg/2008-August/000418.html](https://lists.ubuntu.com/archives/ubuntu-sg/2008-August/000418.html)

---

### Post by circa82 on 2009-03-14
If you would again boot from the live CD, open a terminal, and run the following:
*NOTE: I'm using /dev/sda5 and /dev/sda6 as shown in your post. If those are not the correct device names, make sure they are replaced*

```
# [color=blue]sudo mkdir /mnt/old[/color]
# [color=blue]sudo mkdir /mnt/new[/color]
# [color=blue]sudo mount /dev/sda5 /mnt/old[/color]
# [color=blue]sudo mount /dev/sda6 /mnt/new[/color]
```

Now if you would run the following commands and post the output of each:
```
# [color=blue]ls /mnt/new[/color]
# [color=blue]cat /mnt/old/etc/fstab[/color]
```

---

### Post by ugm6hr on 2009-03-14
See: [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

The "What if it doesn't work?" section 3/4 down is what you need.

---

### Post by jbuczek on 2009-03-14
here's the ls of /mnt/new

john  lost+found  super

and here's the cat of fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=24a0986b-872a-49ab-ac74-2d94fcc6e483 /               ext3    relatime,errors=remount-ro 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
# add a 512 Mb swap file manually - This is not a partition.
/mnt/512Mb.swap  none  swap  sw  0 0
# always mount the archive
//192.168.2.20/archive /mnt/ARCHIVE smbfs rw,user,username=john,password=utnubu 0 0
# this is Drive D on the windows boot side
/dev/sda2 /mnt/WinData ntfs-3g quiet,defaults,rs 0 0
/mnt/WinData/"My Documents"/ /mnt/WinHome none bind
# /dev/sda6
/dev/sda6 /home ext3 defaults,noatime,errors=remount-ro 0  0

This is a dual boot with WinXP Pro.  The first partitions are NTFS for that.  sda5 is the original ubuntu partition.  sda6 is the new one.

I guess I'm not being clear here.

I have successfully corrected and completed the process of moving the /home folder to the new partition.

I can creat new users (ex: super) and their home folder is created in the new partition.  When the log in everything is normal for a new user.  I can access all the old files in /home/john indirectly so they are all intact.

My only problem is that Ubuntu somewhere, somehow Ubuntu has redirected the "home" of "john" to /root and I need to know how to change that back.  I already tried restoring everything back to where it was when I started and that made no difference. When I log in as "john" I get the error messages:

>Users $Home/.dmrc file is being ignored.
>Could not update ICE authority file /home/john/.iceauthority
>{something about fonts} 

as described above and I wind up with an empty gnome desktop with no panels, no icons, apparently nothing.  I can <Ctrl+Alt+F1> to a command line and do anything I want there so all other information about my login is intact.

So I put it back where I want to wind up and I'm waiting for info about this "redirect" that Ubuntu did.  I just need to know how to undo that redirect.

---

### Post by jbuczek on 2009-03-14
OK!  I tried this:

boot to single user
chown -R john:john /home/john
chmod 644 /home/john/.dmrc
chmod 644 /home/john/.ICEauthority

ls -l .dmrc
and
ls -l .ICEauthority

to make sure.

Reboot!

>Could not update ICEauthority file /home/john/.ICEauthority
> There is a problem with the configuration server
 /usr/lib/libgconf2-4/gconf-sanity-check-2 exited with status 256

and then my first ever sight of a "screen of death" in linux, black in this case.

Pardon my levity.

So I tried, again, go go back to the stating point:

-boot the live CD
sudo mkdir /recovery
sudo mount -t ext3 /dev/sda5 /recovery
sudo cp -R /recovery/home_bak /recovery/home

which, BTW didn't work because I wound up with:

"ls recovery/home
> home_bak

So 

cd recovery/home/home_bak
ls
> john
sudo cp -R john ..
cd ..
ls
> john   home_bak
sudo rm -Rf /home/home_bak
ls
> john

Then I used gedit to comment out the new (last) line in /recovery/etc/fstab

and reboot

Same error messages.

I've been working at this for 21 hours straight now so I'm going to bed.  If no one has any more suggestions I guess I copy /home/john to a USB drive tomorrow.  Wipe the Ubuntu partition and start over with Ubuntu from scratch, probably taking a couple weeks to get back to "normal".

Ain't computers wunnerful.

Thanks to everyone for the attempts to help.

---

### Post by taurus on 2009-03-14
Boot into recovery mode from GRUB menu and post the outputs of these commands here.

```
sudo fdisk -l
sudo blkid
cat /etc/fstab
ls -la /home/john
```

---

### Post by jbuczek on 2009-03-15
Thanks to everyone for the help.  As the guru's suspected, the problem turned out to be ownership and permissions.  When I did 

ls -la /home/john

I was surprised to see that everything was owned by root and that the permissions on the two critical file were not as instructed (644).  I know I made the changes but I'm guessing that in the multiple "do it" and "undo it" they got changed again.  I'm suspecting that copying something or moving something when I'm logged in as "root" (in single user or live CD mode) automatically changes ownership again.

Anyway........... I went back to recovery mode, made the changes again and things are back to normal.  Many thanks.

---

### Post by circa82 on 2009-03-15
Nevermind ... good to know.

There are easier ways to move your /home directory to a new partition.

---

