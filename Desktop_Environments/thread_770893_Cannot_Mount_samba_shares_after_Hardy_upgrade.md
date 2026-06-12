---
title: "Cannot Mount samba shares after Hardy upgrade"
date: 2008-04-27
forum: Desktop Environments
---

### Post by hiflyer on 2008-04-27
I upgraded from 7.10 to 8.04 using the upgrade method. No obvious errors. Everything seems to generally work but 2 things. The first was that the grub menu file was not upgraded to include the new operating system. I therefore hand copied and modified the lines to what I guess the new files to be. It seems to work.

I added the following to the menu and got no objections:

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=fd8f19a1-4bed-4928-8726-fdc16025b045 ro splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

No matter whether booting from the original or the one above, the network files that I mount using the fstab which worked just fine under 7.10 stopped working. 

the results from sudo mount -a give

mount error: could not find target server. 
TCP name linux-server/bee_ShareDsk1 not found
No ip address specified and hostname not found

hosts and hostname files  appear to be correct. I use DHCP for addressing from my router.

I have also tried replacing the linux-server name with the ip address but it then responds 

mount error 13 = Permission denied

Any suggestions of why the information is not getting back to the mount function. 

Oh, under nautilus, it mounts these shares from the server just fine. I need to mount these with the mount command as I wish to define them under wine.

thanks

---

### Post by hfranco on 2008-04-28
I'm actually having the same problem with Samba.  I have upgraded to Hardy Server edition from Dapper 6.04 Server edition.

I cannot access the Samba shares on the server from any other pc or Linux box.  I was to do this before without a problem for a little over a  year.

Any suggestions?

---

