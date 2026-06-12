---
title: "I've Made a Stupid Mistake"
date: 2008-12-30
forum: General Help
---

### Post by Exsecrabilus on 2008-12-30
Here is my original topic: [http://ubuntuforums.org/showthread.php?p=6460940&posted=1#post6460940](http://ubuntuforums.org/showthread.php?p=6460940&posted=1#post6460940)

I have found further information.

This is what happened yesterday, when I logged onto my computer:


I tried to view a file in /usr/share/etc/etc/etc/ and was denied the permission to do so. So I started Nautilus (File Browser) as root, and then I thought, instead of starting Nautilus as root everytime I want access to a system file, why don't I change the permissions so that I can view them as a normal account?

But I'm not retarded, just know that before reading on. I selected every folder in Filesystem, and went *right-click -> Properties -> Permissions*. For _Group: Others_ I set _Folder Permissions: Access files_ and _File Permissions: View files_. I didn't go far as to actually let a normal user create and delete files in Filesystem.

Well after that, every single icon image disappeared, and no programs would run. Finally, I rebooted. It started up normal, but suddenly, it stopped, and displayed something like this:

> BusyBox v1.10.2 (Ubuntu 1:1.10.2-1ubuntu6) Built-in shell (ash)
Enter &#8216;help&#8217; for a list of built-in commands.

(initramfs) <blinking cursor here signifying I could type>


I searched around, and read a post about how I should type "exit" to quit the BusyBox thing and resume a normal boot. So I did, and then I found a better clue to what is happening to my computer: I got a message saying something about a kernel panic.

So, can anyone help? I am running Ubuntu 8.10 Intrepid Ibex i386, and I am convinced all my files are gone. But I am not so sure, because upon starting my Ubuntu 8.10 Intrepid Live CD, and opening up *System -> Administration -> Partition Editor* (from the Live CD), I found my hard disk, /dev/sda, was actually occupied 30% with files, exactly the same as before I made my mistake!

---

### Post by redilyn on 2008-12-30
You shouldn't post duplicate messages.

Your files are not gone but you have probably damaged your system beyond repair.

You should never change the permissions on core system files and folders.

Your best bet now is to boot from the livecd. backup your files. Then reinstall ubuntu.

I would suggest creating a separate /home partition when reinstalling. That way you can save your files and settings between re-installations.

In response to your other thread. After booting from the livecd, click places, and look for something the says "X GB Media"

Click on that, when it mounts you should have access to your files.

---

### Post by eBoxNet on 2008-12-30
boot using a live cd and give us the results of ```
ls /dev/disk/by-uuid/ -n
```

---

### Post by eBoxNet on 2008-12-30
oh and something else,you should getting an error message just before it drop you in shell,can you paste this msg pls?

thanks

---

### Post by Exsecrabilus on 2008-12-30
> **redilyn said:**
> You shouldn't post duplicate messages.

Your files are not gone but you have probably damaged your system beyond repair.

You should never change the permissions on core system files and folders.

Your best bet now is to boot from the livecd. backup your files. Then reinstall ubuntu.

I would suggest creating a separate /home partition when reinstalling. That way you can save your files and settings between re-installations.

In response to your other thread. After booting from the livecd, click places, and look for something the says "X GB Media"

Click on that, when it mounts you should have access to your files.

Thanks for trying to help me. But for some reason, when I boot from the Live CD and open up Nautilus and try to click on XX GB Media which is ultimately my hard disk, an error comes up, and I can't view my files.

> **eBoxNet said:**
> oh and something else,you should getting an error message just before it drop you in shell,can you paste this msg pls?

thanks

I'm sorry, but I don't understand what you've just said. I should be getting an error message when I do what? When I run the command you wrote above from my Live CD? Paste your message I'm quoting? Why? Explain your sentence please, thank you.

---

### Post by eBoxNet on 2008-12-30
are you dual booting?
did you try to run ```
ls /dev/disk/by-uuid/ -n
```

can you give us the error (if u have any from boot) ?

---

### Post by eBoxNet on 2008-12-30
just before the shell promtp you should get an error msg,if we have the error and the result of the : ```
ls /dev/disk/by-uuid/ -n
``` we can then check if theres anything wrong with your disk conf.

---

### Post by Exsecrabilus on 2008-12-30
> **eBoxNet said:**
> are you dual booting?
did you try to run ```
ls /dev/disk/by-uuid/ -n
```

can you give us the error (if u have any from boot) ?
I'm not double-booting. Check my second post in this topic, I have a question about your second post in this topic.

Didn't you say I could boot from a Live CD and post the results?

EDIT: Can I type the code you gave me into the BusyBox prompt?

---

### Post by eBoxNet on 2008-12-30
yes you can,open up a terminal windows and type inside ```
ls /dev/disk/by-uuid/ -n
```

---

### Post by redilyn on 2008-12-30
> **Exsecrabilus said:**
> Thanks for trying to help me. But for some reason, when I boot from the Live CD and open up Nautilus and try to click on XX GB Media which is ultimately my hard disk, an error comes up, and I can't view my files.

What is the error message you get when you try to open X GB Media??

Someone correct me if I'm wrong but changing the file permissions as you described should not have prevented the partition from being mounted.

Have you tried the following from the terminal

```

sudo chmod 777 -R /dev/sdaX

```

Where X is your partition number (ie sda1 or sda2)

This will not fix your system but may give you access to your files again.

---

### Post by albinootje on 2008-12-30
> **Exsecrabilus said:**
>  I am running Ubuntu 8.10 Intrepid Ibex i386, and I am convinced all my files are gone. But I am not so sure, because upon starting my Ubuntu 8.10 Intrepid Live CD, and opening up *System -> Administration -> Partition Editor* (from the Live CD), I found my hard disk, /dev/sda, was actually occupied 30% with files, exactly the same as before I made my mistake!

Your files should be there.
Do you have any usb-disk or usb-stick or DVD or cdroms to use ?
I recommend booting from the live cdrom, and then back up your important data (/etc and /home) from your hard disk, and do a fresh new install.

---

### Post by eBoxNet on 2008-12-30
yeah i think you are right ,he gave permissions to filesystem only to root right?

---

### Post by redilyn on 2008-12-30
> **eBoxNet said:**
> yeah i think you are right ,he gave permissions to filesystem only to root right?

Thats what I'm thinking. Hopefully chmod will resolve the issue.

---

### Post by eBoxNet on 2008-12-30
could it work if he boot live cd and run gksudo nautilus and then try to access the disk?

---

### Post by redilyn on 2008-12-30
Yep, that should work as well...I think.

Really, we need the error messages. Then we can make a more educated suggestion.

---

### Post by eBoxNet on 2008-12-30
yes thats for sure

---

### Post by albinootje on 2008-12-30
> **eBoxNet said:**
> could it work if he boot live cd and run gksudo nautilus and then try to access the disk?

Maybe. But it's unclear to me what the user has changed concerning permissions, and ending up with a busybox prompt, and then with a kernel panic is simply to much to deal with imho.
Therefore I recommend a fresh reinstall after making backups first.

However if you want to spend time on this problem by using chmod, feel free to try of course, my quick impression is that it's gonna be a waste of time or a long and cumbersome process, but I could be wrong of course.

We're all humans,robots,animals, and animal-robots after all ;)
(And Futurama rules) :)

