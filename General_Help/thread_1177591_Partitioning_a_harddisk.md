---
title: "Partitioning a harddisk"
date: 2009-06-03
forum: General Help
---

### Post by Ampi on 2009-06-03
Hello everybody,

I am not entirely sure where to post this, hence the general help. Excuses if I am wrong..

I love Ubuntu and use it on all my computers. But tomorrow I'm getting my new, and with that my fastest, computer with 500GB of Harddisk. 

I want to partition it, which until now I have never done, I always have used multiple harddisks using the entire disk as an entire partition. Easy..

My problem now is the following. I have heard that partitioning a single harddisk is best only doen once (is that correct??).
Ad so I am really thinking about the partitions.

I would like to have Ubuntu as my main OS.
I also would like to use Windows XP for one or two programs that don't run on linux. 
And maybe some space for a third (linux) OS to play with :).
And then of course my home-partitition and a DATA-partition.

Any ideas how I could split the 500 GB best?? WIth all this freedom I don't know what to do...

---

### Post by merlinus on 2009-06-03
My suggestion:

primary partition, first on the hdd - 20G for xp.

extended partition for rest of space - 480G.

logical partitions within the extended, formatted as ext3:

15G /
20G /home
440+G /data
1.5G /swap

then at some point you will easily be able to divide /data into as many logical partitions as you wish without messing anything up.

these figures will vary some because formatting and journalling will take up space.

---

### Post by munky99999 on 2009-06-03
Well first get GParted.

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

Next get Virtualbox or vmware or something similar.
[http://www.virtualbox.org/](http://www.virtualbox.org/)

That should do the job for you.

This way you can simply use the hard drive u have as space etc etc. Virtualization is far more efficient.

The only reason to truly dual boot is for 3d acceleration. Virtualization just doesnt have it. Thusly no gaming.

---

### Post by kestrel1 on 2009-06-03
> **merlinus said:**
> My suggestion:

primary partition, first on the hdd - 20G for xp.

extended partition for rest of space - 480G.

logical partitions within the extended, formatted as ext3:

15G /
20G /home
440+G /data
1.5G /swap

then at some point you will easily be able to divide /data into as many logical partitions as you wish without messing anything up.

these figures will vary some because formatting and journalling will take up space.

I would second that setup, but I will also mention that if you want to use other OS's you could take a look at VirtualBox. You don't need to partition the drive for this as it is software & enables you to use other OS's as virtual machines. A very good way to try out other distro's.

---

### Post by ajgreeny on 2009-06-03
> My problem now is the following. I have heard that partitioning a single harddisk is best only done once (is that correct??).Where did you hear or find this comment?
I wouldn't like to say it's utter rubbish, but I have partitioned my main hard disk, and changed the partition sizes on it, no end of times without any apparent problems whenever I have added test installs of other linux distros, eg Fedora, Mint, Mandriva, etc etc.  I suppose it is possible that continuous partitioning and installing of OSs may eventually weaken the drive, but no sign of it at the moment after 5 years use and play.  Every time you do it is also a potential data loss action, as well, though with gparted, the only software I've ever used, that has never happened to me either.

---

### Post by Ampi on 2009-06-03
thanks!!!!

[LIST]
[*]Actually, I heard it via via, hence my question...
[*]My main OS will be Ubuntu not Windows, why Windows it's own partition? And is 15GB enough?
[*]I want to start from Ubuntu making all the partitions from there, is that possible?
[*]Where can I read about logical partitions?? Is it as 'viable' as 'real' partitions??
[/LIST]

Seems like I still have a lot of questions... ;)

---

### Post by Ampi on 2009-06-03
Oh one other thing about the virtual box. I actually only need one or two programs in windows, so maybe I can do that Virtually?? I have never done that before... But then I would only make logical partitions...

Sorry, I am still not entirely clear on the subject, but that's what the forum for!

---

### Post by merlinus on 2009-06-03
FWIW, not all windows programs will run in a VM.  I have one that does not; hence the need for dual-booting.

And with so much hdd space available, you might as well create the partition, even if only 10G, as it will be very difficult to do so down the line.

---

### Post by lisati on 2009-06-03
> **merlinus said:**
> FWIW, not all windows programs will run in a VM.  I have one that does not; hence the need for dual-booting.

And with so much hdd space available, you might as well create the partition, even if only 10G, as it will be very difficult to do so down the line.

But isn't that half the fun, figuiring out what will work and what won't work?

---

### Post by kestrel1 on 2009-06-04
I have not had a problem running programs in a vitrual environment under Windows, but I would suggest that you try it out first. If the program is heavy on graphics you could get in to problems & you want to allocate as much memory to the VM as possible without making your host OS (Ubuntu) too low on memory. If you have 2gb of ram then I would use 1gb for the VM, leaving enough for Ubuntu to run the program.
If you decide that you would prefer a dual boot then you really want to install Windows first then Ubuntu unless you are happy to play around to get grub back on the MBR.

