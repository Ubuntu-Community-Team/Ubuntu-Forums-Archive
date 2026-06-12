---
title: "Backup main hard disk over the lan to a share"
date: 2009-01-15
forum: General Help
---

### Post by jms1989 on 2009-01-15
Hello, My mom has HP Pavilion dv7-1135nr laptop that I'm trying to backup vista so I could restore it in the future if a major problem occurs. There are no recovery disks.

I want to use dd to do it but I don't know how to send the results over the network. I need to backup 50GB of data to my external disk but its formated to fat32 and is the only one with enough space. I also need to somehow split it up in dvd sized portions so I can burn it to dvds. I want to do this so if we ever need to recover a file, we could mount it as a loop device and fetch the files.

I know its possible but I just don't now or not sure how.

---

### Post by cariboo on 2009-01-15
I would suggest using a program that is designed to do what you want, like partimage. Partimage is available in the repositories and it will do what you need. It has one huge advantage over dd, it will only archive the data nad not the empty space on the hard drive. Partimage also works on a network.

Have a look at the [Partimage]("http://www.partimage.org/Main_Page") page for more info.

Jim

---

### Post by jms1989 on 2009-01-18
I gave partimage a look and a test drive. It's NTFS support is experimental. I need something that will let me backup a ntfs partition. I like how partimage works but poor ntfs support and the lack of the ability to recover individual files is not good. I need both. 

Backing up the files separately is not desired as I want to be able to save the partition to a set of dvds and retain the ability to recover individual file.

---

### Post by theWrkncacnter on 2009-01-18
Could you use scp to backup all the files from the ntfs partition to your network share? Then you could use any dvd burning software to burn all the files that will fit.

---

### Post by virtuallinux on 2009-01-19
Well, dd will certainly work, but it will most likely take quite a while.  If you have the network share mounted, you can have dd output to a file on the share. It works something like this:

dd if=/dev/sda1 of=/media/share/backup.img

where sda1 is the partition you want to backup, /media/share is the path to the share you have mounted, and backup.img is the clone of sda1 (the partition we're backing up).  For example, I have a network share mounted as /media/common.  I have windows installed on /dev/sda1. So, It would look like this:

dd if=/dev/sda1 of=/media/common/backup.img

The name "backup.img" is completely arbitrary, you could name it "VistaBackup" just as easily.  To restore this later, you would need to have an empty partition at least as big as the one you backed up. If this partition was /dev/sda3, then restoring the partition would work like this:

dd if=/media/share/backup.img of=/dev/sda3

---

### Post by HermanAB on 2009-01-19
The fastest network transport is netcat "nc".  You can use dd and netcat with gzip like this:

If you are impatient (and who isn't?), then make the dd block size bigger, with the 'bs=1M' parameter. It will speed things up a bit - or at least, it will make you believe that it speeded it up a bit...

Sending gigabytes of zeroes accross a 100MBps network can take a long, long time. Therefore, it is a good idea to compress the data before sending it with netcat, since most of the hard disk is usually empty. Remember to unzip it before writing it back. This will make a huge improvement in the backup time.

Save image

On the server:

# nc -l -p 50000 | dd bs=1M of=pc.img

On the PC:

# dd bs=1M if=/dev/hda | gzip -9 | nc servername 50000

Restore Image

On the PC:

# nc -l -p 50000 | gunzip |  dd bs=1M of=/dev/hda

On the server:

# dd bs=1M if=pc.img | nc pc.ip.addr.ess 50000

Because of the bs parameter, dd may not stop by itself. Eventually you will notice that things stopped, but dd is still running and netcat is still waiting. To stop it cleanly, press ctrl-C on the sending machine. The other side will then shut down too.

More details here:
[http://aeronetworks.ca/netcat-howto.html](http://aeronetworks.ca/netcat-howto.html)

Cheers,

Herman

---

### Post by AJExtreme on 2009-01-19
Have you tried using "Arconis"  it is an image software for windows, not sure how it would do for linux, or even vista, I used it with Win XP, Outstanding job. Just image the entire drive if you intend to put it back on if things don't work out right for your changes.  It will restore your hard drive back to it's previous state with all hardware.  Like nothing had changed.  One of the things I use with Windows when doing multiple computers with the same hardware config.

---

### Post by jms1989 on 2009-01-20
Thanks for the replies. Originally I was going to use dd to backyp the laptop but since someone said it would also copy the zeros in the partition too, it made it less desired. Supposedly, it could also backup actually data and only record the zeros in metadata thus keeping the resulting file smaller than the source disk.

netcat sounds good but it still used dd. How can I make dd only copy the real data and skip the zeros. I have 74GB of free space on the share and the partition is about 55GB used of 222GB. I've thought about copying the recovery partition but that'll add about 9GB making the image 64GB in size. Would I really need the recovery partition or can I leave it out?

I know I can use Acronis to back it up, I've used it several times. I can backup 50Gb in an hour to a usb disk. I want to make this a learning experience and have it serve as a resource for others wanting to do the same thing.

---

