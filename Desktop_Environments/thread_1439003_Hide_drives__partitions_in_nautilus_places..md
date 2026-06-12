---
title: "Hide drives / partitions in nautilus places."
date: 2010-03-25
forum: Desktop Environments
---

### Post by t.rei on 2010-03-25
Hi, 

I have quite a lot of testing operating systems installed. Some with their own home or boot partition. 

Now my places section in nautilus is an utter MESS.

I was not able to find any working solution how to hide these partitions. Can anyone please help me out?

thanks,

t.rei

---

### Post by Grenage on 2010-03-25
I *believe* that anything mounted under /media is automatically listed in Nautilus, but anything mounted elsewhere is not.

For example, tend to mount things I don't need listed, under /mnt.

---

### Post by t.rei on 2010-03-25
Thats the thing, the partitions arent mounted. As a matter of fact they arent even in fstab.

So I just have a very long list of not-mounted-partitions under places. 

Somewhere these must be detected, no? Probably any 'potentially mountable partition' just gets found and listed.

---

### Post by Grenage on 2010-03-25
[This]("http://ubuntuforums.org/showthread.php?t=567003") looks like it might cover it.

---

### Post by t.rei on 2010-03-25
yes, I have tried that. Unfortunately it didn't work. Maybe it's not HAL anymore, that is responsible? That post is from 2007 after all. :)

I did use google and forum search before posting. ;)

---

### Post by Grenage on 2010-03-25
Touché!  I'm so used to searching and posting links to solutions on common problems, and I'm very tired. :)

I have no media to test this with, but I will do at work tomorrow.  If you haven't got a solution by then, I'll dabble and see what I can come up with.

---

### Post by t.rei on 2010-03-25
cool, thanks. I will try no longer than another 30 minutes tonight. If I should find out how to do it, I'll definately post.

---

### Post by t.rei on 2010-03-26
Well, I haven't solved the problem.
I have lessened it by removing 3 alternate linux systems (*sniff* my playgrounds).

On the other hand, I now have tons of diskspace.

So the problem remains and I'm still looking for a solution, in order to get my working desktop 'just perfect'.

If any gnome-dev should happen to read this: I think the intuitive part would be a 'Computer -> rightclick-on-drive -> properties -> show in nautilus places [x]' kind of thing. Or at least a flag like that accessible via gconf-editor.

---

### Post by mcduck on 2010-03-26
> **t.rei said:**
> Thats the thing, the partitions arent mounted. As a matter of fact they arent even in fstab.

So I just have a very long list of not-mounted-partitions under places. 

Somewhere these must be detected, no? Probably any 'potentially mountable partition' just gets found and listed.

Then *add* them to fstab, set the mount point to somewhere else than in /media, and add "noauto" to mount options.

That way the partitions won't show in Nautilus, and aren't mounted automatically on boot.

---

### Post by t.rei on 2010-03-26
Wonderfull! that does it! 

Thanks a lot. 

This is not really intuitive, but it works. :)

---

### Post by rnerwein on 2010-03-26
hi
have a look at: man udev ( if you want to realy hide your partitions )
hide unmounted partitions:
create a file under /etc/udev/rules.d/
own rule:  /etc/udev/rules.d/hide-partitions.rules
# you can just hide partitions and devices etc directly through their partition mount location (eg /dev/sda*)
#   It does hide my two partitions (52 GB Filesystem, System Reserved) and
#   the floppy drive... just also the DVD drive.!!!!!!!!.. :/
# we only care about block devices

    ACTION!="add|change", GOTO="hide_partitions_end"
    SUBSYSTEM!="block", GOTO="hide_partitions_end"
    KERNEL=="loop*|ram*", GOTO="hide_partitions_end"

# Floppy Drive which should not display
    KERNEL=="fd0", ENV{ID_DRIVE_FLOPPY}="1", ENV{DKD_PRESENTATION_HIDE}="1"

# Partition sda2 that we want to hide from gnome
    KERNEL=="sda2", ENV{DKD_PRESENTATION_HIDE}="1"

# Partition sda3 that we want to hide from gnome
    KERNEL=="sda3", ENV{DKD_PRESENTATION_HIDE}="1"

LABEL="hide_partitions_end"

is it that what you are looking for ?
ciao

---

### Post by t.rei on 2010-03-26
Interesting. That seems like a rather sensible approach. Unfortunately I am currently short a testing installation. 

I'll try this when I'm back from the weekend. But so far the solution with mountpoints outside of /media works. Marking as solved.

---

### Post by bobpaul on 2010-04-03
> **rnerwein said:**
> hi
have a look at: man udev ( if you want to realy hide your partitions )
hide unmounted partitions:
create a file under /etc/udev/rules.d/
own rule:  /etc/udev/rules.d/hide-partitions.rules

...

is it that what you are looking for ?
ciao

What does that even do? I looked at man udev and there's no mention of DKD_PRESENTATION_HIDE. Does this only prevent the devices from showing in Nautilus Places, or does it do something like remove the /dev/sda2 entry from showing, preventing it from being mounted or manipulated with tools like dd at all?

---

### Post by dtach on 2010-05-07
Hi, I'm an fairly new Ubuntu user and would like to hide my other partitions too. However, I'm unfamiliar with how to "add" drives to fstab. In fact, I don't even know what fstab is =/. If someone is able to give me a quick walk through how to do this, it would be appreciated a whole lot.

