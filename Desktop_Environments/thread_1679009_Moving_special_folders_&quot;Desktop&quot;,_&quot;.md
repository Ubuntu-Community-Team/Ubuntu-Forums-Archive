---
title: "Moving special folders &quot;Desktop&quot;, &quot;Downloads&quot; and &quot;Pictures&quot;"
date: 2011-01-31
forum: Desktop Environments
---

### Post by cdysthe on 2011-01-31
Hi,

I would like to permanently move the special folders "Desktop", "Pictures" and "Downloads" into the "Documents" folder. Currently they are stored in their default location in my home directory. Can I just drag them there and my system will still work like normal, or do I have to do this with gconf or something like that?

I'm running Ubuntu with stock Gnome desktop.

---

### Post by vanadium on 2011-01-31
I am not sure, but I guess if you do the move with nautilus, they should remain "special".

If they do not remain "special", then edit ~/.config/user-dirs.dirs and update the paths to reflect their new location.

---

### Post by Chuckaluphagus on 2011-06-10
vanadium, thank you for posting that.  Very helpful, it showed up as the very first Google hit when I was looking to answer the exact same question.

---

### Post by LifeBringer on 2011-08-19
What about moving them to a separate NTFS internal HDD? Is there a way to automount the drive on start?

---

### Post by cbowman57 on 2011-08-19
Just put it in your fstab.  Here's a link to one example, there are plenty more on the web: [http://cazatech.wordpress.com/2007/10/03/adding-a-ntfs-partition-to-fstab/](http://cazatech.wordpress.com/2007/10/03/adding-a-ntfs-partition-to-fstab/)

---

### Post by LifeBringer on 2011-08-19
UPDATE 2: Thanks to Mobius1 I have updated this HOW TO with a fixed solution. Ubuntu One now syncs smoothly.

