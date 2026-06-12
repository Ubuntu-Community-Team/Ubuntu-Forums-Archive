---
title: "Just a couple of questions"
date: 2009-04-27
forum: General Help
---

### Post by Amused2Death on 2009-04-27
As a long time windows user, and first time serious linux user the last few weeks have been a steep learning curve. So far i have freed myself from windows, installed Ubuntu, updated to jaunty, and mounted a second hdd.
Wine has made it possible for me to still play VGA planets and soon i intend to install vmware so i can still play with other operating systems and possibly games ;)

Now the questions;
I have mounted the 2nd drive and taken ownership from root (thanks to these forums). Is it possible not to have it on my desktop ?

I stuck with gnome after reading an article on 10 reasons why gnome is better than kde. Is it possible to install both and switch between them so i can see the differences and make up my own mind ?

Ubuntu has made the Linux experience pretty awesome, a far cry from the last time i tried with Caldera in 1999. Ease of installation and use has made it possible to look at converting some more people.

These forums have made the task easier, but no doubt i will have more questions as the weeks roll on.

Thanks in advance for any responses.

---

### Post by kpkeerthi on 2009-04-27
> **Amused2Death said:**
> 
I have mounted the 2nd drive and taken ownership from root (thanks to these forums). Is it possible not to have it on my desktop ?

If your is drive is mounted under /media, a desktop shortcut will be automatically created for you. Where is the partition currently mounted? If you are not sure, post the output of ```
mount
``` and highlight the partition(s) you want the shortcuts for.

> 
Is it possible to install both and switch between them so i can see the differences and make up my own mind ?

Yes. Just run this command
```
sudo apt-get update && sudo apt-get install kubuntu-desktop
```
This should get you all kubuntu (KDE) stuffs. You can choose which environment you need from the Login Screen, under Options.

To uninstall, you'd do
```
sudo apt-get purge kubuntu-desktop
```
And the package name for ubuntu (GNOME desktop) is **ubuntu-desktop**

---

### Post by 3Miro on 2009-04-27
It is possible to have both KDE and gnome, however, Ubuntu is not optimized for KDE and many people complain that even Kubuntu is not.

I have been a KDE user for years and I grantee you that if you look around you will find sites with 10 reasons why KDE is better than gnome. This is more of a personal preference question.

You may try to download the kubuntu live cd and take a look at KDE 4.2 for yourself. It will be somewhat limited (running from the CD only), but it will give you an idea.

---

### Post by mb_webguy on 2009-04-27
The /mnt directory is a better place to mount non-dedicated partitions (i.e. partitions that aren't serving a specific purpose like /home or /usr).  Any partition mounted in the /media directory will be treated like removable media, including an icon on the desktop and the ability to unmount it with a click.

As for KDE, yes, you can have both at once.  Kubuntu is Ubuntu is Kubuntu.  The only difference between them are the desktop environmnet used and the default applications.  If you install the kubuntu-desktop package, you'll be able to select the KDE desktop at the login screen by going to Options->Select Session.

---

### Post by Amused2Death on 2009-04-28
result of code: mount

six@The-Witcher:~$ mount
/dev/sdb1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=755)
**/dev/sda1 on /media/sda1 type ext2 (rw)**
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/six/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=six)

I think this is the right bit (bold). What i want is NO desktop icon. Would it be better to redo it with gparted and make it ext3. I am a noob but i gather from what i have read that would just combine the 2 drives into one big one ??

Can it be renamed, 200.0 GB Media seems so impersonal :)

Cheers

ps i'm happy you know what all that means

---

