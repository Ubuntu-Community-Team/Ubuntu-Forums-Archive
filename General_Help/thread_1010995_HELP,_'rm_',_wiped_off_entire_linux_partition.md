---
title: "HELP, 'rm /*', wiped off entire linux partition"
date: 2008-12-14
forum: General Help
---

### Post by Bulletbeast on 2008-12-14
I just did 'rm /*' by mistake and that resulted in the deletion of everything (thank god my Windows partition wasn't mounted), and I mean everything. If I reboot, terror awaits. Can anyone provide me with a binary of ext3grep (64-bit, if that matters) or help me in any other way? And why does opening "file:///" in Firefox show all files like they used to be, and open text files? (Trying to "download" executables doesn't work, though). I have a terminal open, but I can't even chdir. Help!

---

### Post by cmnorton on 2008-12-14
If the command you listed in your post is actually what you entered, then you did not precede the command with sudo. And, you did not include the -rf switches. That is the good news. 

So, it looks like you blew away every file at / level, but did not recurse into directories. This was still bad, but not as bad as it could be.

I do not know the answer to why firefox shows the files the way they used to be.

When you say everything is wiped off, what are you looking at that says everything is gone?

I've forgotten the single files that are at the / level that would prevent you from operating normally. Try booting again. Maybe you'll only have to recover the system.

---

### Post by northern lights on 2008-12-14
While I don't understand how you could have run this by mistake, if you didn't do so with superuser rights (no *sudo* pre-command) only files owned by the user have been wiped. Thus your system is going haywire because all your user's config files are gone.

You should be able to either reconfigure everything, or, start off afresh by adding a new user.

For the latter option, boot into Recovery Mode, drop to a root shell and run```
useradd NEWUSER
```where NEWUSER should be replaced by the desired login.

Then run```
passwd NEWUSER
```to set the password.

Reboot and login with the new user, it should behave as if you did a clean install.

---

### Post by logos34 on 2008-12-14
yes, it's good you didn't use sudo and -R option...whew

hope northern lights suggestion works for you.  If not there's always [TestDisk ext2 recovery ]("http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_ext2")(I think it would work--ext3 only adds journaling)

---

### Post by Bulletbeast on 2008-12-14
The command was literally 'rm sphere /*', sphere being a subfolder of my home directory. I did a sudo several commands before, which might have stuck, and I'm looking at the messages saying stuff like "dir: No such file or directory".

It seems I have recovered the 'cd' command to my home folder, then cd'd to / without noticing, which led me to think that Firefox can't recover the files. I'll save xterm and see what I can do from there.

---

### Post by jakupl on 2008-12-14
are you sure that the command did anything? I don't think it should.

---

### Post by geirha on 2008-12-14
If you have that terminal you ran the command in open still, try running the following commands and post the results
```
id
ls -l /

```

If you are not in a root shell, and did not prepend the command with sudo, that command should not have deleted anything at all, since rm will not remove directories without the -r switch. If it was run as root (which the id command should show), you have deleted a few symbolic links in / which can be recreated easily.

---

### Post by Bulletbeast on 2008-12-14
> **jakupl said:**
> are you sure that the command did anything? I don't think it should.

Shouldn't it say that I don't have the rights to delete those files?

---

### Post by jakupl on 2008-12-14
> **Bulletbeast said:**
> Shouldn't it say that I don't have the rights to delete those files?

well yes. I just did a leap of faith. here you go.
```

jakup@bobby:~$ rm /*
rm: cannot remove `/bin': Is a directory
rm: cannot remove `/boot': Is a directory
rm: cannot remove `/cdrom': Permission denied
rm: cannot remove `/dev': Is a directory
rm: cannot remove `/etc': Is a directory
rm: cannot remove `/home': Is a directory
rm: cannot remove `/initrd': Is a directory
rm: cannot remove `/initrd.img': Permission denied
rm: cannot remove `/initrd.img.old': Permission denied
rm: cannot remove `/lib': Is a directory
rm: cannot remove `/lost+found': Is a directory
rm: cannot remove `/media': Is a directory
rm: cannot remove `/mnt': Is a directory
rm: cannot remove `/opt': Is a directory
rm: cannot remove `/proc': Is a directory
rm: cannot remove `/root': Is a directory
rm: cannot remove `/sbin': Is a directory
rm: cannot remove `/srv': Is a directory
rm: cannot remove `/sys': Is a directory
rm: cannot remove `/tmp': Permission denied
rm: cannot remove `/usr': Is a directory
rm: cannot remove `/var': Is a directory
rm: cannot remove `/vmlinuz': Permission denied
rm: cannot remove `/vmlinuz.old': Permission denied
jakup@bobby:~$ 

```

