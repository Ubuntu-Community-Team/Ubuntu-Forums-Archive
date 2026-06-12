---
title: "File transfer, UNIX -&gt; LINUX"
date: 2009-05-20
forum: General Help
---

### Post by Arppa on 2009-05-20
Hi everyone!
I have an old HP unix machine (HP-UX 8.0 and HP 9000 Series 382) and I need to transfer some files somehow to my linux machine. The unix machine doesn't have a LAN port (it has RS-232) and the files are too large for a floppy disk. I have a tape drive available, though I'm not sure how to get it working under linux nor unix. The unix isn't networked. Is it possible send the files via RS-232 and if it is possible, what prog I'd have to do it with or do I have to write my own prog for the task.
All suggestions are appreciated, thanks!

---

### Post by StuartN on 2009-05-20
> **Arppa said:**
> I need to transfer some files somehow to my linux machine. The unix machine doesn't have a LAN port (it has RS-232)

You could have a look at GKermit, a GPL version of the Unix Kermit package. It is available in the Ubuntu repositories and there is a manual at [http://www.columbia.edu/kermit/gkermit.html](http://www.columbia.edu/kermit/gkermit.html)

---

### Post by sedawk on 2009-05-20
A few comments ...

Setting up the RS232 connection (e.g. with a null modem cable) so
you can use your Linux box as a Unix-terminal (or vice versa) is
one thing, but transfering files over this connection is another.
This procedure heavily depends on what software exists on your
HP-UX box ( e.g. something like rz/sz).
I guess downloading and compiling extra software on
that HP box is out of question anyway (opening pandora's box ...).

I once connected two PCs in the pre-LAN era using RS232 to transfer
files. This was slower than copying files via 1.44-floppies, so I gave up
and did it with floppy disks!
If files are too big (e.g. a (compressed) tar archive) you can
split that archive using "split" (is "split" installed on HP-UX?)
and on Linux you can concatenate the files again using "cat".

If you can get hold of (old) SCSI hardware, you can try to insert
a (cheap) SCSI-adapter to your Linux box (with connectors compatible
with the cable in your HP box if any). Then you can
connect the disk of the HP box directly to your Linux box
(compatibility? Can Linux read the file system?).
Or you additionally get hold of an external SCSI tape or 
SCSI disk and connect it first to your HP box and after copying
you connect the external SCSI device to your Linux box and
recover the data. 

Or you can buy a compatible old LAN card for your HP box, which might be
the easiest solution if your HP-UX detects that hardware
out-of-the-box and has a proper TCP/IP implementation.

How much data do you want to transfer? Is there any
good compression tool on the HP-UX box (like gzip) so you
can compress the data first?
Does your Linux box have a floppy drive or do you have to buy
one first ?-)

---

### Post by dstempfley on 2009-05-20
Wow a step back a few years.  

If you have tapes and they fit the files, I'd plug in the drive just to see if it works right away.  You might be surprised.  If not, scrap that it's a lot of headache to make old hardware work.

Get a null mode cable and setup up the serial communications between the two hosts.  The baud rates, error correction, etc. must match.  As for the transfer there's lots of options.  The effort will depend on whether this is a one time thing or will happen all the time.
 
Method 1. The ugliest method which I would try first is to setup a listener, then blast the file over the port. (install sharutils on the linux system) 

    On the linux: setup receiver
        cat </dev/ttyS0 | uudecode

    On HP:  send file
        tar cf - | gzip | uuencode file.tgz > /dev/cua0

     *note you might need to test betwee a /dev/tty? and a /dev/cua? device.  I think one has flow control settings for serial consoles.  

It's quick and ugly, it might work.

Method 2. You can connect kermit to both sides and do a kermit transfer.  I never liked this solution, but it works and is generally easy to setup with software supported on both sides.  The HP probably has kermit already use ckermit on linux.

Method 3. You can set up a serial console on one side, log in and use zmodem (available in lrzsz).  You setup rz on the receiving end, then use sz to send the files.  You need lrzsz on both sides. If your setting up the terminal on the HP, you'll need to modify /etc/inittab (or launch a single getty by hand). On the linux side look at upstart and /etc/event.d.  I've setup more terminals with inittab then upstart but it's probably just as easy.

Method 4. If you'll need to do this transfer a lot, then you should look at setting up a ppp/slip connection between the two computers and then using ftp or ssh to transfer the files.

Almost forgotten method:  If you have the same hardware bus for drives, i.e. SCSI, then pull the hard drive from the HP and see if you can mount it on the linux system.  Problems to consider are whether linux has the filesystem support for the disk format on the HP.

Hope it helps,

/Dion

---

### Post by Arppa on 2009-05-21
Thanks for the replies!

sedawk:
The HP-UX box doesn't have anything special installed on it, only the standard tools and programs. I'm not sure whether it has sz/rz, I'll have to check it when I get back to the office. And yes, downloading new software is unfortunately out of question.
The files' overall size is about 50 megs and largest single files are about 5 megs.
I like the idea about connecting the unix hard drive to linux, but I'll have to find out if I can mount the unix file system in linux (I'll have to check what fs it uses too).
The linux box has a floppy drive.


