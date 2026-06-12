---
title: "Grub help? Older version doesn't support uuid."
date: 2009-03-02
forum: General Help
---

### Post by dragos240 on 2009-03-02
Hello, i just installed arch on another partition and the grub version is 0.97, this version does not support the uuid command. I do not fear that i won't be able to get into my ubuntu partition, i think that i can, but i just don't know how... My old grub setup i will list in the code box below:

```

uuid  07446460-fa38-4d28-bf91-23ef304158d1
kernel  /boot/vmlinuz-2.6.27-11-generic root=UUID=07446460-fa38-4d28-bf91-23ef304158d1 ro quiet splash
initrd  /boot/initrd.img-2.6.27-11-generic
quiet

```I was able to boot into ubuntu using this configuration a few nights ago, but forgot what i did, when i keep trying to boot into ubuntu, it goes to it's busybox. Could someone please help, i had to boot off the live-cd of ubuntu to get on here, and i really would rather use my normal ubuntu, and arch didn't come with any wireless internet tools, so i couldn't get on the internet. Any ideas,

Thanks in advance,
Dragos240

---

### Post by dragos240 on 2009-03-02
Bump, i'm sorry, i really need someone to reply to this, i want my ubuntu back :(

---

### Post by unutbu on 2009-03-02
Intrepid ext3 partitions have a 256 byte inode size, while previous versions used a 128 byte inode size. Perhaps arch uses the 128 byte inode size. Some (older) versions of GRUB can not read the newer 256 byte inode size file systems and will return GRUB Error 2.

If you think this might be your problem, then:

Boot from the Ubuntu 8.10 LiveCD. (It is important that it be the 8.10 CD.)
Then reinstall GRUB. Here are instructions [http://ubuntuforums.org/showpost.php?p=1308395&postcount=1](http://ubuntuforums.org/showpost.php?p=1308395&postcount=1).

If this does not work, then how about follow these instructions to run boot_info_script:
[http://ubuntuforums.org/showpost.php?p=6725571&postcount=3](http://ubuntuforums.org/showpost.php?p=6725571&postcount=3)
Posting the RESULTS.txt file will give us a much better view of your boot setup.

---

### Post by bodhi.zazen on 2009-03-02
you can either delete the uuid line and go back to 

root (hd0,x)
kernel /boot/vmlinux root=/dev/sdxy ro quiet splash

Or re-install grub to the MBR from Ubuntu

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

Or use chainloader or configfile

See also : [How to Multi-boot (Maintain more then 2 OS) - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=724817")

---

### Post by Slim Odds on 2009-03-02
> **dragos240 said:**
> Bump, i'm sorry, i really need someone to reply to this, i want my ubuntu back :(

a 12 minute bump.....

What kind of a place do you think this is?  :(

---

### Post by absolutezero1287 on 2009-03-02
> **Slim Odds said:**
> a 12 minute bump.....

What kind of a place do you think this is?  :(

I lol'd.

I used Ubuntu, then installed Arch and toyed with it for a while. I came back to Ubuntu cause its so much easier. As they say in the Arch forums...have you -Syu'd today?!!?!

```
sudo pacman -Syu
```

Also, try what the other members have suggested. If one of the method works please mark the thread solved.

---

### Post by dragos240 on 2009-03-03
> **absolutezero1287 said:**
> I lol'd.

I used Ubuntu, then installed Arch and toyed with it for a while. I came back to Ubuntu cause its so much easier. As they say in the Arch forums...have you -Syu'd today?!!?!

```
sudo pacman -Syu
```Also, try what the other members have suggested. If one of the method works please mark the thread solved.

Yes, but i couldn't use a package manager because i have a wireless connection.

---

### Post by absolutezero1287 on 2009-03-03
> **dragos240 said:**
> Yes, but i couldn't use a package manager because i have a wireless connection.

You should take the time to properly configure the wireless connection.

---

### Post by dragos240 on 2009-03-03
> **Slim Odds said:**
> a 12 minute bump.....

What kind of a place do you think this is?  :(

Sorry...

---

