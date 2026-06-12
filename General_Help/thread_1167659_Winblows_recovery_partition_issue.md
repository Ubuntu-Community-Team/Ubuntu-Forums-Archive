---
title: "Winblows recovery partition issue"
date: 2009-05-23
forum: General Help
---

### Post by linuxfanboy on 2009-05-23
Not sure this belong in this section or on this forum at all lol...Move/delete if it doesnt.

I want to start from scratch and wipe my hd clean and setup dual boot system...

In windows disk management...There is this partition on my hd, its NTFS  its 1.6gb, it has no letter (unnamed) and its hidden. In status it says Status healthy(unknown partition). It says it has 500mb free on it. It doesnt have the usual options on it when you right click, ity just has delete.

Is this that winblows recovery partition? While back I installed program that lets you mount cds like isos but it required seperate partition with bunch of space on it to operate. It was around the same size as this unknows partition. I think that partition did have name but not sure. Anyway that program isnt installed anymore but I may have had uninstall issues with it....

Long story short, is there a way to make sure this hidden partition is the windows partition? Obv I cant open it cos its hidden to see. How can I see whats on it?

Windows xp seemed to have some ability to heal itself lots of times lol....like when smth when wrong it could repair and work fine on reboot...then when viruses or major issues struck, I could just open new profile and everything would be ok on it....

Where does this healing ability come from? Is it from the recovery partition or from system restore? My other drives seem to have system restore on them.....i see the files during scans etc....not sure if theyre used.

Ive read bit about this recovery partition and looks like you need to get into safe mode and then repair windows....which I havent done....not as I remember anyway....

So does windows use that partition actively or is it smth that only I can access manually? To my knowledge I havent used the option to restore it from safe mode....so if its not used by windows itself then I see no point in it taking up space.

Thanks for the help.:popcorn:

---