### Post by eriqjaffe on 2008-04-28
I had similar problems when I was running 8.04 beta.  It seems to be a samba issue rather than a Ubuntu issue.  I fixed it by simply rolling back [smbfs](http://packages.ubuntu.com/gutsy/smbfs) and [samba-common](http://packages.ubuntu.com/gutsy/samba-common) to 3.0.26a.

Just download the debs (you can grab them manually from the links above) and install them using "dpkg -i --force-downgrade" in the terminal.

---

### Post by hfranco on 2008-04-28
> **eriqjaffe said:**
> I had similar problems when I was running 8.04 beta.  It seems to be a samba issue rather than a Ubuntu issue.  I fixed it by simply rolling back [smbfs](http://packages.ubuntu.com/gutsy/smbfs) and [samba-common](http://packages.ubuntu.com/gutsy/samba-common) to 3.0.26a.

Just download the debs (you can grab them manually from the links above) and install them using "dpkg -i --force-downgrade" in the terminal.

Thanks eriqjaffe.  I'll try that when I get home and let you know my results. I appreciate it.

---

### Post by hfranco on 2008-04-28
eriqjaffe this worked thanks.

---

### Post by hiflyer on 2008-05-18
I did figure out why I could not connect to the share device. The issue is getting the ip address. Whether it is Samba or in the operating system is unclear. A solution is to hard code the IP address in the file hosts in the /etc directory. You may also need to lock the address in the router so it does not change otherwise it will stop working if the router changes the ip address.

---

### Post by eriqjaffe on 2008-05-19
Good to know, I may try that out since the system I connect to most has a static IP address.

---

### Post by scohar70 on 2008-05-20
I had this problem too... couldn't mount from fstab after upgrading to 8.04 Hardy.

I tried setting the fstab entries to the IP address, but it didn't work for me.

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=9a47ebde-643b-48e3-ab07-35a47ef44bf5 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=68f99861-504f-4e02-a658-77a081d2ecf5 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

# Temporary Seagate mount for just when I need to do backups
# /dev/sdb1 /media/seagate vfat user,rw,suid,umask=0000,utf8 0 0

# Samba mount
[B]//jaguar/Backups	/media/backups	smbfs	credentials=/etc/samba/user,rw,uid=scott	0	0
[/B]
```

Ultimately, I downgraded to 3.0.26a, as suggested above, and it works now.

I didn't really want to do the downgrade, and I suppose I will have to keep an eye out for a "real fix" in the future, but at least it's working for now.

---

### Post by lunaz on 2008-05-24
before i try your method, a question:
do i downgrade on hardy client, hardy server, or both?

> **eriqjaffe said:**
> I had similar problems when I was running 8.04 beta.  It seems to be a samba issue rather than a Ubuntu issue.  I fixed it by simply rolling back [smbfs](http://packages.ubuntu.com/gutsy/smbfs) and [samba-common](http://packages.ubuntu.com/gutsy/samba-common) to 3.0.26a.

Just download the debs (you can grab them manually from the links above) and install them using "dpkg -i --force-downgrade" in the terminal.

---

### Post by eriqjaffe on 2008-05-24
> **lunaz said:**
> before i try your method, a question:
do i downgrade on hardy client, hardy server, or both?I only downgraded the client - the server I'm connecting to isn't running Ubuntu, so I didn't touch it.

---

### Post by lunaz on 2008-05-25
```

rebecca@soggy:~/Desktop/sambadebs$ sudo dpkg -i --force-downgrade samba-common_3.0.26a-1ubuntu2.3_i386.deb
dpkg - warning: downgrading samba-common from 3.0.28a-1ubuntu4 to 3.0.26a-1ubuntu2.3.
(Reading database ... 95771 files and directories currently installed.)
Preparing to replace samba-common 3.0.28a-1ubuntu4 (using samba-common_3.0.26a-1ubuntu2.3_i386.deb) ...
Unpacking replacement samba-common ...
dpkg: dependency problems prevent configuration of samba-common:
 samba-common depends on libldap2 (>= 2.1.17-1); however:
  Package libldap2 is not installed.
dpkg: error processing samba-common (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 samba-common
rebecca@soggy:~/Desktop/sambadebs$

```

well i got errors with dependancy. does this mean i have to dl all the ones on that page and do that command on all the packages seperately? i only downloaed the smbfs and samba-common packages that were linked.

---

### Post by lunaz on 2008-05-26
fixed it! i had to install the ldap2 package first found here
[http://packages.ubuntu.com/gutsy/i386/libldap2/download](http://packages.ubuntu.com/gutsy/i386/libldap2/download)

then i did the other 2 linked above. here's the commands.

```

sudo dpkg -i --force-downgrade libldap2_2.1.30-13.4_i386.deb
sudo dpkg -i --force-downgrade samba-common_3.0.26a-1ubuntu2.3_i386.deb
sudo dpkg -i --force-downgrade smbfs_3.0.26a-1ubuntu2.3_i386.deb

```

---

### Post by GoneSouth on 2008-06-10
lunaz - thx, this worked for me as well.

is there a bug open for this that anyone's aware of ??

 - GS

<< rant on - k is hardy about the buggiest ubuntu release in the last two years or is it just me ? >>

---

### Post by GoneSouth on 2008-06-10
Oh, my bad. This fixed my samba mounting problem, but now synaptic thinks I have broken dependencies and won't let me install any updates? Is there a way to fix / override this?

** update ... i had to downgrade smbclient and winbind to the gutsy version level as well. this fixed the broken dependency.

---

### Post by RoboRutt on 2008-06-11
Top feng-shui people - thanks for all your help!  I upgraded, and am now winding my way around all those little customisations that I have made over the past year... (7.04 --> 7.10 --> 8.04 )

I thought I would contribute to the world by winding these tips into a single list of commands... :)

Assumes that you are using a i386 machine... hope that helps - credits to the real authors (thread previous) I just wound it together...

```

wget http://mirrors.kernel.org/ubuntu/pool/main/o/openldap2/libldap2_2.1.30-13.4_i386.deb
wget http://security.ubuntu.com/ubuntu/pool/main/s/samba/samba-common_3.0.26a-1ubuntu2.3_i386.deb
wget http://security.ubuntu.com/ubuntu/pool/main/s/samba/smbfs_3.0.26a-1ubuntu2.3_i386.deb
sudo dpkg -i --force-downgrade libldap2_2.1.30-13.4_i386.deb
sudo dpkg -i --force-downgrade samba-common_3.0.26a-1ubuntu2.3_i386.deb
sudo dpkg -i --force-downgrade smbfs_3.0.26a-1ubuntu2.3_i386.deb
rm libldap2_2.1.30-13.4_i386.deb
rm samba-common_3.0.26a-1ubuntu2.3_i386.deb
rm smbfs_3.0.26a-1ubuntu2.3_i386.deb

```

---

### Post by RoboRutt on 2008-06-12
DOH !!

I just did a normal update for hardy, and of course it upgraded my samba etc.. and now the drive won't mount again !

Just wound the following commands into a single line entry for those that want to run it regularly... hope that helps :)

```


wget http://mirrors.kernel.org/ubuntu/pool/main/o/openldap2/libldap2_2.1.30-13.4_i386.deb; wget http://security.ubuntu.com/ubuntu/pool/main/s/samba/samba-common_3.0.26a-1ubuntu2.3_i386.deb; wget http://security.ubuntu.com/ubuntu/pool/main/s/samba/smbfs_3.0.26a-1ubuntu2.3_i386.deb; sudo dpkg -i --force-downgrade libldap2_2.1.30-13.4_i386.deb; sudo dpkg -i --force-downgrade samba-common_3.0.26a-1ubuntu2.3_i386.deb; sudo dpkg -i --force-downgrade smbfs_3.0.26a-1ubuntu2.3_i386.deb; rm libldap2_2.1.30-13.4_i386.deb; rm samba-common_3.0.26a-1ubuntu2.3_i386.deb; rm smbfs_3.0.26a-1ubuntu2.3_i386.deb; sudo mount -a


```

:)RR

---

### Post by eriqjaffe on 2008-06-12
You can always block the updates through your package manager so that they'll get bypassed when you do an update/upgrade.

```
echo "foo samba-common" | sudo dpkg --set-selections
echo "foo smbfs" | sudo dpkg --set-selections
```

...I don't use Synaptic, but I know it has a mechanism to block updates as well.

Of course, that could lead to dependency problems down the road, but...

---

### Post by RogueLeader on 2008-06-27
Hello everyone.  I recently upgraded from Gutsy to Hardy on my laptop.  Fortunatley, this went much more smoothly than my Feisty to Gutsy upgrade on my Desktop a while back.  At any rate...

Like all of you, I was also experiencing errors mounting samba shares that had worked perfectly before my upgrade.  Auto mounting (via entries in /etc/fstab) didn't work, and neither did manually trying to mount.  I came across this thread and was almost resigned to revert my samba client package to the earlier version.  I dug a little bit deeper and have figured out what the problem was for me.  Hopefully it will work for you guys too, so you can get back up to date with your samba packages!

I, like the OP, was getting Error 13: Permission denied errors despite always being authenticated in Gutsy.  I also use a credentials file, like I noticed **scohar70** did.  Here was where my, and I suspect most people here's problem lied.  After stumbling upon [this discussion from another forum]("http://www.linuxquestions.org/questions/linux-networking-3/cifs-mount-error-13-permission-denied-cifs-sucks-463271/"), I caught a small response explaining the hangup.  Someone noted that samba (I suppose the new version) interpreted, say, "user = bryan" as indicating the user " bryan" (with space).  I edited /etc/samba/user (my credentials file) to eliminate all spaces, and voila!  Manual mounting (and auto-mounting via fstab) work for me again!

This might also explain why this is not a widespread issue.  Users of credentials files probably aren't too numerous in the scheme of things.  On top of that, this setback only targets people with an ill configured file.

Hope this was the issue... some people in the discussion I linked claimed they still couldn't get it to work even with no whitespace issues.  Good luck!

By the way, my manual mount command that worked was:

```
sudo mount -t smbfs //valkyrie.local/gallant /media/valkyrie/gallant -o credentials=/etc/samba/user,uid=youse,gid=youse

```

and my /etc/fstab entry (for the same share) is

```
//valkyrie.local/gallant /media/valkyrie/gallant smbfs credentials=/etc/samba/user,uid=youse,gid=youse 0 0
```

---

