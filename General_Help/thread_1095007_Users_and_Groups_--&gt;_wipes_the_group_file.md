---
title: "Users and Groups --&gt; wipes the group file"
date: 2009-03-13
forum: General Help
---

### Post by togo59 on 2009-03-13
After spending _months_ sorting out wireless connections and sound-card woes (getting rid of pulseaudio) I have enjoyed about 6 weeks of pure Ubuntu bliss. 

Then all I did was add a new user using the System -> Users and Groups menu. It emptied my group file and my computer failed to boot properly (I was back to [ [COLOR="Blue"]_this_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1017058&highlight=chown%3A+invalid+group") problem). So I copied an old version of the group file and that seemed to do the trick.

Until I logged in.

Now I've lost my wireless connection and GStreamer is gone so all sound has gone and sound apps don't work. (And I wonder what else is screwed up). nm-applet doesn't have the right permissions to automatically configure the network connections.

Why is it that the Users and Groups application is allowed to create such mayhem? If I was fiddling around with bash maybe I could expect such a problem. 

Since this plea for help has to do with groups and permissions not wireless or sound per se, I have posted this here.

Please find help me restore my system if you can! Or just point out what to do next.

Thank you.

---

### Post by jackflap on 2009-03-13
Not sure what I can suggest about restoring your system.

This sounds like a bug in the users and groups dialog.. and should probably be filed in launchpad, but I kinda feel too sorry for you to ask you to do it.

However, in the future once you get everything running sweet and sorted, you may want to consider backing up your setup.

Remastersys is a great tool to do this:

[http://www.remastersys.klikit-linux.com/ubuntu.html](http://www.remastersys.klikit-linux.com/ubuntu.html)

It will create a compressed live cd of your current install as-is, and allow you to 'Install' it as you would a regular ubuntu installation.

It's a great way to roll back in situations like these.

---

### Post by togo59 on 2009-03-13
Thanks Jackflap!

I added my comments to [[COLOR="Blue"]_an already existing bug report._[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/+bug/160862") :(

It seems this is a major bug that the Ubuntu team have chosen to ignore. :(

I've wasted half my life getting my sound card and all the sound apps to work properly and the other half trying to get my wireless card to talk to my router. Obviously I can't get mail and what's worse I have to go back to Windows.

I've spent even more time trying to get my daughter's computer working wirelessly but failed. Ubuntu is great when it works but that's just a small percentage of the time since my first Gutsy download. Flaky or what?

---

### Post by jackflap on 2009-03-13
Wow, such a severe bug and it wasn't even acknowledged..

I do often have to wonder myself at the viability of the open-source development model when things like that happen.

But hardware issues get easier I guess. You end up learning the workarounds that your specific hardware needs, and hardware compatibility does improve by the day. Every release more and more devices work out-the-box. Naturally buying hardware which is known to work with Ubuntu makes a huge difference.

But I feel for you, a stupid bug like that can waste a ton of work. I've done my share of crying myself.. but I just can't bring myself to ditch Ubuntu, I'm a sucker for it really.

Good luck :)

---

### Post by togo59 on 2009-03-13
I wish someone could help me patch things back together. I don't know where to start...

---

### Post by heindsight on 2009-03-13
Well, firstly I feel I have to mention again that it's ALWAYS a good idea to back up important configuration files before changing them. The fact that you're using a GUI tool should not make a difference. Before you change anything related users and groups, BACK UP /etc/passwd, /etc/group and /etc/shadow.

One suggestion I have is to see if you have a /etc/group- file. Some user/group modification tools make a backup of /etc/group in /etc/group-, so if you have that file you may be able to use it to restore your old group file.

---

### Post by togo59 on 2009-03-13
Heindsight! How many times have I wished to go back in time and copy all my critical files -- Ubuntu should definitely have such a warning!

But I can't go back and, because I'm having to use Windows to access the network, I can't tell you what's in group- but I did notice it was nearly empty. I'll post it's contents.

By the way. I notice that I no longer have permission to use "Users and Groups". Common sense on the part of my PC you might say but maybe a clue to why so much else is not working.

sudoers looks AOK BTW and, anyway, I can still sudo this and that.

It seems that the users file has gone the same way as groups... (but I don't know what the "users" file is).

---

### Post by togo59 on 2009-03-13
Just to confirm group- has only three lines in it. group was empty so I backed it up with group~ which had/has about 50 lines but of course that was old.

I am very grateful for your suggestions -- please keep them coming!

I can't even mount the windows drives any more so I can't copy files from Ubuntu over to Windows to post here. No wireless -- no web access; no permissions -- no Windows disk access.

Can't set Users and Groups any more even if I wanted to.

Any ideas why all my permissions have all gone crazy? I'm sure that's the root of all this!

---

### Post by heindsight on 2009-03-13
> **togo59 said:**
> Heindsight! How many times have I wished to go back in time and copy all my critical files -- Ubuntu should definitely have such a warning!

But I can't go back and, because I'm having to use Windows to access the network, I can't tell you what's in group- but I did notice it was nearly empty. I'll post it's contents.

By the way. I notice that I no longer have permission to use "Users and Groups". Common sense on the part of my PC you might say but maybe a clue to why so much else is not working.

sudoers looks AOK BTW and, anyway, I can still sudo this and that.

It seems that the users file has gone the same way as groups... (but I don't know what the "users" file is).
I would expect that if you can still use sudo, you should still be able to use the "Users and Groups" dialog. But if you can't, there are still other ways to try to edit your /etc/group file. It won't be easy to fix though - you'd have to recreate the same groups you had before with the same group ID numbers (otherwise various files will end up belonging to the wrong groups) and you'll have to add yourself (and other system accounts to the correct groups).

The reason you're having so many problems now is that since your /etc/group file was broken, you probably no longer belong to all the correct groups you used to, which means you no longer have permission to access certain files/services that you used to be able to. Also if the old groups file you copied had different GID's for some groups than what they used to be on your machine, then some files will now belong to the wrong group which may prevent them from working as they're supposed to.

You may be able to mostly fix things by looking at the GID's of various files on your machine, then finding out which groups those files should belong to and then creating the appropriate groups in /etc/groups with the correct GIDs. You can do this until you no longer have any files that belong to nonexistent groups (you can use the -nogroup option to the find command to find files that belong to nonexistent groups). It will be very tedious but you should be able to recreate most of the groups on your machine.

There may however have been groups that did not own any files and I'm not sure how you'd go about ensuring that you correctly recreate all those groups. Also, you would still have to somehow (I'm not sure exactly how) figure out exactly which groups to add which users to, to make sure everything works correctly.

In the end, I'm afraid you may have to back up your data and reinstall - it will probably involve a lot less work.

---

### Post by togo59 on 2009-03-13
Oh my god.

Thanks for taking the trouble to go into so much detail. I use Ubuntu as a means to an end, not as an end in itself. I doubt whether I can be bothered any more.

I've been trying to promote Ubuntu and open source in my university but this episode makes me realize that it still has a long way to go before it's fully grown up.

I was a VMS administrator about 15 - 20 years ago; in those days everything just worked. Ubuntu by comparison feels so amateurish;  I've never come across such a badly constructed OS. I've had no end of grief with wireless cards, sound cards etc. What a complete waste of time.

Thanks for taking the trouble.

---

### Post by heindsight on 2009-03-13
> **togo59 said:**
> Just to confirm group- has only three lines in it. group was empty so I backed it up with group~ which had/has about 50 lines but of course that was old.

I am very grateful for your suggestions -- please keep them coming!

I can't even mount the windows drives any more so I can't copy files from Ubuntu over to Windows to post here. No wireless -- no web access; no permissions -- no Windows disk access.

Can't set Users and Groups any more even if I wanted to.

Any ideas why all my permissions have all gone crazy? I'm sure that's the root of all this!

Sorry, I missed this post of yours. If this group~ file is from the same install of Ubuntu, then things might not be quite as bad as I thought (I was working on the assumption that you had no backup of your old group file to use as a starting point). Depending on how old this group~ file is you may not have all that much work to do to fix things. It will still be tedious work though...

---

### Post by togo59 on 2009-03-13
Just for clarity:

1) My original group file got wiped by Users and Groups. I couldn't even boot up properly (see first post)

2) After I did a rescue boot, I found that I had a group~ file with about 50 or so lines. It looked OK so I renamed the two files:
sudo mv /etc/group /etc/group_corrupt
sudo mv /etc/group~ /etc/group

Now at least I can boot the dam thing. I didn't chmod anything.

3) I login to find no wireless, no sound and everything screwed up. The sound can be heard *before* I login (that ol' Ubuntu trick again).

(What started it? I wanted to create an extra account on my computer. I just added a user.)

---

### Post by heindsight on 2009-03-13
Well, depending on how much changes you've made to the system (especially changes that may have affected the groups you have or group membership of users) it might not be that hard to fix your group file then.
If you want to check how old the file is, you should be able to find out by using:
```
ls -lt /etc/group
```

As a first step, I'd recommend comparing the /etc/passwd and /etc/group files. Make sure that the primary group for each user in /etc/passwd is listed in /etc/group (with a few exceptions, most users' primary group has the same name as the login name). If there are any user accounts whose primary groups are not listed in /etc/group you could try posting here and I or others could see what those groups are called on our machines, to help you add them back to your group file.

That should bring you some of the way towards restoring your system. The next step would be to look for files whose GID's aren't listed in /etc/group. That can be done by doing:
```
sudo find / -nogroup -printf "%G %p\n"
```
If you post that list here, again I and others should be able to tell you the names of the groups those files should belong to and you can add those groups to your group file.

After that you should only need to add yourself (and perhaps other users) to the appropriate groups. If you need help with that, you could post your group file here and we can try to help you work out who should belong to which group.

That should restore your group file to a usable state - and hopefully that's all you'll need to get things working again.

---

### Post by togo59 on 2009-03-16
Thanks again for your kind efforts on my behalf.

Unfortunately, I can't mount any external drive to copy my files to (including my windows partition and my pen drive) - it says something like: the specified device doesn't exist in fstab or mtab.

And I can't use either my wired or my wireless networks from Ubuntu. (I'm writing this from Windows, which is working perfectly on both). So I can't send you the files you asked for. (ifconfig says that eth0 and wlan0 are OK and I know the wired network is communicating as the lights on the router flash and in Network Config, it says packets are being sent to and fro). So it's a permissions/groups screw up.

What I can say is there is a GID mismatch between passwd and group. I noticed in passwd that the new user I added had a zero in place of a number e.g. 
fred.x.1001.0:Fred,,, etc whereas all the others looked like
tom.x.1000.65534:Tom,,, I changed the zero to 65534 but no effect.

```
ls -lt /etc/group
```
Produces 2008/12/21, which was back when I had wireless comms OK but I hadn't realised pulseaudio was screwing up my sound. I later uninstalled pulseaudio, which cured the problem. pulseAudio is still be referenced in the group file of course.

```
sudo find / -nogroup -printf "%G %p\n"
```
produced just the following:
```
find:'/proc/5628/task/5628/fd/5': No such file or directory
find:'/proc/5628/task/5628/fd/5': No such file or directory
find:'/proc/5628/task/5628/fdinfo/5': No such file or directory
find:'/proc/5628/fd/5': No such file or directory
find:'/proc/5628/fdinfo/5': No such file or directory
```

I cannot use System -> "Users and Groups" anymore, as it tells me I don't have the privilege. But (obviously) I can use sudo

I notice that the computer name seems to have changed but I could be imagining this. E.g.
at a terminal I get: roger@localhost:~$ as a prompt
if I boot up using repair, I get: root@rubi~# as a prompt.

I thought I used to get the computer's name "rubi" at the prompt in the terminal window.

This is so screwed up I think I may have to reinstall. If I do reinstall I'll have to back up my work and my mail folders (dam myself for using pop -- I have no copy on the server). But I'll need to mount a drive somehow in order to make them safe. But mount doesn't seem to work! :(

If I do ```
mount -l
```
I can see basically what's in /etc/mtab.

If I go to the directory /dev/disk/by-label/ I can see a drive label for a Windows NTFS drive that's supposed to be mountable from Ubuntu. There's a UUID reference in mtab that's the same as one in /dev/disk/by-UUID/ but I don't know how the two relate to one another. I.e. how do I know which disk the UUID refers to?

In the Places menu (main Ubuntu GUI), I can see the drive I want to mount. If I plug in my USB drive, this appears in the list too. Curiously both fstab and mtab don't use device labels so I can't tell what's referencing what. As I said in para 1 above, mount just returns an error.

---

### Post by heindsight on 2009-03-16
> **togo59 said:**
> 
What I can say is there is a GID mismatch between passwd and group. I noticed in passwd that the new user I added had a zero in place of a number e.g. 
fred.x.1001.0:Fred,,, etc whereas all the others looked like
tom.x.1000.65534:Tom,,, I changed the zero to 65534 but no effect.


I suspect that's a large part of your problem right there. 0 is the GID of root's group and 65534 is the GID of the nogroup group. No normal user should belong to root's group and having nogroup as a primary group doesn't help much either. The default in Ubuntu is for normal users to have the same GID as their UID, and that GID is associated with a group of the same name as the user.

Try changing those lines in /etc/passwd to:
```

fred:x:1001:1001:Fred,,,:/home/fred:/bin/bash
tom:x:1000:1000:Tom,,,:/home/tom:/bin/bash

```
(note that fields in /etc/passwd and /etc/group must be separated by : colons not . dots) and make sure that /etc/group contains lines like:
```
fred:x:10001:
tom:x:1000:

```

> **togo59 said:**
> 
```
ls -lt /etc/group
```
Produces 2008/12/21, which was back when I had wireless comms OK but I hadn't realised pulseaudio was screwing up my sound. I later uninstalled pulseaudio, which cured the problem. pulseAudio is still be referenced in the group file of course.

For now I think just leave the references to pulseAudio in the group file - it shouldn't break anything. Once you've got things back to normal you can think about removing it.

> **togo59 said:**
> 
```
sudo find / -nogroup -printf "%G %p\n"
```
produced just the following:
```
find:'/proc/5628/task/5628/fd/5': No such file or directory
find:'/proc/5628/task/5628/fd/5': No such file or directory
find:'/proc/5628/task/5628/fdinfo/5': No such file or directory
find:'/proc/5628/fd/5': No such file or directory
find:'/proc/5628/fdinfo/5': No such file or directory
```


OK, that means that you don't have any files that belong to groups that have been removed from /etc/group. That's a good start. It means that appart from the changes I suggested above, you probably only need to make sure that you belong to all same groups as before and you'll be ok.

It would be usefull if you could run the command:
```
id
```and post the output here. That will give a summary of which groups you belong to.

> **togo59 said:**
> 
I cannot use System -> "Users and Groups" anymore, as it tells me I don't have the privilege. But (obviously) I can use sudo

I suspect that may be because your GID is wrong, but I'm not sure.

> **togo59 said:**
> 
I notice that the computer name seems to have changed but I could be imagining this. E.g.
at a terminal I get: roger@localhost:~$ as a prompt
if I boot up using repair, I get: root@rubi~# as a prompt.

I thought I used to get the computer's name "rubi" at the prompt in the terminal window.


That is rather strange. If your hostname is "rubi" then you should indeed see the name as rubi in your prompt. I'm not sure why it would show it as localhost.

> **togo59 said:**
> 
This is so screwed up I think I may have to reinstall. If I do reinstall I'll have to back up my work and my mail folders (dam myself for using pop -- I have no copy on the server). But I'll need to mount a drive somehow in order to make them safe. But mount doesn't seem to work! :(

If I do ```
mount -l
```
I can see basically what's in /etc/mtab.

If I go to the directory /dev/disk/by-label/ I can see a drive label for a Windows NTFS drive that's supposed to be mountable from Ubuntu. There's a UUID reference in mtab that's the same as one in /dev/disk/by-UUID/ but I don't know how the two relate to one another. I.e. how do I know which disk the UUID refers to?

In the Places menu (main Ubuntu GUI), I can see the drive I want to mount. If I plug in my USB drive, this appears in the list too. Curiously both fstab and mtab don't use device labels so I can't tell what's referencing what. As I said in para 1 above, mount just returns an error.

The files in /dev/disk/by-label etc are symbolic links to the /dev/sdXX files. So you can just use ```
ls -l
``` to find out which labels/UUIDs correspond to which devices. Perhaps easier though, is to use the blkid command:
```
sudo blkid
```Should list all your partitions on all disks with their UUIDs and labels.

I suspect your inability to mount has to do with insufficient permissions either because your GID is wrong, or because you've lost membership of some group that you need to be a member of to mount.

You can try to mount things manually though, by doing something like:
```
sudo mount -t TYPE /dev/sdXX /mount/point
```
Of course you'll have to substitute correct values for TYPE, SDXX and /mount/point.

---

### Post by togo59 on 2009-03-16
Progress! 
Before I entered the correct GID I got, in response to ```
sudo blkid
```
was...
```
 
uid=1000(roger) gid=65534(nogroup)
groups=4(adm), 20(dialout), 24(Cdrom), 46(plugins), 108(lpadmin),
123(admin), 124(sambashare), 65534(nogroup)
```
Now this has been changed to give gid=1000(Roger) above.

With the right GID I was able to mount the drive at the command prompt but not from the "Places" menu. Here is the contents of my group file:
```
root:x:0:
daemon:x:1:
bin:x:2:
sys:x:3:
adm:x:4:roger
tty:x:5:
disk:x:6:
lp:x:7:
mail:x:8:
news:x:9:
uucp:x:10:
man:x:12:
proxy:x:13:
kmem:x:15:
dialout:x:20:roger
fax:x:21:
voice:x:22:
cdrom:x:24:roger
floppy:x:25:
tape:x:26:
sudo:x:27:
audio:x:29:pulse
dip:x:30:
www-data:x:33:
backup:x:34:
operator:x:37:
list:x:38:
irc:x:39:
src:x:40:
gnats:x:41:
shadow:x:42:
utmp:x:43:
video:x:44:
sasl:x:45:
plugdev:x:46:roger
staff:x:50:
games:x:60:
users:x:100:
nogroup:x:65534:
libuuid:x:101:
syslog:x:102:
klog:x:103:
scanner:x:104:
nvram:x:105:
fuse:x:106:
ssl-cert:x:107:
lpadmin:x:108:roger
crontab:x:109:
mlocate:x:110:
ssh:x:111:
avahi-autoipd:x:112:
gdm:x:113:
netdev:x:114:
pulse:x:115:
pulse-access:x:116:
pulse-rt:x:117:
saned:x:118:
messagebus:x:119:
polkituser:x:120:
avahi:x:121:
haldaemon:x:122:
admin:x:123:roger
roger:x:1000:
peter:x:1001:
sambashare:x:124:roger

```
Here is the passwd file:
```
root:x:0:65534:root:/root:/bin/bash
daemon:x:1:65534:daemon:/usr/sbin:/bin/sh
bin:x:2:65534:bin:/bin:/bin/sh
sys:x:3:65534:sys:/dev:/bin/sh
sync:x:4:65534:sync:/bin:/bin/sync
games:x:5:65534:games:/usr/games:/bin/sh
man:x:6:65534:man:/var/cache/man:/bin/sh
lp:x:7:65534:lp:/var/spool/lpd:/bin/sh
mail:x:8:65534:mail:/var/mail:/bin/sh
news:x:9:65534:news:/var/spool/news:/bin/sh
uucp:x:10:65534:uucp:/var/spool/uucp:/bin/sh
proxy:x:13:65534:proxy:/bin:/bin/sh
www-data:x:33:65534:www-data:/var/www:/bin/sh
backup:x:34:65534:backup:/var/backups:/bin/sh
list:x:38:65534:Mailing List Manager:/var/list:/bin/sh
irc:x:39:65534:ircd:/var/run/ircd:/bin/sh
gnats:x:41:65534:Gnats Bug-Reporting System (admin):/var/lib/gnats:/bin/sh
nobody:x:65534:65534:nobody:/nonexistent:/bin/sh
libuuid:x:100:65534::/var/lib/libuuid:/bin/sh
syslog:x:101:65534::/home/syslog:/bin/false
klog:x:102:65534::/home/klog:/bin/false
hplip:x:103:65534:HPLIP system user,,,:/var/run/hplip:/bin/false
avahi-autoipd:x:104:65534:Avahi autoip daemon,,,:/var/lib/avahi-autoipd:/bin/false
gdm:x:105:65534:Gnome Display Manager:/var/lib/gdm:/bin/false
pulse:x:106:65534:PulseAudio daemon,,,:/var/run/pulse:/bin/false
saned:x:107:65534::/home/saned:/bin/false
messagebus:x:108:65534::/var/run/dbus:/bin/false
polkituser:x:109:65534:PolicyKit,,,:/var/run/PolicyKit:/bin/false
avahi:x:110:65534:Avahi mDNS daemon,,,:/var/run/avahi-daemon:/bin/false
haldaemon:x:111:65534:Hardware abstraction layer,,,:/var/run/hald:/bin/false
roger:x:1000:1000:Roger,,,:/home/roger:/bin/bash
peter:x:1001:1001:Peter,,,,:/home/peter:/bin/bash

```
They seem to agree up to group 3. Then they diverge until group 7 and then it's a bit hit and miss. Do I work from the passwd file and remove all groups not referenced by it? Seems a bit drastic but the group file contains the most out-of-date info.

Here is the result of sudo blkid:
```
roger@localhost:~$ sudo blkid
[sudo] password for roger: 
/dev/sdb1: UUID="3a8d62b2-b096-4b20-b71c-741e64fb989c" TYPE="ext3" 
/dev/sda1: UUID="D214875E14874507" LABEL="Big" TYPE="ntfs" 
/dev/sdc1: UUID="927C62E47C62C299" LABEL="Big" TYPE="ntfs" 
/dev/sdb5: TYPE="swap" UUID="52bb3478-d6db-49cf-aa51-7f4c3cf65cbe" 

```
Note there are two disks with the same label. In the "Places" menu, these disks are listed with their correct labels (but I can't use the menu to mount the disks). However, I mounted the first "Big" disk only to find it wasn't the correct one. Weird.

My set up is Windows on an 80Gb disk, Ubuntu on a separate 200Gb disk and a third disk called "Big" because it's 500Gb to hold stuff like music and video, shared between Windows and Ubuntu. But /dev/sda1 is actually my 80Gb disk; /dev/sdc1 is my 500Gb disk.

Even with the correct GID, I don't seem to be able to do much.

---

### Post by heindsight on 2009-03-16
> **togo59 said:**
> Progress! 
Before I entered the correct GID I got, in response to ```
sudo blkid
```
was...
```
 
uid=1000(roger) gid=65534(nogroup)
groups=4(adm), 20(dialout), 24(Cdrom), 46(plugins), 108(lpadmin),
123(admin), 124(sambashare), 65534(nogroup)
```
Now this has been changed to give gid=1000(Roger) above.

With the right GID I was able to mount the drive at the command prompt but not from the "Places" menu. Here is the contents of my group file:
```
root:x:0:
daemon:x:1:
bin:x:2:
sys:x:3:
adm:x:4:roger
tty:x:5:
disk:x:6:
lp:x:7:
mail:x:8:
news:x:9:
uucp:x:10:
man:x:12:
proxy:x:13:
kmem:x:15:
dialout:x:20:roger
fax:x:21:
voice:x:22:
cdrom:x:24:roger
floppy:x:25:
tape:x:26:
sudo:x:27:
audio:x:29:pulse
dip:x:30:
www-data:x:33:
backup:x:34:
operator:x:37:
list:x:38:
irc:x:39:
src:x:40:
gnats:x:41:
shadow:x:42:
utmp:x:43:
video:x:44:
sasl:x:45:
plugdev:x:46:roger
staff:x:50:
games:x:60:
users:x:100:
nogroup:x:65534:
libuuid:x:101:
syslog:x:102:
klog:x:103:
scanner:x:104:
nvram:x:105:
fuse:x:106:
ssl-cert:x:107:
lpadmin:x:108:roger
crontab:x:109:
mlocate:x:110:
ssh:x:111:
avahi-autoipd:x:112:
gdm:x:113:
netdev:x:114:
pulse:x:115:
pulse-access:x:116:
pulse-rt:x:117:
saned:x:118:
messagebus:x:119:
polkituser:x:120:
avahi:x:121:
haldaemon:x:122:
admin:x:123:roger
roger:x:1000:
peter:x:1001:
sambashare:x:124:roger

```
Here is the passwd file:
```
root:x:0:65534:root:/root:/bin/bash
daemon:x:1:65534:daemon:/usr/sbin:/bin/sh
bin:x:2:65534:bin:/bin:/bin/sh
sys:x:3:65534:sys:/dev:/bin/sh
sync:x:4:65534:sync:/bin:/bin/sync
games:x:5:65534:games:/usr/games:/bin/sh
man:x:6:65534:man:/var/cache/man:/bin/sh
lp:x:7:65534:lp:/var/spool/lpd:/bin/sh
mail:x:8:65534:mail:/var/mail:/bin/sh
news:x:9:65534:news:/var/spool/news:/bin/sh
uucp:x:10:65534:uucp:/var/spool/uucp:/bin/sh
proxy:x:13:65534:proxy:/bin:/bin/sh
www-data:x:33:65534:www-data:/var/www:/bin/sh
backup:x:34:65534:backup:/var/backups:/bin/sh
list:x:38:65534:Mailing List Manager:/var/list:/bin/sh
irc:x:39:65534:ircd:/var/run/ircd:/bin/sh
gnats:x:41:65534:Gnats Bug-Reporting System (admin):/var/lib/gnats:/bin/sh
nobody:x:65534:65534:nobody:/nonexistent:/bin/sh
libuuid:x:100:65534::/var/lib/libuuid:/bin/sh
syslog:x:101:65534::/home/syslog:/bin/false
klog:x:102:65534::/home/klog:/bin/false
hplip:x:103:65534:HPLIP system user,,,:/var/run/hplip:/bin/false
avahi-autoipd:x:104:65534:Avahi autoip daemon,,,:/var/lib/avahi-autoipd:/bin/false
gdm:x:105:65534:Gnome Display Manager:/var/lib/gdm:/bin/false
pulse:x:106:65534:PulseAudio daemon,,,:/var/run/pulse:/bin/false
saned:x:107:65534::/home/saned:/bin/false
messagebus:x:108:65534::/var/run/dbus:/bin/false
polkituser:x:109:65534:PolicyKit,,,:/var/run/PolicyKit:/bin/false
avahi:x:110:65534:Avahi mDNS daemon,,,:/var/run/avahi-daemon:/bin/false
haldaemon:x:111:65534:Hardware abstraction layer,,,:/var/run/hald:/bin/false
roger:x:1000:1000:Roger,,,:/home/roger:/bin/bash
peter:x:1001:1001:Peter,,,,:/home/peter:/bin/bash

```
They seem to agree up to group 3. Then they diverge until group 7 and then it's a bit hit and miss. Do I work from the passwd file and remove all groups not referenced by it? Seems a bit drastic but the group file contains the most out-of-date info.


That looks good. Don't delete the groups that aren't referenced in passwd. The groups mentioned in passwd are just the primary group for each account, you still need the other groups. As long as all the groups listed in passwd actually exist, you're fine. I think at this stage all you need to do is add yourself to all the right groups.

Looking at the groups I belong to on my machine, I'd recommend you add yourself to at least the following groups:
fuse, audio, video, scanner, fax, dip, floppy

Apart from that, your group file looks fine to me. The only group woth mentioning that I have on my Hardy install that is not listed in your group file is a group called dhcp. Try doing:
```
ls -l /lib/dhcp3-client/call-dhclient-script
```
and see what group that file belongs to.

> **togo59 said:**
> 
Here is the result of sudo blkid:
```
roger@localhost:~$ sudo blkid
[sudo] password for roger: 
/dev/sdb1: UUID="3a8d62b2-b096-4b20-b71c-741e64fb989c" TYPE="ext3" 
/dev/sda1: UUID="D214875E14874507" LABEL="Big" TYPE="ntfs" 
/dev/sdc1: UUID="927C62E47C62C299" LABEL="Big" TYPE="ntfs" 
/dev/sdb5: TYPE="swap" UUID="52bb3478-d6db-49cf-aa51-7f4c3cf65cbe" 

```
Note there are two disks with the same label. In the "Places" menu, these disks are listed with their correct labels (but I can't use the menu to mount the disks). However, I mounted the first "Big" disk only to find it wasn't the correct one. Weird.

My set up is Windows on an 80Gb disk, Ubuntu on a separate 200Gb disk and a third disk called "Big" because it's 500Gb to hold stuff like music and video, shared between Windows and Ubuntu. But /dev/sda1 is actually my 80Gb disk; /dev/sdc1 is my 500Gb disk.

Even with the correct GID, I don't seem to be able to do much.

Well, there's no rule that says that the LABEL of a filesystem has to be unique, athough I'm not quite sure what happens when you get two filesystems with the same label.

I suspect the reason you couldn't mount those filesystems is because they're ntfs filesystems, which are mounted by ntfs-3g, which uses fuse and you aren't a member of the fuse group.

---

### Post by togo59 on 2009-03-16
Many thanks for all your help! :KS

I've got a busy 24hours ahead of me so I won't be able to get back to you about progress until late tomorrow evening.

- Roger

---

### Post by togo59 on 2009-03-23
Fixed it.

It was all those 65534's in the passwd file.

Thanks for all your help. 8)

---

### Post by Zill on 2009-03-23
togo59:  Congratulations on fixing the problem.

I believe the corruption of /etc/passwd and /etc/group when using the Users and Groups GUI may be related to [Bug #240437]("https://bugs.launchpad.net/ubuntu/+source/liboobs/+bug/240437").

Although this bug was raised against Xubuntu and a slow AMD-K6 processor, it seems to be quite a widespread problem with the users-admin tool.  The workaround is to edit the two config files manually, rather than use the GUI, until this problem is fixed.

I know this advice is a bit late for you but hopefully you found the learning experience of repairing your system "interesting". ;-)

---