---

### Post by northern lights on 2008-12-14
> **jakupl said:**
> I just did a leap of faith.
Respect. I didn't dare try.

Sad part is, we gotta figure another reason for why the OP's system is bonked...

---

### Post by Bulletbeast on 2008-12-14
I only got the 'is a directory' bits...

---

### Post by iponeverything on 2008-12-14
open a vc
clt-alt-f2

login and do "ls /"

I think that all you did was delete directory that you were working in while you were in it and it just confused bash.

---

### Post by northern lights on 2008-12-14
> **Bulletbeast said:**
> I only got the 'is a directory' bits...

[EDIT]
vmlinuz is the a compressed linux kernel
- what was I thinking last night?!
[/EDIT]

Since 'the command' was obviously not as damaging as you thought, can you describe the exact nature of your problem?
What exactly is not working?

---

### Post by jocko on 2008-12-14
> **Bulletbeast said:**
> ...
And why does opening "file:///" in Firefox show all files like they used to be, and open text files? (Trying to "download" executables doesn't work, though). I have a terminal open, but I can't even chdir. Help!

If you can see the files in firefox,** they are still there**.
Otherwise the only way you would see the files in firefox would be if firefox by some magical reason kept a copy of your entire system, which I find very unlikely (where would it keep the files? In RAM?)...

If this was the *exact* command you ran:
```
rm sphere /*
```it would only remove the file "sphere" (but if that's a folder it would fail, as you did not have the "-f" switch). It would also *try* to remove any loose files in your / directory, but would fail as you don't have proper permissions. It would not even *attempt* to remove anything in any subdirectory under /, as you did not have the "-r" switch.
So unless the command really was [sudo rm -rf sphere /*] ([COLOR=Red]<-- Don't even think about using this command...[/COLOR]), you should be perfectly fine. Even with sudo (but without -rf), it would only remove some symlinks to your vmlinuz and initrd files, which is probably not too dangerous...

---

### Post by Bulletbeast on 2008-12-15
@jocko: ...or if firefox somehow neglected their deletion, still reading them from the HDD as if they weren't deleted, because ext3 keeps deleted files, doesn't it?

@iponeverything: Not only bash was confused, but most of my system, in a very peculiar way.

Anyway, the files are still there indeed, and I fixed initrd.img and vmlinuz. However, Ubuntu still doesn't boot, with a message of "Kernel panic: attempted to kill init", preceded by "can't find /sbin/init".

---

### Post by Bulletbeast on 2008-12-15
Booting from Live CD, can't chroot to /media/disk (my Linux partition): 'chroot: cannot run command `/bin/bash': No such file or directory'.

So, to sum it up, after deleting files in my root folder, commands out of the current directory can't be found. Wtf.

---

### Post by Bulletbeast on 2008-12-15
Any help?

---

### Post by amdalex on 2008-12-15
reinstall?

---

### Post by geirha on 2008-12-15
Are the files in bin/ still there?
```
ls -l /media/disk /media/disk/bin
```

---

### Post by Bulletbeast on 2008-12-15
I don't wanna go to the trouble of reinstalling again, I'd much rather find a way to fix it. I read that it might in fact have something to do with vmlinuz and initrd.img, which were the only damaged files, how do I recover them? Other files are intact. /sbin/init has the same size and modification date as on the live cd.

---

### Post by northern lights on 2008-12-15
> **amdalex said:**
> reinstall?
[http://ubuntuforums.org/showthread.php?t=1010875]("http://ubuntuforums.org/showthread.php?t=1010875")

> **Bulletbeast said:**
> I don't wanna go to the trouble of reinstalling again, I'd much rather find a way to fix it. I read that it might in fact have something to do with vmlinuz and initrd.img, which were the only damaged files, how do I recover them? Other files are intact. /sbin/init has the same size and modification date as on the live cd.

Can you run```
sudo apt-get install linux-image-2.26.XX-X-generic
```where *linux-image-2.26.XX-X-generic* should at best be a kernel that is not currently installed?

Can you quote any error messages?
--> It is still unclear, to me at least, what exactly caused your problem in the first place.

---

### Post by jocko on 2008-12-15
> **Bulletbeast said:**
> I don't wanna go to the trouble of reinstalling again, I'd much rather find a way to fix it. I read that it might in fact have something to do with vmlinuz and initrd.img, which were the only damaged files, how do I recover them? Other files are intact. /sbin/init has the same size and modification date as on the live cd.

Those "files" are only symlinks to the real files in your /boot directory.

Boot a live cd and mount the hard drive and check the file names in the /boot directory of your drive.
If the drive is mounted in [COLOR=Blue]/media/disk[/COLOR]:
```
sudo ln -s [COLOR=Blue]/media/disk[/COLOR]/boot/vmlinuz-[COLOR=Red]2.6.27-10-generic[/COLOR] [COLOR=Blue]/media/disk[/COLOR]/vmlinuz
sudo ln -s [COLOR=Blue]/media/disk[/COLOR]/boot/initrd.img-[COLOR=Red]2.6.27-10-generic[/COLOR] [COLOR=Blue]/media/disk[/COLOR]/initrd.img

``` (adjust the red part of the file names to match the real files in your /boot directory)

---

### Post by Therion on 2008-12-15
> **jakupl said:**
> 

well yes. I just did a leap of faith. here you go.
Dude.  

Chuck Norris called.  

He wanted to give you a pair of Brass Balls, but realizes now you've got your own...

---

### Post by geirha on 2008-12-15
> **jocko said:**
> 
```
sudo ln -s [COLOR=Blue]/media/disk[/COLOR]/boot/vmlinuz-[COLOR=Red]2.6.27-10-generic[/COLOR] [COLOR=Blue]/media/disk[/COLOR]/vmlinuz
sudo ln -s [COLOR=Blue]/media/disk[/COLOR]/boot/initrd.img-[COLOR=Red]2.6.27-10-generic[/COLOR] [COLOR=Blue]/media/disk[/COLOR]/initrd.img

``` (adjust the red part of the file names to match the real files in your /boot directory)

Better make that

```
sudo ln -s /boot/vmlinuz-[COLOR=Red]2.6.27-10-generic[/COLOR] [COLOR=Blue]/media/disk[/COLOR]/vmlinuz
sudo ln -s /boot/initrd.img-[COLOR=Red]2.6.27-10-generic[/COLOR] [COLOR=Blue]/media/disk[/COLOR]/initrd.img

```

---

### Post by jocko on 2008-12-15
> **geirha said:**
> Better make that

```
sudo ln -s /boot/vmlinuz-[COLOR=Red]2.6.27-10-generic[/COLOR] [COLOR=Blue]/media/disk[/COLOR]/vmlinuz
sudo ln -s /boot/initrd.img-[COLOR=Red]2.6.27-10-generic[/COLOR] [COLOR=Blue]/media/disk[/COLOR]/initrd.img

```
NO. That would make the links point to the live session "/boot" directory instead of the real one...
The paths in symlinks are only relative paths and not absolute paths, so a link to [COLOR=Blue]/media/disk[/COLOR]/boot/initrd.img-[COLOR=Red]2.6.27-10-generic[/COLOR] will always point to the correct path even if the mount point is changed...

---

### Post by geirha on 2008-12-15
> **jocko said:**
> NO. That would make the links point to the live session "/boot" directory instead of the real one...

Only when running the live session. When the real system boots, it will point to the correct /boot/*

> **jocko said:**
> The paths in symlinks are only relative paths and not absolute paths, so a link to [COLOR=Blue]/media/disk[/COLOR]/boot/initrd.img-[COLOR=Red]2.6.27-10-generic[/COLOR] will always point to the correct path even if the mount point is changed...

No, that will always point to /media/disk/boot/initrd.img-2.6.27-10-generic. It will not change to /boot/initrd.img-2.6.27-10-generic if the mount point changes to /. Test it!

---

### Post by NSAJEFF on 2008-12-15
You got the cajones! =D> I though about trying that command and said, "fsck that!".

> **jakupl said:**
> well yes. I just did a leap of faith. here you go.
```

jakup@bobby:~$ rm /*
rm: cannot remove `/bin': Is a directory
rm: cannot remove `/boot': Is a directory
rm: cannot remove `/cdrom': Permission denied
rm: cannot remove `/dev': Is a directory
rm: cannot remove `/etc': Is a directory
rm: cannot remove `/home': Is a directory
rm: cannot remove `/initrd': Is a directory
rm: cannot remove `/initrd.img': Permission denied
rm: cannot remove `/initrd.img.old': Permission denied
rm: cannot remove `/lib': Is a directory
rm: cannot remove `/lost+found': Is a directory
rm: cannot remove `/media': Is a directory
rm: cannot remove `/mnt': Is a directory
rm: cannot remove `/opt': Is a directory
rm: cannot remove `/proc': Is a directory
rm: cannot remove `/root': Is a directory
rm: cannot remove `/sbin': Is a directory
rm: cannot remove `/srv': Is a directory
rm: cannot remove `/sys': Is a directory
rm: cannot remove `/tmp': Permission denied
rm: cannot remove `/usr': Is a directory
rm: cannot remove `/var': Is a directory
rm: cannot remove `/vmlinuz': Permission denied
rm: cannot remove `/vmlinuz.old': Permission denied
jakup@bobby:~$ 

```

---

### Post by Bulletbeast on 2008-12-15
I can't install a kernel, because I can't chroot to /media/disk. I've made those symlinks from Nautilus, if that's okay, making sure that they have permissions like the ones in the Live CD. I'm going to try if it works now.

It is unclear to me, either, what would cause such a problem, but the event directly preceding it is a 'rm /*'. Errors basically consist of "No such file or directory" for any command outside the current directory. When booting from my hard drive, /sbin/init isn't found, resulting in a Kernel Panic: attempted to kill init. My computer freezes at that point. I've tried a fsck which showed no errors.

---

### Post by jocko on 2008-12-15
> **geirha said:**
> Only when running the live session. When the real system boots, it will point to the correct /boot/*



No, that will always point to /media/disk/boot/initrd.img-2.6.27-10-generic. It will not change to /boot/initrd.img-2.6.27-10-generic if the mount point changes to /. Test it!
Ok, tested it, and it appears I was wrong, the command I gave would make the links with absolute paths.
This is the correct way of making the links with relative paths:
```
cd [COLOR=Blue]/media/disk/[/COLOR]
sudo ln -s boot/vmlinuz-[COLOR=Red]2.6.27-10-generic[/COLOR] vmlinuz
sudo ln -s boot/initrd.img-[COLOR=Red]2.6.27-10-generic[/COLOR] initrd.img
```

---

### Post by geirha on 2008-12-15
> **Bulletbeast said:**
> It is unclear to me, either, what would cause such a problem, but the event directly preceding it is a 'rm /*'. Errors basically consist of "No such file or directory" for any command outside the current directory. When booting from my hard drive, /sbin/init isn't found, resulting in a Kernel Panic: attempted to kill init. My computer freezes at that point. I've tried a fsck which showed no errors.

In the live session, when you mount your / partition to /media/disk. Does /media/disk/sbin/init exist? and does /media/disk/bin/bash exist?

---

### Post by Bulletbeast on 2008-12-15
Yes, they do.

---

### Post by yogo on 2008-12-15
> **jakupl said:**
> well yes. I just did a leap of faith. here you go.




Funniest post I have read all day, has kept me chuckling to myself reading this entire thread.

---

### Post by Bulletbeast on 2008-12-16
Bump...

---

### Post by geirha on 2008-12-16
If /bin/bash exists, it doesn't make any sense that chroot would give you a "no such file or directory". Only reasons I can think of with that happening is that /media/disk wasn't mounted at the time, or /bin/bash is a symbolic link.

How do the symlinks you created look now?
```
ls -l /media/disk /media/disk/boot
```

---

### Post by russo.mic on 2008-12-16
> **jakupl said:**
> well yes. I just did a leap of faith. here you go.
```

jakup@bobby:~$ rm /*
rm: cannot remove `/bin': Is a directory
rm: cannot remove `/boot': Is a directory
rm: cannot remove `/cdrom': Permission denied
rm: cannot remove `/dev': Is a directory
rm: cannot remove `/etc': Is a directory
rm: cannot remove `/home': Is a directory
rm: cannot remove `/initrd': Is a directory
rm: cannot remove `/initrd.img': Permission denied
rm: cannot remove `/initrd.img.old': Permission denied
rm: cannot remove `/lib': Is a directory
rm: cannot remove `/lost+found': Is a directory
rm: cannot remove `/media': Is a directory
rm: cannot remove `/mnt': Is a directory
rm: cannot remove `/opt': Is a directory
rm: cannot remove `/proc': Is a directory
rm: cannot remove `/root': Is a directory
rm: cannot remove `/sbin': Is a directory
rm: cannot remove `/srv': Is a directory
rm: cannot remove `/sys': Is a directory
rm: cannot remove `/tmp': Permission denied
rm: cannot remove `/usr': Is a directory
rm: cannot remove `/var': Is a directory
rm: cannot remove `/vmlinuz': Permission denied
rm: cannot remove `/vmlinuz.old': Permission denied
jakup@bobby:~$ 

```

Your a better man than I!

Russo

---

### Post by Bulletbeast on 2008-12-16
```
ubuntu@ubuntu:~$ chroot /media/disk
chroot: cannot change root directory to /media/disk: Operation not permitted
ubuntu@ubuntu:~$ sudo chroot /media/disk
chroot: cannot run command `/bin/bash': No such file or directory
ubuntu@ubuntu:~$ ls -l /media/disk /media/disk/boot
/media/disk:
total 104
drwxr-xr-x   2 root root  4096 2008-11-14 12:15 bin
drwxr-xr-x   3 root root  4096 2008-12-15 20:13 boot
drwxr-xr-x   4 root root  4096 2008-10-29 21:18 dev
drwxr-xr-x 137 root root 12288 2008-12-14 16:05 etc
drwxr-xr-x   2 1000 1000  4096 2008-11-24 19:05 fix
drwxr-xr-x   4 root root  4096 2008-11-12 19:21 home
drwxr-xr-x  15 root root  4096 2008-11-28 11:39 lib
drwxr-xr-x   4 root root  4096 2008-11-12 17:45 lib32
lrwxrwxrwx   1 root root    44 2008-12-15 20:13 Link to initrd.img-2.6.27-9-gene
ric -> /media/disk/boot/initrd.img-2.6.27-9-generic
lrwxrwxrwx   1 root root    41 2008-12-15 20:13 Link to vmlinuz-2.6.27-9-generic
 -> /media/disk/boot/vmlinuz-2.6.27-9-generic
drwx------   2 root root 16384 2008-06-09 00:47 lost+found
drwxr-xr-x  10 root root  4096 2008-12-14 16:00 media
drwxr-xr-x   2 root root  4096 2008-10-20 12:27 mnt
drwxr-xr-x   3 root root  4096 2008-10-29 21:04 opt
drwxr-xr-x   2 root root  4096 2008-10-20 12:27 proc
drwxrwxrwx   2 root root  4096 2008-12-15 14:59 Recycled
drwxr-xr-x  32 root root  4096 2008-12-13 09:09 root
drwxr-xr-x   2 root root  4096 2008-12-04 11:47 sbin
drwxr-xr-x   3 root root  4096 2008-11-20 21:46 srv
drwxr-xr-x   2 root root  4096 2008-10-14 13:02 sys
drwxrwxrwt  23 root root  4096 2008-12-14 17:58 tmp
drwxr-xr-x  12 root root  4096 2008-11-12 16:54 usr
drwxr-xr-x  15 root root  4096 2008-10-29 21:28 var

/media/disk/boot:
total 44156
-rw-r--r-- 1 root root  420395 2008-10-22 01:49 abi-2.6.24-21-generic
-rw-r--r-- 1 root root  503560 2008-11-04 20:53 abi-2.6.27-7-generic
-rw-r--r-- 1 root root  503560 2008-11-20 23:30 abi-2.6.27-9-generic
-rw-r--r-- 1 root root   74177 2008-10-22 01:49 config-2.6.24-21-generic
-rw-r--r-- 1 root root   85316 2008-11-04 20:53 config-2.6.27-7-generic
-rw-r--r-- 1 root root   85316 2008-11-20 23:30 config-2.6.27-9-generic
drwxr-xr-x 3 root root    4096 2008-11-28 12:14 grub
-rw-r--r-- 1 root root 7737415 2008-10-28 07:41 initrd.img-2.6.24-21-generic
-rw-r--r-- 1 root root 7737411 2008-10-15 06:22 initrd.img-2.6.24-21-generic.bak
-rw-r--r-- 1 root root 8665954 2008-11-28 11:55 initrd.img-2.6.27-7-generic
-rwxrwxrwx 1 root root 8666599 2008-11-28 11:46 initrd.img-2.6.27-9-generic
-rw-r--r-- 1 root root    4420 2008-05-05 14:02 invaders
-rw-r--r-- 1 root root  124152 2008-09-11 20:11 memtest86+.bin
-rw-r--r-- 1 root root 1153201 2008-10-22 01:49 System.map-2.6.24-21-generic
-rw-r--r-- 1 root root 1352144 2008-11-04 20:53 System.map-2.6.27-7-generic
-rw-r--r-- 1 root root 1352144 2008-11-20 23:30 System.map-2.6.27-9-generic
-rw-r--r-- 1 root root    1130 2008-11-04 20:57 vmcoreinfo-2.6.27-7-generic
-rw-r--r-- 1 root root    1130 2008-11-20 23:32 vmcoreinfo-2.6.27-9-generic
-rw-r--r-- 1 root root 1905688 2008-10-22 01:49 vmlinuz-2.6.24-21-generic
-rw-r--r-- 1 root root 2339552 2008-11-04 20:53 vmlinuz-2.6.27-7-generic
-rwxrwxrwx 1 root root 2339712 2008-11-20 23:30 vmlinuz-2.6.27-9-generic
ubuntu@ubuntu:~$
```

As I said, GRUB points to the specific files in /boot. By the way, where/what is the init-bottom (I think) script? That's what's executed before not being able to find /sbin/init.

---

### Post by geirha on 2008-12-17
The symlinks are not right, they are named wrong. Do it from the terminal:
```

sudo ln -s /boot/initrd.img-2.6.27-9-generic /media/disk/initrd.img
sudo ln -s /boot/vmlinuz-2.6.27-9-generic /media/disk/vmlinuz

```

As for chroot. I've googled it a little and it seems it also gives that error message if it is unable to find one of the libraries needed by the shell. Try ```
ldd /media/disk/bin/bash
``` which will show what libraries bash needs in order to run, then look into /media/disk/lib and check that they are all there.

---

### Post by Bulletbeast on 2008-12-17
Bash's libraries are all there, and... how could've I forgotten to change the names? Changed to initrd.img and vmlinuz, rebooting now to see if it works.

---

### Post by geirha on 2008-12-17
The links also had wrong paths, as per the discussion between me an jocko previously in this thread. The links need to point to /boot/... and not /media/disk/boot/...

---

### Post by Bulletbeast on 2008-12-17
Fixed that, rebooting. By the way, it has come upon me that, unless chrooted, ldd would show the dependencies relative to the live cd, and not the hard disk.

---

### Post by Bulletbeast on 2008-12-17
Nope, still doesn't work, although I pasted your commands. If nothing else helps, I'd consider reinstalling. However, since it'd be my first time (previous one was on top of a broken Hardy with most programs removed anyway in order to free up space for the auto-upgrade that eventually broke it), I don't know how should I proceed. How much would be lost if I installed Intrepid on top of itself? Or should I backup /home and do a clean install?

---

### Post by geirha on 2008-12-17
When you chroot to /media/disk, the libraries bash needs will be looked for in /media/disk/lib, yes. BTW. Are you using the same Ubuntu CD as you installed from? I only ask because you'd probably get a problem chrooting if the installed system is 64-bit while the CD is 32-bit.

The installer will insist on formatting the / partition, so all files will be lost if you reinstall. You'll need to backup /home if you want to keep your homedir, unless you have /home on a seperate partition. If you have /home on a seperate partition, you can tell the installer to use that partition as /home, and to not format it.

---

### Post by Bulletbeast on 2008-12-17
Yeah, I'm using the same CD, a 64-bit. Another google shows that such a problem may have all sorts of causes. However, it has brought me to look at the contents of /lib and, guess what, ld-linux.so.2 has an 'unreadable' emblem. /lib/ld-linux.so.2 is a link to /lib32/ld-linux.so.2, which is OK, and points to /lib32/ld-2.8.90.so. Is this because of the live CD or could it be the cause of my problem?

Has rw permissions for all. Error on changing them: no such file or directory. Recreating it using sudo ln -s results in the same file, which leads me to think that it's because of the Live CD.

Yeah, there's no /lib32 on the cd.

---

### Post by geirha on 2008-12-17
I don't have a 64-bit install, but it's probably correct that it points to /lib32/ld-linux.so.2 (64-bit apps use /lib/ld-linux-x86-64.so.2 afaik), and if the CD does not have a /lib32 directory, then it's perfectly normal that that symlink appears broken.

---

### Post by Bulletbeast on 2008-12-17
I came to that conclusion, too.

Still, I don't want to reinstall. Anyone wanna google it up and see if they have more luck than me?

---

### Post by Bulletbeast on 2008-12-17
Bump.

What about installing a kernel without Synaptic? How is this done?

---

### Post by northern lights on 2008-12-18
> **Bulletbeast said:**
> Bump.

What about installing a kernel without Synaptic? How is this done?
Does *aptitude* or *apt-get* work?
If so, the kernel packages are called linux-image-YYYYYY-2.XX.XX-X, depending on your hardware and the desired version. Intrepid now includes Linux version 2.27, all previous Ubuntu repos include 2.26
Run ```
aptitude search linux-image
``` and pick what suits you (YYYYYY will most likely just be *generic*).

If Synaptic's broken, *apt-get* probably doesn't work either, as it is Synaptic's backend.

If that's the case, check [http://getdeb.net]("http://getdeb.net") for manually downloadable .debs

---

### Post by bgs100 on 2009-01-05
> **jakupl said:**
> well yes. I just did a leap of faith. here you go.
```

jakup@bobby:~$ rm /*
rm: cannot remove `/bin': Is a directory
rm: cannot remove `/boot': Is a directory
rm: cannot remove `/cdrom': Permission denied
rm: cannot remove `/dev': Is a directory
rm: cannot remove `/etc': Is a directory
rm: cannot remove `/home': Is a directory
rm: cannot remove `/initrd': Is a directory
rm: cannot remove `/initrd.img': Permission denied
rm: cannot remove `/initrd.img.old': Permission denied
rm: cannot remove `/lib': Is a directory
rm: cannot remove `/lost+found': Is a directory
rm: cannot remove `/media': Is a directory
rm: cannot remove `/mnt': Is a directory
rm: cannot remove `/opt': Is a directory
rm: cannot remove `/proc': Is a directory
rm: cannot remove `/root': Is a directory
rm: cannot remove `/sbin': Is a directory
rm: cannot remove `/srv': Is a directory
rm: cannot remove `/sys': Is a directory
rm: cannot remove `/tmp': Permission denied
rm: cannot remove `/usr': Is a directory
rm: cannot remove `/var': Is a directory
rm: cannot remove `/vmlinuz': Permission denied
rm: cannot remove `/vmlinuz.old': Permission denied
jakup@bobby:~$ 

```

Holy Crap

---

### Post by jakupl on 2009-01-05
> **bgs100 said:**
> Holy Crap

Well it did not really scare me, because if it would delete anything owned by root, than the problem would be much greater than just me loosing my stuff. The great "permissions" system would be broken for all of us.

---