Thanks in advance,
Danny

---

### Post by Grenage on 2010-05-07
Danny,

Do the partitions automatically mount when Ubuntu loads up?  Do you want these drives hidden, or hidden and simply not used at all?

---

### Post by dtach on 2010-05-09
Well, originally they didn't automatically mount, but after reading a dual boot (7 and Ubuntu) tutorial online, I downloaded something called "NTFS Configuration Tool" and now all partitions automatically mount.  Also, it's probably important I tell you: I'm unable to unmount the partitions I don't want to use without using sudo nautilus.

      As for your second question: The partitions being either hidden, or "hidden-completely-without-any-availability-at-all" would be fine. I don't believe I'll ever need to access that part of my drive from Ubuntu. Thank you again in advance, I really do appreciate any help I can get!

Danny

---

### Post by bobpaul on 2010-05-10
> **dtach said:**
> Well, originally they didn't automatically mount, but after reading a dual boot (7 and Ubuntu) tutorial online, I downloaded something called "NTFS Configuration Tool" and now all partitions automatically mount.  Also, it's probably important I tell you: I'm unable to unmount the partitions I don't want to use without using sudo nautilus.

```

$ sudo gedit /etc/fstab

```

I expect you'll see something like this:

```

/dev/sda3  /             ext4    relatime,errors=remount-ro 1 1
//dev/sda5 /home         ext3    relatime,errors=remount-ro 0 2
/dev/sda1  /mnt/Windows  ntfs3g  errors=remount-ro          0 2
/dev/sda6  none         swap     sw
/dev/sda2  /boot         ext3    relatime,errors=remount-ro 0 1

```

Put a # in front of the NTFS lines to comment them. On next reboot, they shouldn't be mounted automatically. You could also try something like ",noauto" on the end of the options line, though this might make them show up in nautilus as unmounted.

---

### Post by Grenage on 2010-05-10
Ok dokes, could you please post your /etc/fstab file?

---

### Post by dtach on 2010-05-10
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	nodev,noexec,nosuid	0	0
#Entry for /dev/sda3 :
UUID=052a5338-47c3-4224-9120-9c078962c42e	/	ext3	errors=remount-ro	0	1
#Entry for /dev/sda4 :
UUID=116F76BF59B32A05	/media/Storage	ntfs-3g	defaults,nosuid,nodev,locale=en_US.utf8	0	0



I want to keep the "storage" part of the drive, and bobpaul-- i dont think the other partitions are not showing up on here

---

### Post by Grenage on 2010-05-11
> **dtach said:**
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	nodev,noexec,nosuid	0	0
#Entry for /dev/sda3 :
UUID=052a5338-47c3-4224-9120-9c078962c42e	/	ext3	errors=remount-ro	0	1
#Entry for /dev/sda4 :
UUID=116F76BF59B32A05	/media/Storage	ntfs-3g	defaults,nosuid,nodev,locale=en_US.utf8	0	0


Easiest thing to do, is to add the partitions you don't want to see, and set their mount point to be */mnt* (linux's standard mount directory).  Unless something is mounted in */media*, it won't automatically show up in the nautilus bar.  For example:

```
/dev/sda4     /mnt/mypartition    ntfs-3g	defaults,nosuid,nodev,locale=en_US.utf8	0	0
```

You'll need to make sure that mount point exists first:

```
sudo mkdir /mnt/mypartition
```

Note that you don't *need* to use UUIDs for partitions, but it can sometimes be handy;  I only use them for removable media or in machines where I'll change the partitions.

Once done, you can test the changes with:

```
sudo mount -a
```

---

### Post by dtach on 2010-05-11
Great, that did the trick!! Thank you so much, you've been a huge help.

danny

---

### Post by Grenage on 2010-05-11
Awesome, glad it worked!

---

### Post by pt123 on 2010-08-27
> **rnerwein said:**
> hi
have a look at: man udev ( if you want to realy hide your partitions )
    KERNEL=="sda2", ENV{DKD_PRESENTATION_HIDE}="1"
ciao

Note in Lucid DKD_PRESENTATION_HIDE was changed to 
UDISKS_PRESENTATION_HIDE

[http://fedoraforum.org/forum/showthread.php?t=250263](http://fedoraforum.org/forum/showthread.php?t=250263)

---

### Post by t.rei on 2012-01-28
[http://www.worldofnubcraft.com/969/hide-your-disks-or-partitions-from-nautilus/](http://www.worldofnubcraft.com/969/hide-your-disks-or-partitions-from-nautilus/)

This sums up the current state of this matter, I guess. (nice step by step guide + some text for the interested). Just reinstalled and lo-and-behold, found my old thread in google. ;)

---

### Post by leona on 2012-12-24
> **t.rei said:**
> [http://www.worldofnubcraft.com/969/hide-your-disks-or-partitions-from-nautilus/](http://www.worldofnubcraft.com/969/hide-your-disks-or-partitions-from-nautilus/)

This sums up the current state of this matter, I guess. (nice step by step guide + some text for the interested). Just reinstalled and lo-and-behold, found my old thread in google. ;)

I was going to say this didn't work, but it was a cut and paste error 'watch that' it seems to copy the 'smart quotes' rather than " once I had corrected that, it worked.

---