GL!

---

### Post by eBoxNet on 2008-12-30
i think its a good opportunity to get more experience.

---

### Post by redilyn on 2008-12-30
> **albinootje said:**
> Maybe. But it's unclear to me what the user has changed concerning permissions, and ending up with a busybox prompt, and then with a kernel panic is simply to much to deal with imho.
Therefore I recommend a fresh reinstall after making backups first.

However if you want to spend time on this problem by using chmod, feel free to try of course, my quick impression is that it's gonna be a waste of time or a long and cumbersome process, but I could be wrong of course.

We're all humans,robots,animals, and animal-robots after all ;)
(And Futurama rules) :)

GL!

While I agree, in the end a reinstall is going to be necessary. 

BUT

What we are trying to do is save his files. He can not backup as he can not mount the partition.

This is what we are discussing

---

### Post by Exsecrabilus on 2008-12-30
> **eBoxNet said:**
> yes you can,open up a terminal windows and type inside ```
ls /dev/disk/by-uuid/ -n
```
```
ubuntu@ubuntu:~$ ls /dev/disk/by-uuid/ -n 
total 0 
lrwxrwxrwx 1 0 0 10 2008-12-30 14:37 1a7efeec-ccf3-4b45-a423-90d201188f66 -> ../../sda1 
lrwxrwxrwx 1 0 0 10 2008-12-30 14:34 4cf8f4c4-dc72-4c99-955e-905c5f21f90f -> ../../sda5 
lrwxrwxrwx 1 0 0 10 2008-12-30 14:38 C032-E10C -> ../../sdb1 
ubuntu@ubuntu:~$  
```

