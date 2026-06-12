---
title: "System Restore"
date: 2006-02-03
forum: Desktop Environments
---

### Post by aseem_mal on 2006-02-03
**My Ubuntu Adventures:**
So, I have my newly installed Ubuntu all setup, everythings working fine, all devices, even my wifi... but... what if someday I screw up something? I'd like to be able to go back in time, like a H.G. Wells' "Time Machine".
Windows XP has the System Restore. What does Ubuntu have?? ;)

---

### Post by AirIntake on 2006-02-03
I wouldn't mind something like this as well. I'm really happy with my Ubuntu install right now and would hate to have to do it all over again.

---

### Post by GeneralZod on 2006-02-03
As far as I'm aware, there isn't anything, really.  I always just reboot into Knoppix and take a .tar.bz2 of my / partition, but that's not exactly a quick or elegant process :/

---

### Post by gamma on 2006-02-03
There's Konserve, but I'm not 100% how that works.

---

### Post by sfabel on 2006-02-04
Don't screw it up. ;)

No, seriously. Booting into single-user mode and backing up / and other important partitions are probably the only way.

Although:
To keep a stable, running system without you having the possibility of screwing up, would be to remove all lines in /etc/apt/sources.list except for the security updates.

If you then backup your hidden folders in your homedir (the ones starting with ".", except "." and ".." themselves), you should be fine. Set it up as a cron job and you're set with your time machine. :)

Just my $0.02.

Have fun,

Stephan

---

### Post by aseem_mal on 2006-02-04
Don't screw it up. ;)

No, seriously. Booting into single-user mode and backing up / and other important partitions are probably the only way.

Although:
[QUOTE=sfabel]To keep a stable, running system without you having the possibility of screwing up, would be to remove all lines in /etc/apt/sources.list except for the security updates.[/QUOTE]

Hi Stephan: I am quoting a copy of my sources list BELOW, can you please tell which lines to remove, and which to keep?
Thanks,
Aseem
> 
deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted

deb [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy universe
# deb-src [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
# deb-src [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

#deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) breezy universe


---

### Post by engla on 2006-02-04
There is [Howto: Backup and restore your system!]("http://ubuntuforums.org/showthread.php?t=81311")

---

