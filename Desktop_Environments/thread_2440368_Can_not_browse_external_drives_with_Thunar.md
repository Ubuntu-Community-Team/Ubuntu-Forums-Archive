---
title: "Can not browse external drives with Thunar"
date: 2020-04-09
forum: Desktop Environments
---

### Post by bsh on 2020-04-09
Hi,
on Xubuntu 18.04.4 desktop, whenever I plug in an external USB disk (thumbdrive/pendrive or hard disk or anything), it's icon appears on the desktop and it appears as it was mounted (and it is), but also a "Select which application to use to open this" window pops up (sorry I don't even know what it's officially called, because mine is hungarian), and no matter what I choose (obviously thunar), it does not work. And when I double click the icon on the desktop to open it, the same "Select application" pops up.
The drive gets mounted under /media/username, I can browse that from the command line as root, but not as a normal user, so I think it is somehow a permission issue. Permissions are:
755 root:root /media
750 root:root /media/username
755 username:usergroup /media/username/drivelabel

It doesn't matter if the drive has a single partition or multiple, what filesystems are on it, etc. FAT, ext4, nothing works.

Any help please? Thanks.

---

### Post by ajgreeny on 2020-04-09
With one of those disks attached that has files on it can you please run command ```
sudo ls -la /media/username/label
``` so we can see permissions of files and folders it contains.
Use the proper username and label, of course. 
Also please show the output of command ```
mount
``` 
You ought to be able to both read and write to a disk formatted as fat32 or NTFS, so the more info we can get the better.

---

### Post by bsh on 2020-04-10
Sorry, I'm not going to be around that computer* during the holidays. (Til tuesday)

I've tested with a 8 gig Sandisk (which is also the partition label) freshly formatted FAT3 thumbdrive, with nothing on it, permissions see above.

* IIRC I've seen this exact same behaviour on all of my xubuntu installs, gotta check.

---

### Post by Artim on 2020-04-10
Try opening Thunar as root:

```
sudo thunar
```

---

### Post by ajgreeny on 2020-04-12
> **Artim said:**
> Try opening Thunar as root:

```
sudo thunar
```
No, no, no!!

Please never do that or you may end up with even bigger problems; not being able to login as user is one possible result of starting thunar with sudo.

If you feel you must open thunar as root use "sudo -H thunar" instead.

---

### Post by Artim on 2020-04-12
I stand corrected!  Tell me, please, what is the difference between sudo and sudo -H?

---

### Post by CelticWarrior on 2020-04-12
From man sudo:

```
-H, --set-home
                 Request that the security policy set the HOME environment
                 variable to the home directory specified by the target user's
                 password database entry.  Depending on the policy, this may
                 be the default behavior.
```

---

### Post by The Cog on 2020-04-12
To expand on that: Setting the home directory to root's prevents thunar from placing root-owned files in your directory that you cannot then read. Without that -H precaution, many apps that you run with sudo can create history or configuration files that you as a user cannot read, which prevents you from using the app again without using sudo.

Personally, I use "sudo -i" by habit rather than "sudo -H", but I think that difference is minor.

---

### Post by Morbius1 on 2020-04-12
Unless you are running Ubuntu 20.04:

Ubuntu 18.04

    tester@ub1804:~$ printenv | grep HOME
    HOME=/home/tester
    tester@ub1804:~$ sudo printenv | grep HOME
    [sudo] password for tester:
    HOME=/home/tester

Ubuntu 20.04:

    tester@ub2004:~$ printenv | grep HOME
    HOME=/home/tester
    tester@ub2004:~$ sudo printenv | grep HOME
    [sudo] password for tester:
    HOME=/root

So it will basically default to the -H option to make sure it runs with HOME of the user being invoked ( root in this case ) not the user doing the invoking.

---

### Post by The Cog on 2020-04-13
Ooh! There's interesting. 
I just tried, and it also changes home on 19.10. That's a very good idea. I'll try it on Red Hat tomorrow to see what that does.

---

### Post by ajgreeny on 2020-04-13
> **Morbius1 said:**
> Unless you are running Ubuntu 20.04:

Ubuntu 18.04

    tester@ub1804:~$ printenv | grep HOME
    HOME=/home/tester
    tester@ub1804:~$ sudo printenv | grep HOME
    [sudo] password for tester:
    HOME=/home/tester

Ubuntu 20.04:

    tester@ub2004:~$ printenv | grep HOME
    HOME=/home/tester
    tester@ub2004:~$ sudo printenv | grep HOME
    [sudo] password for tester:
    HOME=/root

So it will basically default to the -H option to make sure it runs with HOME of the user being invoked ( root in this case ) not the user doing the invoking.
So forgive me for asking what to you may seem obvious, but does that mean that using sudo for a GUI application in 20.04, and maybe 19.10, will not, or should not cause the permissions problems that it can potentially in earlier versions of Ubuntu?

That's  how your post reads to me.

---

### Post by Morbius1 on 2020-04-13
You are correct. [The change restores sudo handling of $HOME to what everyone else does]("https://launchpad.net/ubuntu/eoan/+source/sudo/+changelog")

See also: [https://askubuntu.com/questions/1186999/how-does-sudo-handle-home-differently-since-19-10](https://askubuntu.com/questions/1186999/how-does-sudo-handle-home-differently-since-19-10)

---

### Post by DuckHook on 2020-04-13
You've no idea how long I (and presumably the 'buntu world out there) have been waiting/pining for this reversion to sanity. Why on earth was it ever changed in the first place???

---

### Post by bsh on 2020-04-14
ok so after this derail:
i think i solved it. i just deleted everything from /media and let the system recreate the mount folders when a device was connected. it turns out, the username folder under /media had wrong permissions.
media looks like this and it was ok:
drwxr-xr-x   3 root root  4096 ápr   14 13:56 media

the contents of media:
drwxr-xr-x   3 root root 4096 ápr   14 13:56 .
drwxr-xr-x  25 root root 4096 ápr    7 06:27 ..
drwxr-x---+  3 root root 4096 ápr   14 13:56 username
this was 755 before and without the +

and finally the contents of /media/username when a SANDISK drive is connected:
drwxr-x---+ 3 root root 4096 ápr   14 13:56 .
drwxr-xr-x  3 root root 4096 ápr   14 13:56 ..
drwxr-xr-x  2 username username 4096 ápr   14 13:56 SANDISK

this now opens as usual, without the "select application to open this unknown file" thingy, and is read/write.
maybe the /media folder and it's contents were wrong because it may be a remains of older installs.

---

### Post by ajgreeny on 2020-04-14
Great news! 

Please mark as SOLVED from the Thread Tools menu up-top if this really is now solved to your satisfaction. It is a great help to other users searching the forum.

---