That came out in one second.

> **redilyn said:**
> What is the error message you get when you try to open X GB Media??

Someone correct me if I'm wrong but changing the file permissions as you described should not have prevented the partition from being mounted.

Have you tried the following from the terminal

```

sudo chmod 777 -R /dev/sdaX

```

Where X is your partition number (ie sda1 or sda2)

This will not fix your system but may give you access to your files again.

Strangely, this time, the error did not come up when I first clicked the XX.X GB Media in Nautilus's Places sidebar. It had no Eject button, signifying it wasn't mounted, and my clicking it did so.

It went like this, from the Live CD GNOME Terminal:

```
ubuntu@ubuntu:~$ sudo chmod 777 -R /dev/sda1
ubuntu@ubuntu:~$ 
```

I am worried, because:

-1: When changing permissions of 10+ GB files, it took a few minutes, when I first did it, but this time, it took like 1 second, because the second line came right after, signifying the task was done.
-2: My suspicions were proven correct when I clicked upon the XX.X GB Media upon the Live CD Desktop and still found it empty.

---

### Post by eBoxNet on 2008-12-30
yes i think at the end he will reinstall cause it will a huge pain to restore all the permissions on filesystem folders,as you said at least we will help him backup his files.

hate to say that but i think that its MUCH easier and faster to backup and then reinstall :(

---

### Post by Exsecrabilus on 2008-12-30
> **eBoxNet said:**
> yes i think at the end he will reinstall cause it will a huge pain to restore all the permissions on filesystem folders,as you said at least we will help him backup his files.

hate to say that but i think that its MUCH easier and faster to backup and then reinstall :(

I posted my results. Look at the last post on the second page.

---

### Post by eBoxNet on 2008-12-30
can you pls try to normal boot and give us any error you get before it drop you on shell? this may be useful

---

### Post by albinootje on 2008-12-30
> **Exsecrabilus said:**
> ```
ubuntu@ubuntu:~$ ls /dev/disk/by-uuid/ -n 
total 0 
lrwxrwxrwx 1 0 0 10 2008-12-30 14:37 1a7efeec-ccf3-4b45-a423-90d201188f66 -> ../../sda1 
lrwxrwxrwx 1 0 0 10 2008-12-30 14:34 4cf8f4c4-dc72-4c99-955e-905c5f21f90f -> ../../sda5 
lrwxrwxrwx 1 0 0 10 2008-12-30 14:38 C032-E10C -> ../../sdb1 

Can you mount those permissions manually (Assuming /dev/sda5 is swap) ?
[code]
sudo mkdir /media/sda1 /media/sdb1
sudo mount /dev/sda1 /media/sda1 
sudo mount /dev/sdb1 /media/sdb1
mount

```
And please post the output of that last command.

Use gksu nautilus to browse them if needed.

---

### Post by redilyn on 2008-12-30
I suspect that can't be good.

Do you have any really important files on your computer you MUST save??

If not, time to reinstall.

If so, Open partition editor and ensure it still says 30% or whatever used. Then try mounting your partition manually as described above.

While your in partition editor do you mind posting your partition number sdaX (is sda1 where your data is??)

---

### Post by Exsecrabilus on 2008-12-30
> **eBoxNet said:**
> can you pls try to normal boot and give us any error you get before it drop you on shell? this may be useful
How could I do that? Thankfully, a few weeks ago, I turned off "quiet" and "splash" so I can see the log of my boot.

You mean before the BusyBox shell comes up, right? Yeah, but how would I do that? Thanks.

---

### Post by eBoxNet on 2008-12-30
pls try albinootje and redilyn posts,they are faster and better than my suggestion,we are heading to the end i think we will soon know what's going on on your hdd.

---

### Post by Exsecrabilus on 2008-12-30
> **albinootje said:**
> Can you mount those permissions manually (Assuming /dev/sda5 is swap) ?
```

sudo mkdir /media/sda1 /media/sdb1
sudo mount /dev/sda1 /media/sda1 
sudo mount /dev/sdb1 /media/sdb1
mount

```
And please post the output of that last command.

Use gksu nautilus to browse them if needed.

```
ubuntu@ubuntu:~$ sudo mkdir /media/sda1 /media/sdb1
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /media/sda1
ubuntu@ubuntu:~$ sudo mount /dev/sdb1 /media/sdb1
ubuntu@ubuntu:~$ mount
/proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
/dev/scd0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sda1 on /media/disk-1 type ext3 (rw,nosuid,nodev,uhelper=hal)
/dev/sdb1 on /media/disk type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=999,utf8,umask=077,flush)
/dev/sda1 on /media/sda1 type ext3 (rw)
/dev/sdb1 on /media/sdb1 type vfat (rw)
ubuntu@ubuntu:~$ 
```

I have posted a screenshot of my Partition Editor displaying my partitions. The 30% thing wasn't actually 30%, just made that up because a difference between 20% and 30% doesn't really matter to the problem.

---

### Post by Exsecrabilus on 2008-12-30
Wow, your suggestion on gksu nautilus was genius. It works. My files are there.

I should back up and reinstall? I think I saw an error about /sbin/init not existing or something.

---

### Post by redilyn on 2008-12-30
Yes backup and reinstall.

I would suggest when you reinstall that you partition your system so you have:

/ partition

&

/home partition

That way if this happens again your settings and data files are safe or at least safer :)

---

### Post by eBoxNet on 2008-12-30
its good to know you have your files back :)

