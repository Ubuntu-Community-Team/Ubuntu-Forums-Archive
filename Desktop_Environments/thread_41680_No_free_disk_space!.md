---
title: "No free disk space!"
date: 2005-06-14
forum: Desktop Environments
---

### Post by jhk on 2005-06-14
Last night, I ran a script that would download and compile Enlightenment- I've already had a copy compiled and installed, but I wanted a newer version.  This morning I woke up, and saw that my computer was turned off.  Somebody in my house must of turned it off.  Now, when it boots up, I can't log in to anything in GDM because it complains that there's no free disk space, and when I log in to a virtual console and run df it indeed reports 0% on my Linux partition.

Now, this is very odd, because I remember checking yesterday and seeing that I had 60% free- around 17 gigs.  Also, there's  difference  of about 600mb between the total volume and the amount used in df, yet it reports 0 blocks available.

Where did this all go?

I've tried removing all the trash folders I could, but that didn't change anything in df.  I tried removing a few big ISO files I had laying around, and that didn't change anything.  

I can still reboot into Mac Os X, but I actually prefer Linux.

I'm stuck!

Can anyone help me?  Thanks!

---

### Post by Xian on 2005-06-14
My first thought is that it is probably located in your /tmp directory.
Empty that and see if this frees up some space.

---

### Post by jhk on 2005-06-14
[QUOTE=Xian]My first thought is that it is probably located in your /tmp directory.
Empty that and see if this frees up some space.[/QUOTE]
 Nope, I've already tried that.  There's nothing in /tmp.

---

### Post by skoal on 2005-06-14
In alot of circumstances like these, there's a file still left open with some daemon feeding it from a net socket, like giFT or another P2P client.  I'd check the temp folder for any huge . (hidden) files, or even your home configuration directories (which are also . - hidden).

I've seen huge 4-5 gig files before when one of these daemons is left open before or has not exited cleanly.  Try to hunt down the source of the "bit feeder" with:

du -sh <path>

Try that on the key paths like /tmp, /usr/local, and /home.  For example,
```
wormdirt@morpheus:///tmp $ du -sh /home/wormdirt/
21M     /home/wormdirt/
```
* If you get hugh numbers in your $HOME directory, then you can narrow down the search by looking at individual . directories - for example,
```
wormdirt@morpheus://~ $ du -sh .mozilla/
20M     .mozilla/
```

\\//_

---

### Post by Xian on 2005-06-14
Just use the following du command to see the space in all your directories and then narrow them down as needed. It should be obvious almost immediately:

```
$ sudo  du -sh /*
```

Here is my output:
```
$ sudo du -sh /*
3.1M    /bin
6.8M    /boot
0       /cdrom
2.8M    /dev
37M     /etc
8.0K    /FAT
4.0K    /fedora
4.0K    /gentoo
3.2G    /home
4.0K    /initrd
0       /initrd.img
70M     /lib
48K     /lost+found
12K     /media
4.0K    /mnt
4.0K    /ntfs
4.0K    /opt
452M    /proc
7.9M    /root
9.2M    /sbin
4.0K    /srv
4.0K    /storage
4.0K    /suse
4.0K    /susehome
0       /sys
104K    /tmp
2.0G    /usr
151M    /var

```

---

### Post by jhk on 2005-06-14
[QUOTE=skoal]In alot of circumstances like these, there's a file still left open with some daemon feeding it from a net socket, like giFT or another P2P client.  I'd check the temp folder for any huge . (hidden) files, or even your home configuration directories (which are also . - hidden).

I've seen huge 4-5 gig files before when one of these daemons is left open before or has not exited cleanly.  Try to hunt down the source of the "bit feeder" with:

du -sh <path>

Try that on the key paths like /tmp, /usr/local, and /home.  For example,
```
wormdirt@morpheus:///tmp $ du -sh /home/wormdirt/
21M     /home/wormdirt/
```
* If you get hugh numbers in your $HOME directory, then you can narrow down the search by looking at individual . directories - for example,
```
wormdirt@morpheus://~ $ du -sh .mozilla/
20M     .mozilla/
```

\\//_[/QUOTE]
 Aha!  

I have 23 gigs lurking in /var, so that's the problem.

How should I handle this?  Can I just delete everything in /var, or would that bork up my system?

Thanks for the help, skoal.  And Xian!

---

### Post by Xian on 2005-06-14
[QUOTE=jhk] Can I just delete everything in /var, or would that bork up my system?
[/QUOTE]
Major bork. Do as skoal suggested and narrow it down further.

---

### Post by jhk on 2005-06-14
Okay, the 23 gigs are in /var/log/mol.1.log.

That's over with.  Phew.  

Mac-on-linux must be extremely buggy if it dumps 23gig log files around...  It's too bad that it seems to be dead.

Thanks for the help.

---

### Post by Xian on 2005-06-14
This usually happens when there is a sudden power failure and the system makes a major file dump at that time. Are your sure that someone actually powered down your box?

---

### Post by jhk on 2005-06-14
[QUOTE=Xian]This usually happens when there is a sudden power failure and the system makes a major file dump at that time. Are your sure that someone actually powered down your box?[/QUOTE]
 Yeah, I'm sure somebody powered it down.  MOL wasn't running when it was shut down.  I ran it last night then stopped it but I didn't come across any problems afterward.  Odd.

But, on the bright side, I have a bleeding-edge version of e17 on my computer now.  :)

---

