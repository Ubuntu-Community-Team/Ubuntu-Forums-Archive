---
title: "Lucid...   Disappearing DVD Drives and Dropped Mount Points..."
date: 2010-09-01
forum: Desktop Environments
---

### Post by casparov on 2010-09-01
Hi, Everyone... 

I am using 10.04 and am trying to be a good Linux convert, but my experience w/ the long-term release is not nearly as good as it was in Karmic. 

I am experiencing the dropping of my DVD drives (a Samsung and an ASUS) after initial booting (usually) upon opening the browser and running any kind of embedded media. In other words, two separate DVD discs, say, sitting in the drives will be recognized in the file system, and within Movie Player, for ex., and will play upon booting and upon restarting the PC. But their appearance often is nullified if I do not first, at least, play both of them for just a few seconds. Sometimes, after playing them in this way, their appearance will remain for the remainder of the session; other times they are gone. 

This problem is a known bug, but I have no solution: [https://bugs.launchpad.net/ubuntu/lu...ev/+bug/554433](https://bugs.launchpad.net/ubuntu/lu...ev/+bug/554433) . It seems to me that this should not be taken lightly, as it influences a major competence in the OS: the ability to recognize devices. Lucid is much less stable for me than Karmic. 

Has anyone heard of this, and does anyone have an idea for a solution?

Thank-you to those who read and to those who reply, C.

---

### Post by buntunub on 2010-09-01
This used to happen to me back in the 7.04 days and even then it was just a minor annoyance. Haven't seen it happen since. If it does just pop a terminal and type

```
sudo mount /dev/cdrom /media
```

(or sr0, or whatever your drive is)

Your drives are there and probably still mounted, but for whatever reason the desktop icon just dropped most likely. You can also check to see if they are mounted with

```
ls -a /media
```

---

### Post by casparov on 2010-09-01
Buntunub...  

Thanks so much for your reply. 

Your suggestion at terminal produced this: mount: /dev/sr0: unknown device; your suggestion for the media listing command produced this: .  ..  floppy  floppy0  .hal-mtab-lock

I have't got a clue about the second result, but the first indicates (I think) that the DVDs/CD-ROMs are not recognized.  

At the beginning of the current session (which has lasted hours) both devices were recognized, and the discs contained therein were noted.  I then launched both disks to, sort of, cement them within the system session (which sometimes works), but everything disappeared a bit later.  (I had launched into the Web, also, but played no media.)  

You are stalwart in that this was simply an annoyance for you in Gutsy (?), but this problem has necessitated countless restarts and freezes in disc playback.  Everything just vanishes...  

Once again, thanks so much,   C.

---

### Post by wkulecz on 2010-09-02
There are annoying issues with the automatic device naming in 10.04, it change with updates as to which drive SATA or IDE is sda or sdb :( and frequently ignores my BIOS boot loader selecting of the boot drive.  I've had to install grub2 on all my drives to get reliable reboots :(

I only have one Optical drive and don't use it much these days -- CD burning was broke for a good while but a recent update seems to have fixed it last time I tried.

Sorry, I don't have a solution, but I too find this very disconcerting in a LTS release, especially since it was never an issue in 6.06 or 8.04.

---

### Post by casparov on 2010-09-02
wkulecz...

OMG, someone who understands!!!  

Yeah, wkul, it is very frustrating that, when I thought I was doing the right thing by upgrading to a more stable platform, I was actually entering the abyss when it comes to some basic OS requirements.  I never would have abandoned Karmic had I known about this.  There is no sense in a long-term release, which is much less reliable than the intermediate release it replaced.  This is the kind of thing that scares people away from Linux, and here I was trying to evangelize for it...  

I do feel that Ubuntu is worth fighting for--there are times when I am really satisfied w/ it--but this issue makes it hard to use, at times.  For instance, in this session, even w/ a reboot, I cannot get my DVD drives to be recognized, at all.

Thanks for your reply,   C.

---