---

### Post by Exsecrabilus on 2008-12-30
> **redilyn said:**
> Yes backup and reinstall.

I would suggest when you reinstall that you partition your system so you have:

/ partition

&

/home partition

That way if this happens again your settings and data files are safe or at least safer :)
I've always read about a separate home partition, but never fully understood that.

How would I do that with Ubuntu's Ubiquity Live Installer?

---

### Post by Sef on 2008-12-30
> I've always read about a separate home partition, but never fully understood that.

How would I do that with Ubuntu's Ubiquity Live Installer?

You would have to manually partition the hard drive.   It is not hard, but it is nervewracking the first time.

---

### Post by redilyn on 2008-12-30
_Backup Your Data Before Doing The Following!!!_

This is from memory, Hopefully you can fill in any blanks

When you get to the partition screen choose manual

Then delete your exisiting partition (might as well leave the swap though)

Create new partition, choose type ext3 or whatever you like, size somewhere between 10GB and 20GB, then mount point /

Next Create another new partition choose type ext3 or whatever you like, leave size alone, then mount point /home

Ask any questions you may have before you commit the changes!

---

### Post by sarang on 2008-12-30
About the [FONT="Courier New"]chmod -R 777 /dev/sdaX[/FONT] suggestion:

Do _not_ do it on your root partition - it will ruin the permissions of many system files and your system will be injured even more. For example, sudo will throw errors because of incorrect permissions on its files, ssh server will not allow you to connect etc.