dstempfley:
I have available tapes that are large enough to fit the files but I haven't gotten them working yet on the unix box and I'm not sure how to read tapes on the linux machine.
I'll try method 1 and check if the ftp/ssh -option is possible.

I'll get back to you when I run into problems.
Thanks very much you have been very helpful!

---

### Post by dstempfley on 2009-05-22
If you get the tape drive to be recognised, then using it should be straightforward.  Use the mt command to manipulate the tape, check it's status, and eject it.  

You should be able to tar the files to tape "tar cvf <tape device> files"
and then extract them on the other side.

/Dion

---

### Post by sedawk on 2009-05-22
If I remember right HP-UX does not have a tar that supports "z" option
(compression with gzip). Check if you have at least gzip.

1) Get 3-5 floppies
2) Create a tar file containing all important files
3) compress that file with gzip if available
   (I know a download site for pre-compiled HP-UX stuff, but they
    not not even list HP-UX 10.20 anymore, so getting a a working
    gzip for your box seems difficult ...)
4) split the tar archive with "split" into files of size 1.4 MB 
5) Copy first file to first floppy
6) Copy second file to second floppy while restoring the first
   floppy on the Linux PC
7) as 6. but reuse floppies after copying them so that both
   floppy drives can work in parallel.

8) After copying all 1.4 MB files to Linux "unsplit" them with "cat"
   and then check that "frankenstein-ed" tar archive with tar tvf or
   tar tvfz if it is compressed.

I think this is the fastest and easiest solution for 50 MB of date.

It is boring work, but should take less than 90 minutes and you
do not have to mess around with cables, screws, tapes, electrocution,
whatsoever.

---

### Post by txcrackers on 2009-05-22
You could always pull the HD out of the HP machine and put it in the Linux machine (provided the interfaces are compatible).

Almost anything you do come up with will be easier than trying to tie two serial ports together...

---

### Post by Arppa on 2009-05-25
Ok guys, I ripped the HD (Quantum ProDrive 425S) out of the HP box and attached it to the linux box. Unfortunately linux complains:

$ fdisk /dev/sdc
Device contains neither a valid DOS partition table, nor Sun, SGI, OSF disklabel.

I could always try to fix the partition table, but the HD has to work when I'll put it back to the HP.

The file system on the HD should be hfs (according to 'sam' on HP) which should be supported by the linux kernel. (?)

---

### Post by Arppa on 2009-05-25
Turns out that the file system on the hard drive is ufs ("file -s /dev/sdc" revealed this). It mounts without errors/warnings with:

$ mount -r -t ufs -o ufstype=hp /dev/sdc /mnt

but when I try to 'ls' it's contents I get:
ls: reading directory /mnt: Input/output error

What can cause this error? :?

---

### Post by Sef on 2009-05-25
>  The file system on the HD should be hfs (according to 'sam' on HP) which should be supported by the linux kernel. (?)

Found a [thread]("http://www.insanelymac.com/forum/index.php?showtopic=3577&hl=hfsplus") on another site that says [Knoppix]("http://knoppix.com") can acess hfsplus, so likely it can access hfs.  I would download it and see if it works for you.

---

### Post by sedawk on 2009-05-25
Hello!

Good to hear that you are able to connect the SCSI disk
to your Linux box!
(So you have a Linux box supporting SCSI? Than it
 might be easy to connect a DDS/DAT Tape to transfer the data!).

It might be a good idea to create a backup of the hdd with "dd"
so you can unplug it again (many things can be done with that 
backup instead of risking data damage on the real disk).

I read that Linux does support HFS, but not HP's partition tables,
so you might have to find out about the partition layout
of your disk (reconnecting the disk to your HP box?).

Further read:

[http://osdir.com/ml/linux.debian.ports.hppa/2002-07/msg00047.html](http://osdir.com/ml/linux.debian.ports.hppa/2002-07/msg00047.html)

---

