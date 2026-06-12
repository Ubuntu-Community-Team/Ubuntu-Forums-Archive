---
title: "Folder/mount permissions"
date: 2010-10-19
forum: Desktop Environments
---

### Post by Data 1 on 2010-10-19
Hi,

Been using Ubuntu/gnome for months now, have it set up with multiple profiles similar to how you would do a windoze system.

I was trying it out and liked it so much I cloned it to a 500G hard drive. For some reason I couldn't get the partitons to stretch to the end of the HD with gparted so I created a ext4 partition (almost 400G) and mount it user,rw in fstab.

How do I set the permissions or mount differently so I can read and write or my wife can read or write each others folders? Not a real big deal but when she stores pictures and I store pictures she can't see mine and I can't see hers.

Jim

---

### Post by oldfred on 2010-10-19
I do not know much about multiuser (I just boot and my wife uses the computer). But I saved this info:

Two users to share music folder - group & permissions -BoneKracker:
[http://ubuntuforums.org/showthread.php?t=1484221](http://ubuntuforums.org/showthread.php?t=1484221)
[http://ubuntuforums.org/showthread.php?t=1488065](http://ubuntuforums.org/showthread.php?t=1488065)
See lucky's post on network based shares & setting permissions commands
[http://ubuntuforums.org/showthread.php?t=1498422](http://ubuntuforums.org/showthread.php?t=1498422)

The 2 at the beginning makes the directory SGID (Set Group ID). That means any files in the directory automatically will inherit the group of the folder, as opposed to the group of the user putting the file there.

mv ~/music /home
chown root:music /home/music
chmod 2774 /home/music  or 3774

would not recommend using the /media folder.

Group File, Directory and Device permissions: chmod
[http://www.yolinux.com/TUTORIALS/LinuxTutorialManagingGroups.html](http://www.yolinux.com/TUTORIALS/LinuxTutorialManagingGroups.html)

---

### Post by sisco311 on 2010-10-19
Neither the [Unix/Linux file permission]("http://content.hccfl.edu/pollock/aunix1/filepermissions.htm") mechanism nor the Linux [ACL]("https://help.ubuntu.com/community/UbuntuLTSP/ACLSupport") implementation allows you to force the owner/group and permissions for all files created/moved/copied in/to a specific directory.

But you could use bindfs to remount the directory and all files (sub-directories are files too [noparse]:)[/noparse]) in it with read and write permissions for a group or list of users.

See:
[thread=1460472]HowTo: Create a shared directory for local users (with bindfs).[/thread]

---

### Post by Data 1 on 2010-10-19
Wow quick reply is too difficult to be quick in vbull.

Anyhow thank you both for the speedy reply, I will be reading all the articles to see which methods might best fit my needs.

It kinda looks like the bindfs is right up my alley being I am the geeky type :)

Thank you again, I'll post what I did and the results.

Jim

---

### Post by Data 1 on 2010-10-19
Hi again,

Since it is an entire partition I used the workarounds at the end of the first post. When I reboot it says unable to mount and always gives the directory listed second in the bindfs line.

Do I have to "start" the service bindfs or is it on demand? I attempted a reinstall and it said it was installed.

Here is the fstab lines but the result was the same with both workaround examples:

```
/dev/sda3       /storage2    ext4    user,rw           0       2
bindfs#/storage2      /storage     fuse      perms=0700,mirror-only=jim:Di          0    0
```

The partition mounts as /storage2 in this example after skipping the bad mount warning upon boot that says it couldn't mount /storage

I'm sure I made a simple mistake.

Just a note, the tut says gksu gedit /etc/fsatb instead of fstab. I'm notorious for copying and pasting. :)

---

### Post by sisco311 on 2010-10-20
Yep that workaround no longer works. bindfs is affected by [this bug]("https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/503003") too.

As a workaround remove the bindfs fstab entry and create an Upstart job:
```
gksu gedit /etc/init/mount-bindfs.conf
```with the following content:
```
# Remount directories with bindfs
#
# Temporary workaround until BUG 503003 is fixed
#

description "Remount directories with different permissions"

start on stopped mountall 

script
  bindfs -o perms=0700,mirror-only=jim,Di /storage /storage
end script

```Also, instead of /dev/sdXY you should use UUIDs in fstab. [uhelp]community/UsingUUID[/uhelp]

And since 8.04 Ubuntu defaults to the "relatime" mount option. See: [http://lwn.net/Articles/244829/](http://lwn.net/Articles/244829/) and [thread=283131]How to fstab[/thread]


> **Data 1 said:**
> Just a note, the tut says gksu gedit /etc/fsatb instead of fstab. I'm notorious for copying and pasting. :smile:

Thanks. Fixed. 

I will try to update the howto with the new workaround a little bit later.

---

### Post by Data 1 on 2010-10-20
Cool thanks, I'll do it tonight when I get home and report.

I knew the UUID thing but I noticed all the other native mounts in fstab were using the /dev method.

Should I change those to UUID also?

Thank you again, I'll mark this as solved the minute I try it out.

ALSO I'm still using 10.04, was that workaround for the workaround specifically for 10.10 or will it fly with 10.04?

Jim

---

### Post by sisco311 on 2010-10-20
> **Data 1 said:**
> Cool thanks, I'll do it tonight when I get home and report.

I knew the UUID thing but I noticed all the other native mounts in fstab were using the /dev method.

Should I change those to UUID also?


Yes. Don't forget to backup the file first.

> **Data 1 said:**
> 
Thank you again, I'll mark this as solved the minute I try it out.

ALSO I'm still using 10.04, was that workaround for the workaround specifically for 10.10 or will it fly with 10.04?

Jim

I tested it on Natty Narwhal, but it should work with any release newer than 9.04. In 9.04 and earlier releases the fstab entry should do the trick.

---

### Post by Data 1 on 2010-10-22
Hi again,

I must be missing one of the fundamentals of the mod.

I changed everything in fstab to UUID and it worked just fine.

I went back to the original tut ( [http://ubuntuforums.org/showthread.php?t=1460472](http://ubuntuforums.org/showthread.php?t=1460472) ) and made sure everything was as it had stated.

This is not a "critical" issue simply curiosity for a method.

I created the upstart file in the location specified.

I even tried EXACTLY as in the first tut using /home/shared and upstart..... neither user can open the directory.

It's like bindfs itself is not working.

Here is fstab: 
```
proc            /proc           proc    nodev,noexec,nosuid 0       0
UUID=1731f0c4-0590-4c85-8685-c293eef3b7cc       /               ext4    errors=remount-ro 0       1
UUID=298ab20b-59a5-4478-8434-bdf11154d71f       /storage    ext4    user,rw           0       2
UUID=97b374c1-a826-4db8-bf08-5b15695957fa       none            swap    sw                0       0

```

Here is the upstart /etc/init/mount-bindfs.conf:

```
# Remount directories with bindfs
#
# Temporary workaround until BUG 503003 is fixed
#

description "Remount directories with different permissions"

start on stopped mountall 

script
  bindfs -o perms=0700,mirror-only=jim,Di /storage /storage
end script
```

Very interesting.

---