If you decide that you have lost all hope of recovering your current system and you want to get your data and do a complete reinstall, abandoning all hope of repairing the current system, then feel free to do [FONT="Courier New"]chmod -R 777 /dev/sdaX[/FONT] on your root partition, but otherwise, do not do it!

---

### Post by eBoxNet on 2008-12-30
> **sarang said:**
> About the [FONT="Courier New"]chmod -R 777 /dev/sdaX[/FONT] suggestion:

Do _not_ do it on your root partition - it will ruin the permissions of many system files and your system will be injured even more. For example, sudo will throw errors because of incorrect permissions on its files, ssh server will not allow you to connect etc.

If you decide that you have lost all hope of recovering your current system and you want to get your data and do a complete reinstall, abandoning all hope of repairing the current system, then feel free to do [FONT="Courier New"]chmod -R 777 /dev/sdaX[/FONT] on your root partition, but otherwise, do not do it!

i think we should say : DO NOT chmod anything that you don't really need 2 and DO NOT chmod filesystem partition or even directories.

just be sure you know what are you doing before you chmod something.
and of course...a backup is always a useful thing to have :p

---

### Post by redilyn on 2008-12-30
> **sarang said:**
> About the [FONT="Courier New"]chmod -R 777 /dev/sdaX[/FONT] suggestion:

Do _not_ do it on your root partition - it will ruin the permissions of many system files and your system will be injured even more. For example, sudo will throw errors because of incorrect permissions on its files, ssh server will not allow you to connect etc.

If you decide that you have lost all hope of recovering your current system and you want to get your data and do a complete reinstall, abandoning all hope of repairing the current system, then feel free to do [FONT="Courier New"]chmod -R 777 /dev/sdaX[/FONT] on your root partition, but otherwise, do not do it!

Please read the thread before posting.

You are correct, under normal circumstances never run that command.

But as discussed in this thread, the users system was already borked, and a reinstall was necessary. 

The user could not see any files on that partition cause they were owned by root. That command was suggest as a way to get access to his files from a livecd so he could backup.

> 
DO NOT chmod anything that you don't really need 2 and DO NOT chmod filesystem partition or even directories.

Exactly!

---

### Post by Exsecrabilus on 2008-12-30
> **redilyn said:**
> _Backup Your Data Before Doing The Following!!!_

This is from memory, Hopefully you can fill in any blanks

When you get to the partition screen choose manual

Then delete your exisiting partition (might as well leave the swap though)

Create new partition, choose type ext3 or whatever you like, size somewhere between 10GB and 20GB, then mount point /

Next Create another new partition choose type ext3 or whatever you like, leave size alone, then mount point /home

Ask any questions you may have before you commit the changes!

So should I leave linux-swap in place or not? If I choose to destroy it, the new installation will make another one for me anyway, is that why you said leave it as it is?

---

### Post by eBoxNet on 2008-12-30
i didn't reply to you i just wrote that as a conclusion,i know why you gave this suggestion and it was a good one.

"i followed the thread"

sorry i didn't want to make you think that i don't respect your post.

---

### Post by albinootje on 2008-12-30
> **redilyn said:**
> Yes backup and reinstall.

I would suggest when you reinstall that you partition your system so you have:

/ partition

&

/home partition

That way if this happens again your settings and data files are safe or at least safer :)

+1
That also makes it easier to install, and easier to have a dual-boot Linux/Linux where you can share the /home partition.
And with a separate /home you can use the mount option "noexec" as an extra security measure while browsing the internet :)

---

### Post by redilyn on 2008-12-30
> **Exsecrabilus said:**
> So should I leave linux-swap in place or not? If I choose to destroy it, the new installation will make another one for me anyway, is that why you said leave it as it is?

If you delete the swap you will have to create a new one in the manual partitioning screen,

If you leave your existing swap as it is, the installer will use that swap space by default.

---

