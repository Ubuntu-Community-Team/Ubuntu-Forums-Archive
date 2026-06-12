---
title: "Burn a 4.4 GB file?"
date: 2007-05-02
forum: Desktop Environments
---

### Post by xlinuks on 2007-05-02
Hi,
I have Kubuntu 7.04 with 1GB of RAM and K3B 1.0 and I'm trying to burn a file of 4.4GB onto a DVD of 4.7 GB but K3b keeps saying that:"It is not possible to add files bigger than 4.0 GB" and I don't know what's the matter.
Is there any workaround?

---

### Post by vedace on 2007-05-02
The problem is that optical media manufacturers are sneaky.  DVDs that claim to fit 4.7 GB of data can actually only hold 4.37 "Gigabytes".  The problem comes from naming conventions: DVDs hold (1024) * (1024) * (1024) * 4.37 bytes of data, or (2^10)^3 bytes of data, which is actually about 4.7 billion bytes, and thus, 4.7 Gigabytes.  However, computers function in binary, not decimal, and storage units are in a base-2 numbering system.  A new system of binary prefixes was accepted by the IEEE in 2005 that eliminates the ambiguity by referring to what was commonly called a Gigabyte as a Gibibyte; Megabytes became mebibytes, etc.  There's more information [here]("http://en.wikipedia.org/wiki/Binary_prefix"): 

So, in short, nothing's wrong.  Burn a smaller file.  Another problem you're likely to encounter when burning files larger than 2.0 GB is that you can't use the ISO CD format anymore, you must use UDF.  Although that isn't the problem here because the file is just too large for the disk.

---

### Post by xlinuks on 2007-05-02
Thank you for the detailed information.
I have a matroska video file (.mkv) so I can't manage to get it burned, and I guess I can't split it (split & merge on the target computer would be too painful) and burn it onto 2 DVDs, so the best thing I can do is probably rip it (If I find such a ripper).

---

### Post by IanW on 2007-05-02
Xlinux - Can your DVD burner use Dual Layer discs?

Alternatively, install "mkvtoolnix" from Synaptic. This contains a program called "mkvextract", which is the ripper you're looking for.

---

### Post by xlinuks on 2007-05-02
Well thanks
I decided to rip it (before I saw your suggestion about 'mkvtoolnix') and found in the net the 'alltoavi' command line tool which seems to work, I started it with "alltoavi "/media/sdb2/torrents/" mkv 0 0 650 DIVX50 640 480" and it started working, it's done ripping 5% by now, I will report whether it completed succesfully. I'm a bit confused by the size of this tool - 20KB (yes, twenty KB). Time will show.. btw it's already 10 % done.

ps: I'm xlinuks

update: ripped succesfully

---

### Post by sdcrym on 2007-05-04
I have this same problem, and it is** not** because the file is too big for the disc.  I suspect this is also the case for the OP. The problem has something to do with how Linux is handling my DVD burner, but I don't know enough to be able to say what.  I'm able to burn the same files perfectly in Windows.  It's just a huge pain to reboot everytime I want to burn something.  I'm still looking into the problem, but I'll post back if I ever figure it out.  If anybody else knows anything, please let us know.

---

### Post by Saubazi on 2007-06-21
I have the same issue and it is not about lack of disk space on DVD and the solution
is not UDF system. K3b currently won't allow burning larger files than 4GB period.
A google search will provide some controversial information about the issue. I saw
claims about kernel limiting UDF to 4gig and couple of other explanations as well.

I hope there is a solution to this issue I am still looking with search...

---

### Post by kuja on 2007-06-21
Perhaps you can find a way to split the file into 2+ pieces. The 4gb file limit may be a limitation of the UDF file system.

---

### Post by freak_lick on 2008-01-27
This is problem with ubuntu not k3b or something else!
I used k3b in other distros and burned .mkv files which are 4.37 GB in size.
Just dont understand why is this problemn with ubuntu???

---

### Post by freak_lick on 2008-01-27
I have updated k3b to 1.0.4 (added gutsy-backports updates) and now i can burn files larger than 4GB...
cool

---