Update 1: (obsolete)
Success! The only issue remaining is having the folders show up in the home folder, hard linked, instead of the /mnt/<folder name> perhaps /home/* in fstab? Drat Ubuntu One doesn't want to play nice either. :-P

**[HOW TO] Moving special folders Desktop, Downloads, Pictures, et al. - 11.04**

Start by fixing up that target partition through gparted, once ready, go ahead and open the terminal and:

> sudo blkid

Determine the UUID, e.g. xxxx, and type, e.g. ext4 or ntfs, of the desired partition and take note. Then we'll create the target directory:

> sudo mkdir /mnt/folder_name

We chose mnt instead of media so that the drive doesn't show up on the desktop. Now, we'll edit fstab (order is critical) to mount the partition into <folder_name>.

> sudo <text editor, e.g. gedit> /etc/fstab

Now edit something like:

> ...
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=e7f3-d5e1-4ad9 /               ext4    noatime,nodiratime,errors=remount-ro 0       1

So that **UUID=XXXX   /mnt/folder_name    <type>          defaults,uid=1000       0       0** loads before the sda partition (otherwise you'll see a mounting error on boot).

*Note that folder_name is the same directory throughout.*

Here's what mine looks like:
> ...
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
**UUID=6ABE4ECA0D   /mnt/HOMEBASE    [COLOR="rgb(65, 105, 225)"]ntfs[/COLOR]          [COLOR="RoyalBlue"]noauto[/COLOR],defaults,locale-en.UTF-8,uid=1000,umask=000       0       0**
# / was on /dev/sda1 during installation
UUID=e7f3-d5e1-4ad9 /               ext4    noatime,nodiratime,errors=remount-ro 0       1
[COLOR="rgb(65, 105, 225)"]*Using an ntfs partition requires an extra special step with rc.local or Upstart to work.*[/COLOR]

Save, close the editor, and then reboot. So far so good.

Now it's time to transfer your files to your destination partition or drive. You can either use nautilus to copy your folders from /home/. to /mnt/folder_name/. and empty the old folders. Or, if you're lazy open the terminal and enter:

> sudo rsync -axS ~/Desktop /mnt/folder_name/Desktop && sudo rsync -axS ~/Documents /mnt/folder_name/Documents && sudo rsync -axS ~/Downloads /mnt/folder_name/Downloads && sudo rsync -axS ~/Pictures /mnt/folder_name/Pictures && sudo rsync -axS ~/Music /mnt/folder_name/Music && sudo rsync -axS ~/Videos /mnt/folder_name/Videos
Now empty the original folders.

Final step, before reboot:

Head on over to Mobius1's [post]("http://ubuntuforums.org/showpost.php?p=11151879&postcount=6") and either edit /etc/rc.local or create and Upstart job* (preferred).


Reboot and voila, to reverse just undo either rc.local or Upstart method, reboot, then copy back your data files**, remove the fstab entry, reboot.

*I.E.
> sudo <text editor, e.g. gedit> /etc/init/home-mounts.conf
Example of what to enter:
> # Remount partitions with bind
# description "Bind Data Subdirectories to Morbius' Home Directory"

start on stopped mountall

script
[COLOR="rgb(65, 105, 225)"]mount /dev/sdbxx /mnt/HOMEBASE[/COLOR]
mount --bind /mnt/HOMEBASE/Documents /home/lifebringer/Documents
mount --bind /mnt/HOMEBASE/Downloads /home/lifebringer/Downloads
mount --bind /mnt/HOMEBASE/Music /home/lifebringer/Music
mount --bind /mnt/HOMEBASE/Videos /home/lifebringer/Videos
mount --bind /mnt/HOMEBASE/Pictures /home/lifebringer/Pictures
end script
Source [http://ubuntuforums.org/showpost.php?p=11151879&postcount=6](http://ubuntuforums.org/showpost.php?p=11151879&postcount=6)

**Here's the reverse:
> sudo rsync -axS /mnt/folder_name/Desktop ~/Desktop && sudo rsync -axS /mnt/folder_name/Documents ~/Documents && sudo rsync -axS /mnt/folder_name/Downloads ~/Downloads && sudo rsync -axS /mnt/folder_name/Pictures ~/Pictures && sudo rsync -axS /mnt/folder_name/Music ~/Music && sudo rsync -axS /mnt/folder_name/Videos ~/Videos

---

### Post by vanadium on 2011-08-19
> **LifeBringer said:**
> Success! The only issue remaining is having the folders show up in the home folder, hard linked, instead of the /mnt/<folder name> perhaps /home/* in fstab? Drat Ubuntu One doesn't want to play nice either. :-P

I do not think that this could be directly achieved in a space efficient way: it would require that you have a separate partition for each "special" folder, which is mounted on /home/Documents/Movies, /home/Documents/Music, ... etc.

Soft linking would be the only efficient way. In fact, the only drawback of that approach is that you "loose" the custom folder icons for the special folders. For the rest, it works perfectly. However, it is possible to manually assign custom icons to folders, so this little issue could be overcome.

---

### Post by Morbius1 on 2011-08-19
Another alternative is bind which will preserve the icons in your home directory.

* Make sure the ntfs partition is mounted first, for example:
```
UUID=6ABE4ECA0D /mnt/HOMEBASE ntfs defaults,nls=utf8,uid=1000,umask=000 0 0
```* Create folders in /mnt/HOMEBASE corresponing to the folders you want to bind: Documents, Pictures, etc...

* Copy the contents of /home/username/Documents to /mnt/HOMEBASE/Documents

* Manually bind one to the other to make sure that's what you want:
```
sudo mount --bind /mnt/HOMEBASE/Documents/home/username/Documents
```* Then decide which method you want to use to have it automount:
[http://ubuntuforums.org/showpost.php?p=11151879&postcount=6](http://ubuntuforums.org/showpost.php?p=11151879&postcount=6)

---

### Post by LifeBringer on 2011-08-19
> **vanadium said:**
> I do not think that this could be directly achieved in a space efficient way: it would require that you have a separate partition for each "special" folder, which is mounted on /home/Documents/Movies, /home/Documents/Music, ... etc.

Soft linking would be the only efficient way. In fact, the only drawback of that approach is that you "loose" the custom folder icons for the special folders. For the rest, it works perfectly. However, it is possible to manually assign custom icons to folders, so this little issue could be overcome.

The special icons are preserved through what I did. Yeah, if my HDD doesn't automount one of those partitions it would be a problem. The only issue I've encountered is that Ubuntu One doesn't sync to those folders as the other programs do.

I'll look into what Morbius1 is suggesting. Automount and speed issues (OS is on an SSD) is why I didn't just hardlink the /home folder.

---

### Post by LifeBringer on 2011-08-19
> **Morbius1 said:**
> 
```
UUID=6ABE4ECA0D /mnt/HOMEBASE ntfs defaults,nls=utf8,uid=1000,umask=000 0 0
``` This noticeably slowed down the boot process (25 s vs 14 s). Aren't umask=000 and defaults (exec) a repeat? Or were my original nodev,nosuid the reason for the problematic mounts?

> **Morbius1 said:**
> 
* Manually bind one to the other to make sure that's what you want:
```
sudo mount --bind /mnt/HOMEBASE/Documents/home/username/Documents
```* Then decide which method you want to use to have it automount:
[http://ubuntuforums.org/showpost.php?p=11151879&postcount=6](http://ubuntuforums.org/showpost.php?p=11151879&postcount=6)

What would you recommend rc.local (do you uncomment the first line?) or upstart? Which would be more efficient for the boot up?

UPDATE:
I removed nls=utf8, booting is a bit speedier. A better question would be, what could I add to my original fstab flags to guarantee automount on boot? What about *auto*, *nouser*, *async*? Though I hear auto is useless and that nouser and async are default.

UPDATE 2:
nodev and nosuid seem to be the problem. I'm keeping the fstab procedure to defaults,uid=1000

---

### Post by Morbius1 on 2011-08-20
> UUID=6ABE4ECA0D /mnt/HOMEBASE ntfs defaults,nls=utf8,uid=1000,umask=000 0 0> This noticeably slowed down the boot process (25 s vs 14 s). Aren't  umask=000 and defaults (exec) a repeat? Or were my original nodev,nosuid  the reason for the problematic mounts?That line is pretty much the standard way to automount an ntfs partition.
[COLOR=Blue][I]Note: That's a lie. The way Ubuntu's installer will automount an ntfs partition had you asked it to do so during the inital install is this way:
```
UUID=6ABE4ECA0D /mnt/HOMEBASE ntfs defaults,nls=utf8,umask=007,gid=46 0       0
```I modified it a bit because I'm a Samba user and my way makes sharing it easier. Plus I don't have any other users on my system and plus I don't want to get any errors when I send something to the trash.

[/I][COLOR=Black]As for slowing down the boot time I can't comment as I've never experienced this problem.
[/COLOR][/COLOR]> What would you recommend rc.local (do you uncomment the first line?) or upstart? Which would be more efficient for the boot up?* If you use rc.local you need to put the line right above the "[COLOR=Red]exit[/COLOR] 0" line.
[COLOR=Black]* I use the upstart process myself only because the standard way of doing it in fstab itself has issues and I find that upstart is the only reliable way to do it ( in Ubuntu anyway ).
* For a generation the way bind was used was in fstab itself but like I said above there is a problem ( there's a bug report about it somewhere ) using it in fstab in Ubuntu - still works fine in Debian. I haven't kept up with the bug report to see if it's still an issue.

[COLOR=Blue]**Note:**[/COLOR] However you use it it is deceptively seemless so to make sure it's actually doing what it's supposed to do you should run the following command after you reboot:
[/COLOR]```
mount
```When I do it on my own system for example I will get this back:
> /DATA/CommonHome/Documents on /home/morbius/Documents type none (rw,bind)
/DATA/CommonHome/Downloads on /home/morbius/Downloads type none (rw,bind)
/DATA/CommonHome/Music on /home/morbius/Music type none (rw,bind)
/DATA/CommonHome/Pictures on /home/morbius/Pictures type none (rw,bind)
/DATA/CommonHome/Public on /home/morbius/Public type none (rw,bind)
/DATA/CommonHome/Templates on /home/morbius/Templates type none (rw,bind)
/DATA/CommonHome/Videos on /home/morbius/Videos type none (rw,bind)

---

### Post by LifeBringer on 2011-08-20
Thanks, I'll try it the installation way, i.e. defaults,nls=utf8,umask=007,gid=46
I think upstart is the reason for the lack of slowdown. It might be running checks with the /user-dirs.dirs method. Also in 0 2, the 2 caused fsck to run a check at boot up on the partition every time. :-P

I'm currently trying rc.local, with
> exit 0
fi

The bash script and the Upstart methods hasn't worked for me so far. I've created the home-mounts.conf file as outlined by your post, even re-commenting the description line, but no luck.

The worst issue that I'm having is that when /mnt/HOMEBASE fails to mount. Upon manual recovery, i.e. mount /dev/sdb4/, none of my applications launch. I then restart and hopefully when it mounts the system works normally.

They should seriously consider decoupling data and .configs of the user folder.

---

### Post by Morbius1 on 2011-08-20
```
The bash script and the upstart method hasn't worked for me so far.
```If for whatever reason you can't mount using bind from the terminal there's no need to run it from upstart. Upstart simply creates a job that runs at boot.

This is the very first time I've ever read of anyone having a problem with actually using a "mount --bind". Are you getting error messages?

---

### Post by Morbius1 on 2011-08-20
You know, there is one thing I've been meaning to ask you:
> UUID=6ABE4ECA0DIf that just for posting purposes? The reason I ask is that a UUID for an NTFS partition should be 16 characters long.

---

### Post by LifeBringer on 2011-08-20
> **Morbius1 said:**
> You know, there is one thing I've been meaning to ask you:
If that just for posting purposes? The reason I ask is that a UUID for an NTFS partition should be 16 characters long.

Yup, posting purposes.

k, when /mnt/HOMEBASE fails to mount. I get this:
> user@computer:~$ google-chrome
[2523:2523:458811860:ERROR:shared_memory_posix.cc(172)] Creating shared memory in /dev/shm/.com.google.Chrome.Uo4jZJ failed: Permission denied
[2523:2523:458811946:ERROR:shared_memory_posix.cc(175)] Unable to access(W_OK|X_OK) /dev/shm: Permission denied
[2523:2523:458811955:FATAL:shared_memory_posix.cc(177)] This is frequently caused by incorrect permissions on /dev/shm.  Try 'sudo chmod 1777 /dev/shm' to fix.
[1:1:458831431:ERROR:zygote_main_linux.cc(464)] write: Broken pipe
Aborted
lifebringer@71f38r1n93r-de-Cambridge:~$ sudo chmod 1777 /dev/shm


Also, defaults,nls=utf8,umask=007,gid=46 didn't work.

Bind works fine through the terminal. Bind is better than editing /user-dirs.dir

Will try rc.local one more time.

UPDATE 1:
Apparently, user-dirs.dirs listed some folders as just "$HOME/".
I set the fstab flags to defaults,locale-en.UTF-8 0 0.
I'll come back to this thread if defaults.locale-en.UTF-8 0 0 doesn't work out.

The permissions are root, set to r&w, executable, plus no trash, but I'm fine with that.

---

### Post by cbowman57 on 2011-08-20
Sorry if I missed it when I scanned the thread.  I'm not currently using bind, but when I did I put it right at the bottom of my fstab.  In Ubuntu rc.local doesn't seem to be executed properly, I use a blockdev directive in mine, to get it to work I have to precede it with a sleep command.

```
sleep 10
blockdev --setra 8192 /dev/sda
```

---

### Post by Morbius1 on 2011-08-20
I remember reading something like that before. Didn't realize you could use a sleep command in fstab. In the interim I realized you could run a script in upstart and make it dependent on something else finishing. So I just added the manual mount command to my own upstart job and made it dependent on fstab completing:
```
start on stopped mountall
```
Different paths to the same goal.

---

### Post by LifeBringer on 2011-08-20
> **cbowman57 said:**
> 
```
sleep 10
blockdev --setra 8192 /dev/sda
```

Forgive me, but what would the end result look like? If say you were modifying fstab. RC.local hasn't failed yet, but if it fails, I'll erase it from the HOW TO.

Would the following work?
> 
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=e4add7f3-d5e1-4ad9-b97f-7babaa2e1585 /               ext4    noatime,nodiratime,errors=remount-ro 0       1
sleep 10
blockdev --setra 8192 /dev/sdb4
mount --bind /mnt/HOMEBASE/Documents /home/UbuntuLUVerXXX/Documents
mount --bind /mnt/HOMEBASE/Downloads /home/UbuntuLUVerXXX/Downloads
mount --bind /mnt/HOMEBASE/Music /home/UbuntuLUVerXXX/Music
mount --bind /mnt/HOMEBASE/Videos /home/UbuntuLUVerXXX/Videos
mount --bind /mnt/HOMEBASE/Pictures /home/UbuntuLUVerXXX/Pictures


Also should/could I replace /dev/sdb4 with my UUID?

> **Morbius1 said:**
> I remember reading something like that before. Didn't realize you could use a sleep command in fstab. In the interim I realized you could run a script in upstart and make it dependent on something else finishing. So I just added the manual mount command to my own upstart job and made it dependent on fstab completing:
```
start on stopped mountall
```
Different paths to the same goal.

I'll probably use the upstart job. But, after testing the reliability of the blockdev directive, I'll post that as an alternative.

UPDATE:
There it goes again, rc.local worked fine, but the /mnt/HOMEBASE gave me a mount error on start up. I have to chmod 1777 the shm aka /var/run everytime this happens.

If you could show me how how to include blockdev it would be much appreciated. Here's a similar [problem]("http://ubuntuforums.org/showthread.php?t=1756981")

---

### Post by cbowman57 on 2011-08-20
No, no sleep command in fstab, that was to make it execute blockdev in rc.local, sorry for the confusion. :)

I have no idea what would happen if you used "sleep" in fstab, probably just spit out an error, maybe freeze during boot.  I dunno.

---

### Post by LifeBringer on 2011-08-20
UPDATE: Ignore below

So, 
Fstab:
> # /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc nodev,noexec,nosuid 0 0
# / was on /dev/sda1 during installation
UUID=e4add7f3-d5e1-4ad9-b97f-7babaa2e1585 / ext4 noatime,nodiratime,errors=remount-ro 0 1
blockdev --setra 8192 /dev/sdb4


And rc.local as,
> #!bash...
sleep 10
mount --bind /dev/sdb4/Documents /home/UbuntuLUVerXXX/Documents
mount --bind /dev/sdb4/Downloads /home/UbuntuLUVerXXX/Downloads
mount --bind /dev/sdb4/Music /home/UbuntuLUVerXXX/Music
mount --bind /dev/sdb4/Videos /home/UbuntuLUVerXXX/Videos
mount --bind /dev/sdb4/Pictures /home/UbuntuLUVerXXX/Pictures
exit 0
fi

What would the fstab only method look like? Or is that not consistent?

---

### Post by cbowman57 on 2011-08-20
Ok, I seem to have just confused your process.  the blockdev is just a method to speed up drive access, it belongs in rc.local, it's not necessary for what you are trying to do.  I just used that as an  example of something that I had to start in rc.local, and whatr I had to do to get it to work.

If your folders are mounting correctly with what you have in the post above this I'd stick with it.

I've been trying to find an example, or reference, that shows how I did it but I don't have any surviving examples.  If I do locate it at some point I'll come back & post it.

---

### Post by cbowman57 on 2011-08-20
Ok, the problem I had was because it was an ancient reference [http://www.linuxquestions.org/questions/linux-general-1/mount-bind-fstab-problem-383883/](http://www.linuxquestions.org/questions/linux-general-1/mount-bind-fstab-problem-383883/)

I just reapplied it myself.  I like to maintain separate partitions for Downloads, Music, Pictures, etc..  I haven't tried this with ntfs, there might be some extra tricks required.

In preparation I had to create the bind directory in /mnt, then the Downloads, etc.. in /mnt/bind. 

Here's my fstab:

```
# 
# /etc/fstab: static file system information
#
# <file system>    <dir>    <type>    <options>    <dump>    <pass>
tmpfs        /tmp    tmpfs    nodev,nosuid    0    0
UUID=db376066-ca64-48ce-80ae-d0d0b16f8ad8 / ext4 relatime 0 1
UUID=b2724164-3dcb-4f0a-a3b2-9ffdae1421a3  /mnt/bind/Downloads ext4    relatime 0       0
UUID=2f407e00-4b94-44c1-8c22-f3492f410767  /mnt/bind/Maintenance ext4    relatime 0       0
UUID=13b3f8d5-ca84-4e51-8316-a1c0aa930c46  /mnt/bind/Music ext4    relatime 0       0
UUID=7c01f5fd-e741-4505-ac4b-62260a4c6943 /mnt/bind/Pictures ext4 relatime 0 0
/mnt/bind/Pictures /home/chuck/Pictures bind defaults,bind 0 0
/mnt/bind/Downloads /home/chuck/Downloads bind defaults,bind 0 0
/mnt/bind/Maintenance /home/chuck/Maintenance bind defaults,bind 0 0
/mnt/bind/Music /home/chuck/Music bind defaults,bind 0 0
```

---

### Post by Morbius1 on 2011-08-21
> UPDATE:
There it goes again, rc.local worked fine, but the /mnt/HOMEBASE gave me  a mount error on start up. I have to chmod 1777 the shm aka /var/run  everytime this happens.It doesn't matter if you put the bind in rc.local, fstab, upstart, or run it manually from the terminal after you login if the partition you are trying to bind to won't mount at boot.

Please post the output of each of the following commands:
```
sudo blkid -c /dev/null
cat /etc/fstab
mount
```

---

### Post by LifeBringer on 2011-08-21
You can ignore what's below and jump to the 'UPDATE' part.

sudo blkid -c /dev/null
> /dev/sda1: UUID="e4add7f3-d5e1-4ad9-b97f-7babaa2e1585" TYPE="ext4" 
/dev/sdb1: LABEL="PQSERVICE" UUID="1E3408C334089FBF" TYPE="ntfs" 
/dev/sdb2: LABEL="SYSTEM RESERVED" UUID="D698094B98092C15" TYPE="ntfs" 
/dev/sdb3: LABEL="Acer" UUID="76900B3B900B00FB" TYPE="ntfs" 
/dev/sdb4: LABEL="HOMEBASE" UUID="634EABE400ECA00D" TYPE="ntfs" 

cat /etc/fstab
> # /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0

# / was on /dev/sda1 during installation, SSD mod
UUID=e4add7f3-d5e1-4ad9-b97f-7babaa2e1585 /               ext4    discard,noatime,nodiratime,errors=remount-ro 0       0
tmpfs /tmp tmpfs defaults,noatime,mode=1777 0 0

# Data stuff
UUID=634EABE400ECA00D /mnt/HOMEBASE    ntfs    defaults,locale-en_us.UTF-8,UID=1000 0 0


mount (after successful boot)
> /dev/sda1 on / type ext4 (rw,noatime,nodiratime,discard,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,noatime,mode=1777)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
/dev/sdb4 on /mnt/HOMEBASE type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/mnt/HOMEBASE/Documents on /home/lifebringer/Documents type none (rw,bind)
/mnt/HOMEBASE/Downloads on /home/lifebringer/Downloads type none (rw,bind)
/mnt/HOMEBASE/Music on /home/lifebringer/Music type none (rw,bind)
/mnt/HOMEBASE/Videos on /home/lifebringer/Videos type none (rw,bind)
/mnt/HOMEBASE/Pictures on /home/lifebringer/Pictures type none (rw,bind)
gvfs-fuse-daemon on /home/lifebringer/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=lifebringer)


Oh cool, I'll add the blockdev to my rc.local.

mount (after unsuccessful boot)
> /dev/sda1 on / type ext4 (rw,noatime,nodiratime,discard,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,noatime,mode=1777)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
[COLOR="Red"]/dev/sdb4 on /mnt/HOMEBASE type fuseblk (rw,locale-en_us.UTF-8,UID=1000)
[/COLOR]binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/mnt/HOMEBASE/Documents on /home/lifebringer/Documents type none (rw,bind)
/mnt/HOMEBASE/Downloads on /home/lifebringer/Downloads type none (rw,bind)
/mnt/HOMEBASE/Music on /home/lifebringer/Music type none (rw,bind)
/mnt/HOMEBASE/Videos on /home/lifebringer/Videos type none (rw,bind)
/mnt/HOMEBASE/Pictures on /home/lifebringer/Pictures type none (rw,bind)
gvfs-fuse-daemon on /home/lifebringer/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=lifebringer)


UPDATE
Using 'mount' in the boot recovery shell omitted any mention of my sdb4 partition. So, it could be a ntfs specific issue, some other thread mentions that ntfs is handled not by fstab and that could be the source of the issue.

If I disable my ntfs on boot, i.e. noauto, my boot up is ~5 seconds vs ~20 seconds with ntfs.

I currently set the fstab settings to 'noauto', is there anyway to have rc.local or upstart automount the partition for me? Preferably, something to automount the partition after login. Possibly like this: [http://ubuntuforums.org/showthread.php?t=527713](http://ubuntuforums.org/showthread.php?t=527713)

UPDATE 2 (solution)
Fstab:
> # <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc nodev,noexec,nosuid 0 0
#SSD MOD
tmpfs /tmp tmpfs defaults,noatime,mode=1777 0 0
UUID=e4add7f3-d5e1-4ad9-b97f-7babaa2e1585 / ext4 discard,noatime,nodiratime 0 0
#DATA MOD
UUID=634EABE400ECA00D /mnt/HOMEBASE ntfs nodev,nosuid,noatime,nls=utf8,uid=1000,umask=000,[COLOR="Red"]noauto[/COLOR] 0 0

rc.local
> #SSD stuff IO
echo deadline > /sys/block/sda/queue/scheduler
echo 1 > /sys/block/sda/queue/iosched/fifo_batch

#Mounting stuff
[COLOR="Red"]mount /dev/sdb4 /mnt/HOMEBASE[/COLOR]
mount --bind /mnt/HOMEBASE/Downloads /home/lifebringer/Downloads
mount --bind /mnt/HOMEBASE/Music /home/lifebringer/Music
mount --bind /mnt/HOMEBASE/Videos /home/lifebringer/Videos

exit 0
fi

As you can see fstab + ntfs = sh*t doesn't mount
There is a delay with bind, but I believe it is associated with the mounting process.

---