### Post by Exsecrabilus on 2008-12-30
> **albinootje said:**
> +1
That also makes it easier to install, and easier to have a dual-boot Linux/Linux where you can share the /home partition.
And with a separate /home you can use the mount option "noexec" as an extra security measure while browsing the internet :)
After I do that, and I want to install a second Linux distribution, which, by your word, will be easier, how should I install that second distribution?

> **redilyn said:**
> If you delete the swap you will have to create a new one in the manual partitioning screen,

If you leave your existing swap as it is, the installer will use that swap space by default.

So I shouldn't erase it if I don't want to create one manually, which I don't?

---

### Post by redilyn on 2008-12-30
> **eBoxNet said:**
> i didn't reply to you i just wrote that as a conclusion,i know why you gave this suggestion and it was a good one.

"i followed the thread"

sorry i didn't want to make you think that i don't respect your post.

Sorry, that post was not directed at you.

My Internet is very slow where I am so you got a post out before I finished my reply.

Just glad the problem is resolved! :)

---

### Post by eBoxNet on 2008-12-30
no hard feelings man,we are all glad he get his files back ;)
i think its time to mark as SOLVED and close this one so any other users can follow this one.

---

### Post by redilyn on 2008-12-30
> **Exsecrabilus said:**
> After I do that, and I want to install a second Linux distribution, which, by your word, will be easier, how should I install that second distribution?

Leave extra space so you can create another partition.

When you install the other distro install it to that free space and use the same /home partition that you use for ubuntu. Someone correct me if I'm wrong here, I've never done it myself.


> **Exsecrabilus said:**
> 
So I shouldn't erase it if I don't want to create one manually, which I don't?

Do not delete the swap.

---

### Post by Exsecrabilus on 2008-12-30
Huge problem. Thank goodness you guys didn't leave yet.

I started up Ubiquity. It couldn't find any hard disks. WTFimscrewed.

Do I need to start Ubiquity in root mode or something? Wait, why would my hard disk get affected just because I changed the permissions of its contents? I'm confused.....

---

### Post by albinootje on 2008-12-30
> **Exsecrabilus said:**
> After I do that, and I want to install a second Linux distribution, which, by your word, will be easier, how should I install that second distribution?



So I shouldn't erase it if I don't want to create one manually, which I don't?

Erhmm, this is a bit of a difficult question to answer.
I didn't want to encourage you to have a dual-boot Linux/Linux, just wanted to inform you about another advantage of having a separate /home partition.

For a dual-boot or triple-boot Linux machine I've always used Grub for the MBR from one Linux-installation, and then don't let Grub write to the MBR with the second Linux-installation, and I've done the editing of the Grub config myself.
But I've seen installation with Debian and also Ubuntu afair where Grub would recognize the earlier Linux installation and add the boot options for that to the Grub menu.

But again, for now, I suggest to back up your important files (Think of /home and /etc to start with) and then do a fresh installation over your old installation formatting all.
And then spend some time on reading about, and playing with chmod and permissions and some basic Linux system administration.

[https://help.ubuntu.com/](https://help.ubuntu.com/) and [https://wiki.ubuntu.com/](https://wiki.ubuntu.com/) are good places to start.

---

### Post by albinootje on 2008-12-30
> **Exsecrabilus said:**
> Huge problem. Thank goodness you guys didn't leave yet.

I started up Ubiquity. It couldn't find any hard disks.

Did you make your backups and are you starting the new installation now ?
It looks like you forgot to fill in a mount point for /

---

### Post by Exsecrabilus on 2008-12-30
> **albinootje said:**
> Did you make your backups and are you starting the new installation now ?
It looks like you forgot to fill in a mount point for /
I can't. The option doesn't come up. I had the steps for Language, Keyboard Layout, Location, and that was the fourth step. Nothing else.

What's the matter? :(

---

### Post by redilyn on 2008-12-30
Can you still see the partitions in the partition editor??

Question for albinootje:

Why do you backup /etc?? Is it because there are data files in there? I've never heard that suggested before today.

Should he maybe create 3 partitions then? /, /home & /etc?? 

Maybe something to try if I ever have to reinstall :)

---