---

### Post by Ampi on 2009-06-04
haha, it isn't have the fun that is true, but I have been waiting for over a year to be able to run this program... so the fun for me is gone! 

Well, then. The main idea is then two partitions, one for windows and one for the rest. Let's say 15G for Windows (or should I go for 20G??). Then the rest of the 485 GB could have, as stated by merlinus

20G /home 
20G /
1.5G swap
445+G /data

(1) What is the 20G / ?? I would guess this is the root, but is it containing Ubuntu?

(2) And more importantly, can I do all this from the Ubuntu Live CD? Because the partitioning of /data I can do later. But the main partition and the extended partition have to be done inmediately so I can install Ubuntu and use the computer.

(3) Another important question, why is windows the main partition? That makes it sound the most important partition while it is the one I will use once in a while and Ubuntu on the extended partition every day. Or has it to do with the type of partition?

BTW. Thanks guys!

---

### Post by merlinus on 2009-06-04
windows needs to be in a primary partition, and usually likes to on the first one on the hdd.  It has nothing to do with importance. 

The / partition is where the ubuntu operating system and your apps live.  /home will contain settings and configurations for your apps.  Data is where your personal files can be stored.

You can partition in advance using the live gparted disk, or during install.  You will probably have to select manual at the partititoning screen.

I think it best to set up all the partitions at once.  It will make for less work and fiddling around afterwards.

---

### Post by Ampi on 2009-06-04
thanks, those are very clear answers!

So the difference between using Gparted and the Ubuntu cd is that after finished with Gparted I will only have partitions, right? 
Meaning when installing Ubuntu afterwards I only need to choose the right partition. 
There is no real difference in use or quality for these two?

---

### Post by merlinus on 2009-06-04
Correct.  You can d/l the gparted .iso from

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

Burn it as a disk image, and boot from it.  Then you can point the ubuntu install to the partitions you have set up.

---

### Post by Ampi on 2009-06-04
Thanks I just did that, so as soon as the computer arrives..

I am reading about the partitions and I am starting to understand it :). The are two things I don't really understand yet. 

Primary Parttition is the advantage of more than one primary partition. 
I read when you have multipe primary partitions, only one can be active at a time. I know that when I have only one primary partition I still have to reboot to change OS. 

Does one primary partition simply mean I can access all my directories and files on the primary/partition-combo from any OS on that primary/extended-partition-combo? 
Therefore with two or more primary partition I 'really' divide the computer?

I would make something like
hda1 PP: Windows 15G
hda2 empty
hda3 empty
hda4 EP
hda5 LP: / 20G
hda6 LP: /swap 1.5G
hda7 LP: /home 20G
hda8 LP: /data 445+G

How does it work if I want to partition /data even more, is it going to be simply more partitions like hda9 or is it a subdivision?

Thanks again :)

---

### Post by Gina on 2009-06-04
Simply use GParted to Resize the data partition to give some free space (easiest at the top) then use the free space to create a New partition (or partitions).  I've done that many times :lol:  You can create the free space at the bottom instead but that means GParted has to move all the data up and that takes a long time.

Just one point about Windows...  Not sure what the current situation is but many suppliers used to supply Windows already installed and an image on CD-ROM of the installed system rather than a standard Windows install disc. This means you can only re-install Windows to the entire drive, wiping everything!  Not helpful! But if you have a standard Windows install CD-ROM then you can wipe the drive and set it up with GParted system disc.  Then install Windows.

However, if you only have a factory re-install CD-ROM you will need to do what I did with my last laptop - resize the Windows partition (which occupied the entire drive).  This was with XP and I presume your new machine will have Vista which may be a bit different.
With a new machine all the data should be at the beginning of the drive, leaving all the free space following.  In this case you can just use GParted system disc to resize Windows (leaving some headroom for installing software in Windows) and the use the rest as has been discussed.

BTW...  On my P4 desktop I allocated 20GB for XP and am currently using 15GB.  With 500GB available it would be wise not to crowd it too much - defragmenting needs space to work for instance.  And allow space to install Windows software.

EDIT...  Sorry, just checked your OP and you did say XP so please ignore my comments about Vista.

---

### Post by cycling-rod on 2009-06-04
You may find the how-to's here of interest: [http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=1](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=1) Scroll down to Related Stories for variations on Vista/XP and Ubuntu dual booting.

---

### Post by Ampi on 2009-06-06
All good advices!

(1) When installing Ubuntu, do I choose 'install them side by side, choosing between them each start up' ??
Ubuntu is the first one to install, there is no other OS yet, how do I make sure Ubuntu chooses the partition I made for it and doesn't change the ones I have?
(2) After partitioning I got the message 'Verifying DMI pool data' and the computer hangs. So apparently something went wrong partitioning I guess. I 'only' made new partitions, the ones we discussed before. Does the HD need anything more to be read? Extra unallocated space? A partition table (I am not really sure what it is)? A starting point to read from?

---

