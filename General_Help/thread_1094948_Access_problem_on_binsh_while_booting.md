---
title: "Access problem on /bin/sh while booting"
date: 2009-03-13
forum: General Help
---

### Post by stesosaso on 2009-03-13
I have installed Ubuntu Intrepid on separate partition on a Mac Book Pro 3.1. (dual boot with rEFIt)

My partitionning is as follow :

1st : Macintosh HD (hfs+)
2nd : / (ext3)
3rd : /home (ext2)
4st : /swap

This installation permits me to virtualize the installed Ubuntu under OS X. I use it as a local web server (It is easyer to install additional libraries under LAMP then under MAMP especially imagemagick and on top of that I have, in this way, a similar installation as on my production server)

My problem is the following :

After installing SSH server on the booted Ubuntu (not virtualized) and then rebooting it, it came up with the following error message :
```

unable to execute "/bin/sh" Permission denied...
... terminated with status 255
```Rebboting the computer on a Ubuntu Live CD and mounting the "/" partition via nautilus I could see that /bin/sh has as owner and group 1000 instead of root.

I started Nautilus in root rights (sudo nautilus from a terminal under live CD)
and changed the owner and the group to root under the permission tab in nautilus.

Then I verified that the changes have been made, apparently everithing looked allright...

But once I rebooted into the installed Ubuntu (2nd partition) I got the same error message.

I am really not an expert in linux terminal commands, could, please, somebody help me in giving me a step by step terminal procedure ? I do not know how to mount the installed partition from the terminal via the live CD. I have tryed to go into a terminal session on boot sequence via CTRL ALT F1, but it doesn't work...

An other solution would be reinstalling the "/" only without formating the /home. Can this been done ? could somebody explain me the procedure to do so ? Can I realocate the existing /home to a new installation of the "/" after installing it ?

Many thanks in advance for your help and advice, and please excuses my english as it is not my mother language... I am French

---

### Post by heindsight on 2009-03-13
/bin/sh is usually a symbolic link to /bin/dash, so it is possible that the ownership or permissions of dash have been messed up too.

By the way, how did you install the ssh server? Just installing the ubuntu openssh-server package should not mess up any permissions or file ownerships.

Anyway, try the following to fix things:

Boot from the live CD again and open a terminal window. Then do:

```
sudo mount /dev/sda2 /mnt
```
to mount your root partition at /mnt (from your description of your partitioning I assume your ubuntu root partition is /dev/sda2)