### Post by Exsecrabilus on 2008-12-30
> **redilyn said:**
> Can you still see the partitions in the partition editor??

Question for albinootje:

Why do you backup /etc?? Is it because there are data files in there? I've never heard that suggested before today.

Should he maybe create 3 partitions then? /, /home & /etc?? 

Maybe something to try if I ever have to reinstall :)
Yes. I right-click on it, and the options I am able to do are Delete, Resize/Move, Copy, Format to (list all filesystem types here), Manage Flags, Check, Label, Information.

Is there anything I should do there to enable its visibility in Ubiquity?

---

### Post by albinootje on 2008-12-30
> **Exsecrabilus said:**
> I can't. The option doesn't come up. I had the steps for Language, Keyboard Layout, Location, and that was the fourth step. Nothing else.

What's the matter? :(

Can you open a terminal, and post the output of :
```

sudo fdisk -l
lshw -c disk -c storage -sanitize

```
And did you back up your data now or not ?
Would be very useful to know before we help you any further.

---

### Post by albinootje on 2008-12-30
...

---

### Post by albinootje on 2008-12-30
> **redilyn said:**
> Question for albinootje:

Why do you backup /etc?? Is it because there are data files in there? I've never heard that suggested before today.


The directory /etc/ holds all the global configuration files, like /etc/X11/xorg.conf
For a home desktop installation it's indeed usually not needed to make a backup of that.

---

### Post by redilyn on 2008-12-30
Ahh okay. I was just curious!!

---

### Post by Exsecrabilus on 2008-12-30
I think God's playing a joke with me.

I restarted the Live CD, and it works again.

I don't get how I can create a separate /home partition, as it doesn't even give me the option of creating a / partition.

Under /dev/sda, am I supposed to click New partition table and then what?  Ext3 journaling file system? Primary or Logical? Beginning or End? What Mount point? T_T

---

### Post by redilyn on 2008-12-30
Give me a few minutes to boot to a live cd and I will give you step by step directions

---

