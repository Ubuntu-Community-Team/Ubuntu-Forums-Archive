---
title: "root.disk transfer"
date: 2008-12-29
forum: General Help
---

### Post by Gizenshya on 2008-12-29
Hello all, I'm new to the forums.

I had vista 64 and ubuntu 8.04 (64) installed using the Wubi installer.  It worked great, but (its a long story) I want to restore the programs from the root.disk folder to my new Ubuntu 8.04 (same version) install (on its own drive).

The reason is that now I have a very slow internet connection, and am no longer able to get the programs like usual, but I have all the programs I need on the root.disk drive.

Is there anyway to maybe mount the drive and copy the root.disk image to a larger drive?  Would I need a third drive with ubuntu on it to do so? (use drive C to copy files from root.disk on drive A to the ubuntu partition on drive 2)?  I was hoping I'd be able to boot frolm the Live CD and copy files over from root.disk on drive A to drive B and replace the files.

Also, if there is a way to do that, would the programs likely work?  The ubuntu install on the lone drive is a basic one, and only has the files on it that came with the live disk, so if whatever I try fails, I've lost nothing and can just try something else.

---

### Post by Gizenshya on 2008-12-29
another question-- is there a way to mount a root.disk image (or whatever its called) through ubuntu (with tools available on the live CD).

or...

would it be possible to reinstall vista 64 and ubuntu 8.04 64 as they were before, and then copy over the root.disk?

---

### Post by Jammanuser on 2008-12-30
> **Gizenshya said:**
> another question-- is there a way to mount a root.disk image (or whatever its called) through ubuntu (with tools available on the live CD).

or...

would it be possible to reinstall vista 64 and ubuntu 8.04 64 as they were before, and then copy over the root.disk?

Yes there is...see [this link]("http://ubuntuforums.org/showthread.php?t=1007816") where I describe precisely how to mount your root.disk with the LiveCD! :)

Cheers! :popcorn:

-jam man

:guitar:

---

### Post by Gizenshya on 2009-01-04
thanks :)

ok, now I reinstalled windows and ubuntu within it...

But, when I name the new root.disk to root.disk.bak and I move the old one that I want to restore to the folder as root.disk, it doesn't boot :(

when I boot in recovery it reports that root.disk is an unknown volume type.  after that, everything is fille/directory/etc. doesn't exist, and it gives me a busybox terminal :(

any ideas on what to do?

---

### Post by Jammanuser on 2009-01-04
> **Gizenshya said:**
> thanks :)

ok, now I reinstalled windows and ubuntu within it...

[COLOR="Red"]But, when I name the new root.disk to root.disk.bak and I move the old one that I want to restore to the folder as root.disk,[/COLOR] it doesn't boot :(

when I boot in recovery it reports that root.disk is an unknown volume type.  after that, everything is fille/directory/etc. doesn't exist, and it gives me a busybox terminal :(

any ideas on what to do?

I'm not sure if i understand what you're trying to do...;) If you want the programs and stuff on your old root.disk, then simply replace the new with the old...only move the new root.disk completely out of the folder its in, not just rename it. I think that the reason it doesn't work is Ubuntu detects there is two root.disks in the same folder, even though the other one is named "root.disk.bak", and so this confuses it, and it ends up trying to boot from the ".bak" one instead of the other one, which of course doesn't work. :) So i would suggest moving the new root.disk somewhere else than the folder the old one is now in, so it wont get confused, and that should work. :)

Cheers! :popcorn:

-Jam man

:guitar:

---

### Post by Gizenshya on 2009-01-05
good point...

I went ahead and took that a bit further and moved the whole ubuntu folder to another folder, and moved the one from the old wubi installation to its place.

but alas, that wasn't the only problem.

now it says when searching for root.disk/by uuid/blah blah blah, it doesn't find one with that UUID (because the boot loader still uses the command line for the new wubi.

its weird, though... it shows both kernel versions each with its own recovery mode in the boot menu (not in the windows loader, which I use, but from grub when I hit F8 to edit the boot options after I choose ubuntu).

So, there are a few paths to follow from this point.

1.  find the UUID of the drive and insert it into the boot command line.

2.  find a way to boot from it without a uuid (just boot from whatever disk is in root.disk).