```

cd /mnt/bin
ls -l sh dash

```
This should output something like:
```
**-rwxr-xr-x** 1 **root root** 79988 2009-03-09 15:03 dash
**lrwxrwxrwx** 1 **root root**     4 2008-10-29 16:15 **sh -> dash**
```
the dates here aren't so important, what's important are the file permissions, ownersip and the fact that sh is a link pointing to dash (in other words concentrate on the parts of the output that I've made bold).
Read the [ls manual]("http://manpages.ubuntu.com/manpages/intrepid/en/man1/ls.1.html") for more detail on the meaning of the output

If dash is not owned by **root root** (that is user root, group root) then you can fix that using the chown command:
```
sudo chown root:root dash
```
OR if sh does not belong to **root root**, do:
```
sudo chown root:root sh
```

If the permissions of dash aren't **-rwxr-xr-x** as above, do
```
sudo chmod 755 dash
```
This will give the root user full (read write and execute) permission to dash. Other users (including anyone in the root group) will be able to read and execute the file.

You should probably read this too: [uhelp]FilePermissions[/uhelp]

If sh is not a link to dash, then you should replace it with a link to dash:
```
sudo ln -f -s dash sh
```
See the [ln manual]("http://manpages.ubuntu.com/manpages/intrepid/en/man1/ln.1.html") for more detail on this command.

Once you've fixed everything, reboot into your ubuntu installation and see if it works. If it doesn't (or if the permissions and ownership of both sh and dash are correct already), then something else is causing your problem.

---

### Post by stesosaso on 2009-03-13
Thank you so much for your quick reply.

Mounting as you specified is OK

The command ls -l sh dash gives me this as reply :
```
ubuntu@ubuntu:/mnt/bin$ ls -l sh dash
ls: cannot access dash: No such file or directory
-r-xr-xr-x 1 root root 1244960 2008-09-09 23:53 sh

```I have noticed that the right to the sh are not the same as the one you've specified. I have tried this command without any success :

```
ubuntu@ubuntu:/mnt/bin$ sudo chmod 777 sh
chmod: changing permissions of `sh': Read-only file system
```and then :

```
ubuntu@ubuntu:/mnt/bin$ ls -l sh dash
ls: cannot access dash: No such file or directory
-r-xr-xr-x 1 root root 1244960 2008-09-09 23:53 sh

```and due to that the following command does not work too :

```
ubuntu@ubuntu:/mnt/bin$ sudo ln -f -s dash sh
ln: cannot remove `sh': Read-only file system

```If you have any advice, I will appreciate it
Again thank you for your quick help

---

### Post by heindsight on 2009-03-13
That is rather strange. The fact that you don't have dash, that your sh has the wrong permissions and that your filesystem is being mounted read only are causing me to suspect that /dev/sda2 is perhaps not the right partition (either that or you have some serious problems).

Let's take a step back and try again.

First of all, boot from the live CD again, open a terminal, run:
```
sudo fdisk -l
```
and post the output here.

---

### Post by stesosaso on 2009-03-13
You are right sda2 might not beeing the right volume... I would guess for sda3 or sda4, what do you think?
If I remember right my system disk has about 10 Gb space and /home about 15Gb

```
WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          26      204819+  ee  GPT
/dev/sda2              26       15283   122552320   af  Unknown
/dev/sda3   *       15283       16030     6000000+  83  Linux
/dev/sda4           16030       19333    26533203+  83  Linux
ubuntu@ubuntu:/$ 

```

---

### Post by heindsight on 2009-03-13
Looks like sda3 might be your root partition.

If you still have /dev/sda2 mounted on /mnt, do:
```
sudo umount /mnt
```

Then do 
```
sudo mount /dev/sda3 /mnt
cd /mnt/bin
ls -l sh dash
```

and post the output here.

---

### Post by stesosaso on 2009-03-13
here is what I get from this command : 

```
ubuntu@ubuntu:/mnt/bin$ ls -l sh dash
lrwxrwxrwx 1 root root    4 2009-02-05 15:30 sh -> dash

dash:
total 0

```I forgot the first partition witch belongs to rEFIt ... and you couldn't know this, rEFIt creates a partition to make a  MBR like...

---

### Post by heindsight on 2009-03-13
> **stesosaso said:**
> ```
ubuntu@ubuntu:/mnt/bin$ ls -l sh dash
lrwxrwxrwx 1 root root    4 2009-02-05 15:30 sh -> dash

dash:
total 0

```

Apparently your /bin/dash is an empty directory. Looks like you have some very serious problems.

You could perhaps try the following:
Still on the live cd with /dev/sda3 mounted at /mnt, do:
```
sudo rmdir /mnt/bin/dash
sudo cp /bin/dash /mnt/bin/dash
```

That should replace the bin/dash directory on your root partition with the /bin/dash from your live CD. After this you should (hopefully) be able to boot ubuntu normally again. If it works, boot into ubuntu (not from the live cd) and do:
```
sudo apt-get --reinstall install dash
```
to properly fix dash.

I hope that this will get everything back the way it should be, but I can't help wondering how it could have happened that your /bin/dash got replaced by a directory. It makes me wonder whether there are not perhaps other, more serious problems awaiting you. Without knowing exactly what caused this problem, or what else may have been changed/broken in the process, you may want to consider doing a complete reinstall.

---

### Post by stesosaso on 2009-03-13
have done what you told me and here is the result :
```
ubuntu@ubuntu:/mnt/bin$ sudo rmdir /mnt/bin/dash
ubuntu@ubuntu:/mnt/bin$ sudo cp /bin/dash /mnt/bin/dash
ubuntu@ubuntu:/mnt/bin$ ls -l sh dash
-rwxr-xr-x 1 root root 87924 2009-03-13 14:16 dash
lrwxrwxrwx 1 root root     4 2009-02-05 15:30 sh -> dash

```looks better now.
I'll try to reboot on the installed ubuntu and let you know.

By the way, I perhaps know what happend and put me into that trouble.

I had booted on the ubuntu and installed ssh open server, and also reinstalled vmware tools.
after that I rebooted and started under OS X and then started Unbuntu in virtualized mode, but haven't not taken enought care, because I restarted a paused session, and there is the source of my problem, I think

Again many many thanks for your help !

---

### Post by stesosaso on 2009-03-13
I know now that the problem we were taking about is the visible part of the iceberg...

When rebooting had to go into a maintenance on sda3 and had about 0.7% errors on it...

I think it would be wiser reinstalling the system.

Have you any advice for me so that I can reinstall ubuntu from scratch but keeping my /home as it is and reuse it after installation?

Again thanks in advance for your appreciated help and advices.

---

### Post by heindsight on 2009-03-13
> **stesosaso said:**
> 
By the way, I perhaps know what happend and put me into that trouble.

I had booted on the ubuntu and installed ssh open server, and also reinstalled vmware tools.
after that I rebooted and started under OS X and then started Unbuntu in virtualized mode, but haven't not taken enought care, because I restarted a paused session, and there is the source of my problem, I think


It seems very likely that that was what caused your problems. Perhaps it would be a good idea to boot from the live cd again and do an fsck. Don't mount any partitions from your hard drive and do:

```
sudo e2fsck -f /dev/sda3
sudo e2fsck -f /dev/sda4
```

> **stesosaso said:**
> 
Again many many thanks for your help !

you're welcome ;) I hope everything is OK now...

---

### Post by heindsight on 2009-03-13
> **stesosaso said:**
> I know now that the problem we were taking about is the visible part of the iceberg...

When rebooting had to go into a maintenance on sda3 and had about 0.7% errors on it...

I think it would be wiser reinstalling the system.

Have you any advice for me so that I can reinstall ubuntu from scratch but keeping my /home as it is and reuse it after installation?

Again thanks in advance for your appreciated help and advices.

Oh dear, I was afraid something like this might have happened. I think resuming the suspended VM after making changes to the system completely messed up your filesystem.

Well nevermind my previous post then. 

I suggest you first boot from the live cd and do an fsck of your /home partition (the partition should not be mounted):
```
sudo e2fsck -f /dev/sda4
```

After that, mount your /home partition at /mnt:
```
sudo mount /dev/sda4 /mnt
```
Now browse through /mnt in nautilus just to check if everything there seems to be the way it should be.

Finally unmount again:
```
sudo umount /mnt
```

Now you can start the reinstallation and when you get to the part where you have to set up your partitioning, don't change the partition table, use the same /dev/sda3 for / and the same /dev/sda4 for /home, make sure you specify that /dev/sda3 should be reformatted and that /dev/sda4 should NOT be reformatted.

---

### Post by stesosaso on 2009-03-13
That is what the system asked me to do and it came up with 0.7% of errors, errors I had to correct manualy... So I mean that a reinstall of / under a formated sda3 would be the safest solution.

---

### Post by stesosaso on 2009-03-13
Thank you so much for your help [heindsight]("http://ubuntuforums.org/member.php?u=222765") !

I will start as you advised me and then reinstall it formating sda3 and NOT sda4 as you told me.

Schould I install it with a different user, and then, when installation is finished recreate the actual user so that the existing /home is allocated to the right user?

Maybe this it what happens if I reinstall with the right (actual) user at the benning...

---

### Post by heindsight on 2009-03-13
> **stesosaso said:**
> Thank you so much for your help [heindsight]("http://ubuntuforums.org/member.php?u=222765") !

I will start as you advised me and then reinstall it formating sda3 and NOT sda4 as you told me.

Schould I install it with a different user, and then, when installation is finished recreate the actual user so that the existing /home is allocated to the right user?

Maybe this it what happens if I reinstall with the right (actual) user at the benning...

When you're installing and you're asked to create a user account, create a user with the same username as before. Then (as far as your home directory is concerned at least) every thing will be as before...

---

### Post by stesosaso on 2009-03-13
Thank you so much for your help. 

I have now some work to do for the coming week end :D

I wish you a nice WE, and thanks again

---

### Post by heindsight on 2009-03-13
> **stesosaso said:**
> Thank you so much for your help. 

I have now some work to do for the coming week end :D

I wish you a nice WE, and thanks again

Good luck :popcorn:

---