### Post by Liolikas on 2009-05-23
Insert Linux liveCD start **gparted** if do not find it in menu just try command in terminal **sudo gparted** or just **gparted**.
In that program you can manually prepare partitions change settings like hidden etc.
---
You can download only gparted liveCD here if do not want to download entire big Linux distribution cd: [http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

---

### Post by linuxfanboy on 2009-05-23
> **Liolikas said:**
> Insert Linux liveCD start **gparted** if do not find it in menu just try command in terminal **sudo gparted** or just **gparted**.
In that program you can manually prepare partitions change settings like hidden etc.
---
You can download only gparted liveCD here if do not want to download entire big Linux distribution cd: [http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

tnx for the link.

I wanna do a clean wipe of the entire hd 

Lets assume this is the windows recovery partition....Does windows use that partition actively or is it smth that only I can access manually? Afaik I havent used it....so if its not used by windows itself then I see no point in it wasting hd space.

Looking up windows recovery partition didnt help...I mentioned few points in my previous posts from stuff Ive read...No data about this on microshaft's site either.

If smone knows more about it lemme know.

---

### Post by Legace on 2009-05-23
The recovery partition is used to reinstall Windows incase you screw up Windows.

However, if you have a Windows installation CD/DVD, you don't need that recovery partition, and you can safely delete it :)

---

### Post by linuxfanboy on 2009-05-23
> **Legace said:**
> The recovery partition is used to reinstall Windows incase you screw up Windows.

However, if you have a Windows installation CD/DVD, you don't need that recovery partition, and you can safely delete it :)

Thanks, afaik Ive never used it. So without me initiating it by going in safe mode or other stuff....it just stays there doing nothing? I had that useless dead space on my hd for years now lol.

---

### Post by NHArticleTen on 2009-05-23
Some brief notes:

Perhaps I've missed your post stating your specific hardware and current OS(es) and other assorted software.

Part of receiving accurate assistance from other users is to provide them with all the pertinent information.

Note that this is not a mandatory requirement, but it does help the next thousand people with the same questions(when they attempt to google their problems away).

So, for the sake of assumptions and assuming, let's say you have a Compaq or Dell(both do/did the hidden stuff).

Dell ships computers with a generic OEM windoze reinstallation disk that DOES NOT contain the specific Dell-hardware-specific-drivers. When you get your new Dell and first boot it up, you are given the opportunity to do a one-time back-up copy/rescue disk that DOES contain everything specific to your machine and system.

Other than this disk which would be specific to your machine, there is a hidden partition containing the same back-up image which(supposedly) could be used to "reset" the main partition's contents back to "day one" by using "control and F11" right after the POST.(this procedure is beyond the scope of this particular post but the interwebs abound with varied stories relating to this).

Dell also sometimes used a small hidden FAT partition for their machine-specific diagnostics which, if removed, may affect the operations of some Dell-specific diagnostic software/functions.

In your specific situation where you want to retain the original OS and dual-boot, these hidden areas may give you extra headaches(say you reduce the size of the main partition to add an extended partition and somehow change the drive to where the hidden partitions are "lost" or "misplaced").

My thoughts would be to clone the drive with something(clonezilla?) that will "do" the hidden partitions also(you might want to save the MBR separately using something like MBRtool).  Then get your windoze cleaned up, optimized, and defragmented(Ccleaner, Eusing Registry Cleaner, Hijackthis, etc).

After those operations you might even do another back-up clone(your discretion obviously).  Then you'll attempt to reduce the size of your main partition so you have space for an extended partition where you create BOTH a linux partition AND a swap partition(equal to 1.5x your ram).

At this point in my recommendations I'd strongly suggest that you download the latest Puppy Linux and Damn Small Linux.  Both are Live-Run, both do a good job of detecting and running *nix-compatible hardware, and they will give you additional VALUABLE insight into the wonderful world of *nix.

Damn Small Linux is...well...damn small...50mb small...damn!  It's lean and mean and easy to re-install when you "break it" while experimenting/learning WITH A DEDICATED MACHINE FOR THIS PURPOSE...MOST CERTAINLY NOT YOUR MAIN/DUAL-BOOT MACHINE!

Puppy Linux is 100mb and it is the disk I reach for first when I'm checking out other machines.  It has Gparted so you can learn/experiment with partitioning quite easily(without loading up the latest huge-by-comparison Ubuntu offerings).  I have successfully used Puppy with a 2004-vintage laptop containing an internal wifi transceiver but your mileage may vary.

Get yourself another machine that someone else was finished with and giving away or selling for a few dollars and enjoy the many flavors of *nix!

---

### Post by NHArticleTen on 2009-05-23
> **Legace said:**
> The recovery partition is used to reinstall Windows incase you screw up Windows.

However, if you have a Windows installation CD/DVD, you don't need that recovery partition, and you can safely delete it :)

It should be noted that MANY machines ship with a generic windoze re-installation disk that DOES NOT contain your specific equipment drivers.  The "hidden" "factory" back-up image DOES contain an exact image of your system as it was when it left the building with Elvis.

So...

If you've deleted those hidden partitions...don't sweat it(too late now)...

If you need specific drivers then you can probably download them from the OEM website(maybe even updated ones).

---

### Post by linuxfanboy on 2009-05-23
> **NHArticleTen said:**
> It should be noted that MANY machines ship with a generic windoze re-installation disk that DOES NOT contain your specific equipment drivers.  The "hidden" "factory" back-up image DOES contain an exact image of your system as it was when it left the building with Elvis.

So...

If you've deleted those hidden partitions...don't sweat it(too late now)...

If you need specific drivers then you can probably download them from the OEM website(maybe even updated ones).

I have regular desktop not lap and I have cds with drivers for the MB and graphic card so I dont think its an all around package in there...

Can I use ubuntu's live cd to "take a look" in there? its a hidden partition....

If I use mount on that partition....it should just read it and not use it as swap or install ubuntu on it, correct?

---

### Post by NHArticleTen on 2009-05-23
> **linuxfanboy said:**
> I have regular desktop not lap and I have cds with drivers for the MB and graphic card so I dont think its an all around package in there...

Can I use ubuntu's live cd to "take a look" in there? its a hidden partition....

If I use mount on that partition....it should just read it and not use it as swap or install ubuntu on it, correct?

I noticed Ubuntu wouldn't "see" or "mount" hidden partitions from the live-run condition...

psssst-hush,hush...{{Puppy Linux does though}}

---

### Post by linuxfanboy on 2009-05-25
Deleted all partitions including this restore partition (probably) I had... Now it looks like Im missing the space thats around same size as that restore partition....

So I delete all partitions and I create one big one for windoze.... I install windoze there. I figure I can always resize it when I install ubuntu...I cant resize or change it....opened thread about it in installation. tnx for the help here people.

[http://ubuntuforums.org/showthread.php?t=1169448](http://ubuntuforums.org/showthread.php?t=1169448)

---