I opted for route 1, which I haven't had luck with yet :(  Despite having used about 5 different distros ob linux over the past several years, I'm still very much a linux noob... I don't think I've ever sucessfully compiled a source file (which is one reason I love the debian installer in ubuntu woot lol).

anyway, I didn't get far into your tutorial on mounting the root.disk from the live CD :( I can't find out where my main hard drive is mounted.  I tried it with sda1, sda2, .. on up to sda6, and nothing.  it keeps saying that there is nothing there.  I took out the hard drive and put it in an external sata case and it automounts well and good from the live CD, but I still can't quite figure out how to mount it.  :(    ohh, and it I didn't see "win" or OS under Places (so I couldnt' do that step)...  I still haven't been able to mount windows from the drive that ubuntu is on.  I usually just stick it in an external drive and mount it frm another ubuntu drive (or just boot windows) when I need the files haha

So... any idea on route 2? :p

sorry for all the trouble :(

---

### Post by Jammanuser on 2009-01-05
> **Gizenshya said:**
> good point...

I went ahead and took that a bit further and [COLOR="Red"]moved the whole ubuntu folder[/COLOR] to another folder, and moved the one from the old wubi installation to its place.



I didn't mean move the whole Ubuntu folder! :) I simply meant move the new **root.disk** from the new Ubuntu folder. :D The root.disk is what you needed to move, **not** the Ubuntu folder! So i would suggest moving the Ubuntu folder back to its former place, and this time only move the newer **root.disk** to somewhere else, and put your old root.disk in its place...;)

Make sure to do that, and it should work! :popcorn:

Cheers! :)

-Jam man

:guitar:

---

### Post by Jammanuser on 2009-01-05
> **Gizenshya said:**
> good point...

I went ahead and took that a bit further and moved the whole ubuntu folder to another folder, and moved the one from the old wubi installation to its place.

but alas, that wasn't the only problem.

now it says when searching for root.disk/by uuid/blah blah blah, it doesn't find one with that UUID (because the boot loader still uses the command line for the new wubi.

its weird, though... it shows both kernel versions each with its own recovery mode in the boot menu (not in the windows loader, which I use, but from grub when I hit F8 to edit the boot options after I choose ubuntu).

So, there are a few paths to follow from this point.

1.  find the UUID of the drive and insert it into the boot command line.

2.  find a way to boot from it without a uuid (just boot from whatever disk is in root.disk).

I opted for route 1, which I haven't had luck with yet :(  Despite having used about 5 different distros ob linux over the past several years, I'm still very much a linux noob... I don't think I've ever sucessfully compiled a source file (which is one reason I love the debian installer in ubuntu woot lol).

anyway, I didn't get far into your tutorial on mounting the root.disk from the live CD :( I can't find out where my main hard drive is mounted.  I tried it with sda1, sda2, .. on up to sda6, and nothing.  it keeps saying that there is nothing there.  [COLOR="Red"]I took out the hard drive and put it in an external sata case[/COLOR] and it automounts well and good from the live CD, but I still can't quite figure out how to mount it.  :(    ohh, and it [COLOR="Red"]I didn't see "win" or OS[/COLOR] under Places (so I couldnt' do that step)...  I still haven't been able to mount windows from the drive that ubuntu is on.  I usually just stick it in an external drive and mount it frm another ubuntu drive (or just boot windows) when I need the files haha


Try these commands:
```

sudo mkdir /win
sudo mount /dev/**[COLOR="Red"]sdb1[/COLOR]** /win
sudo mkdir /vdisk
sudo mount -o loop /win/ubuntu/disks/root.disk /vdisk
```

And if sdb1 doesn't work, try sdc1, or sdd1, and so on until you find the right disk letter. Did you make sure to enter all the commands the last time...i.e. the "sudo mkdir /win" and so forth? That command creates your /win folder to mount your root.disk from...if you skipped it, it explains why you couldn't find your /win folder! :)

Cheers! :popcorn:

-Jam man

:guitar:

---

### Post by Gizenshya on 2009-01-12
that didn't work either :(

my guess is because one of the updates updated the kernel to a newer version.  

but I've given up.  I just decided to delete it and start again.  i'm back with a fast connection now, so I can reinstall all that stuff.  I'd normally keep trying regardless to finish the issue, but classes have already started and I won't have any free time for quite some time :(

thank you for your help, though.

:)

---