### Post by tanxiaojing on 2008-12-30
Welcome to [http://www.nikeboss.com]("http://www.nikeboss.com")
There are different kinds of products and different brands in this website. The merchandises are of good quality and at the lowest price. I really hope you can find something you need.
The lowest price is our characteristic, high quality is our foundation, good service is our duty. Totally, customer satisfaction is our mission. Our company insists that ‘Customer is god; Quality is first, price is reasonable’.
We sincerely hope that we can do business with you in the near future, and make progress together and create the prospect future!
More details please search nikeboss.com
Or contact me [http://nikeboss@live.com]("http://nikeboss@live.com")

---

### Post by redilyn on 2008-12-30
**Important:** If you have not done so yet, stop, and backup your files!!

Okay 

-Go to step 4 of the install
-Choose Manual and click Forward
-Choose your existing partition and click Delete
-Choose the unpartitioned space and click New Partition
-Choose the following Values

Type Of New Partition: Primary
New Partition Size: 20000 (for approx 20GB partition)
Location Of New Partition: Beginning
Use As: ext3
Mount Point: /


-Click Ok
-Choose the unpartitioned space and click New Partition
-Choose the following Values

Type Of New Partition: Primary
New Partition Size: Leave Size As It Is To Use All Available Free Space
Location Of New Partition: End
Use As: ext3
Mount Point: /home

-Click Ok
-Click Forward
-Continue with the installation

---

### Post by Exsecrabilus on 2008-12-30
OK, I understand now.

I deleted my /dev/sda partition using GParted, and started Ubiquity after that.

I now understand _Mount point_, but do not understand _Primary or Logical_, and which filesystem I should use.

I should create two partitions, right? One with the mount point / and the other with the mount point /home.

Is that right? Then do I use _Ext3 journaling file system_ for both of them?

EDIT: I saw your post, thanks a lot. We posted at the same time. XD

When I get the chance, I am going to thank everyone who posted in this topic by thanking each post that they posted.

---

### Post by Exsecrabilus on 2008-12-30
So now it's like:

/dev/sda1 (/) - 24% - ext3
/dev/sda3 (/home) - 71% ext3
/dev/sda5 (swap) - 3% - linux-swap

Is that right?

BTW, what all the other ones for, like /tmp, /usr, etc.?

---

### Post by albinootje on 2008-12-30
> **Exsecrabilus said:**
> So now it's like:

/dev/sda1 (/) - 24% - ext3
/dev/sda3 (/home) - 71% ext3
/dev/sda5 (swap) - 3% - linux-swap

Is that right?


Looks very good!
But how much is the / now in Gigabytes or Megabytes ?

---

### Post by redilyn on 2008-12-30
I think he has a 75GB hdd.

I suggested 20GB, which is 26% of 75GB so I'd say just under 20GB?

---

### Post by sarang on 2008-12-31
> **redilyn said:**
> Please read the thread before posting.

...

But as discussed in this thread, the users system was already borked, and a reinstall was necessary. 

The user could not see any files on that partition cause they were owned by root. That command was suggest as a way to get access to his files from a livecd so he could backup.



Thanks for the very affectionate 'Please read the thread before posting.' 
I know the problem has been solved, but the suggestion of chmoding /dev/sdaX to 777 recursively is still flawed.
 
If you check the permissions on /dev/sdX on any regular, unborked system, you will see that they are:

```

brw-rw----   1 root   disk      8,   0 2008-10-26 10:28 sda
brw-rw----   1 root   disk      8,   1 2008-10-26 10:28 sda1

```

Those are clearly not 777. chmoding devfs nodes,  i.e. /dev/* is in general a bad idea.

If the block fails to mount, the recursive option (-R) of chmod -R is not going to do anything. You would just be attempting to change permissions of one node on devfs, which is not at all necessary here and will not help in backing up in any way. The -R option makes me think that you expected this to change permissions of all files, but this won't happen. Running chmod -R on a block does _absolutely nothing_ to the files on it. This is the reason why the chmod appeared instantaneous to the original poster, instead of taking a few minutes, as s/he had expected. To change permissions of all files, you have to mount the block and run chmod -R on the mountpoint. However, if the block does mount, after mounting through a live CD, just sudo -s to root and backup as root. 

In any case attempting to change permissions on /dev/sdX is entirely unnecessary and perhaps even likely to be harmful.

Also, I am not convinced that a re-install was necessary here. I have been through this exact situation once and my solutions was to write a script that compares permissions of core files on another machine to th ones on mine and restores mine based on that. It worked. However, I did not post this because it seems that the user already got his  files back and considering that s/he changed permissions on core files, s/he is probably not that experienced with linux (no offense and my apologies), I could not find my script, and asking a user to write a script is not really helpful.

---

### Post by albinootje on 2008-12-31
> **sarang said:**
> 
I know the problem has been solved, but the suggestion of chmoding /dev/sdaX to 777 recursively is still flawed.

Yes, totally.
Any suggestions to do a chmod 777 or chmod 666 permanently should be frowned upon in general, except when it comes to certain web software, or /tmp (chmod 1777)

> 
Also, I am not convinced that a re-install was necessary here. I have been through this exact situation once and my solutions was to write a script that compares permissions of core files on another machine to th ones on mine and restores mine based on that. It worked. However, I did not post this because it seems that the user already got his  files back and considering that s/he changed permissions on core files, s/he is probably not that experienced with linux (no offense and my apologies), I could not find my script, and asking a user to write a script is not really helpful.

Imho you cannot give out some complex bash-script to beginners to try to restore all of their file and directory permissions on their Ubuntu system, if that would work at all.
Messing up permissions system wide ends up in a mess, and it can possible stay in a mess is my impression. It would only work perfectly when the user has a really fresh backup of the whole system, otherwise comparing is not gonna be 100% complete. Why take that risk ?

The reinstall imho also has a little bit of a punishment effect.
If you'd give them some wonderful script which could restore what they have damaged, they might even not learn so much from their mistakes.
Just my 2 euro cents.

---

