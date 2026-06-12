---
title: "unable to resize ntfs with unbootable windows"
date: 2009-02-16
forum: General Help
---

### Post by zorkerz on 2009-02-16
So I have had this happen on a few friends computers already. Basically something goes wrong with windows so it cannot boot (sometimes this will require a reinstall or just the recovery console). The solution is to install ubuntu while leaving the windows partition and its data intact.

Booting into a live ubuntu works fine but the installer and gparted cannot resize the ntfs windows partition.

If I try to mount the partition I get an error about it not being safe because windows shut down improperly (sorry I don't have the exact wording). The error provides a command to force the mount which allows perfect access to the partition. 

Is there any way to resize the partition from ubuntu?

I cannot delete the partition or boot windows.

---

### Post by HermanAB on 2009-02-16
The best way to repair broken Windows, is with a CD bootable Windows.  Use BartPE for this type of open heart surgery, not Linux:
[http://www.nu2.nu/pebuilder/](http://www.nu2.nu/pebuilder/)

Cheers,

Herman

---

### Post by dzark on 2009-02-16
The "cannot mount because of improper shutdown" is because the computer was switched off, crashed, etc, instead on unmounting the disk cleanly at the end... Generally okay to follow the supplied command and reset the 'improper shutdown flag'

Once it's cleared, you'll be able to mount it...


To resize, i use 'gParted' (System -> Admin -> Partition Editor). However you cannot edit partitions that are mounted, so make sure you unmount first (eject button next to the drives name in the file explorer)

---

### Post by zorkerz on 2009-02-17
Thanks for the replies. Fixing windows is not my problem I know how to do this. Many people don't have windows cds or only have OEM ones that don't do the recovery console. I find after having windows crash most people are interested in doing a dual boot so as to have a backup os.

I have unmounted the partition. In gparted I can click the resize/move button but it does not allow me to make the partition any smaller even though it has a number of gigs of free space. Do I need to do anything to reset the improper shutdown flag or does this happen automatically after using the supplied mount command?

thanks again

---

### Post by dzark on 2009-02-17
defrag ;)

---

### Post by troublescoot on 2009-02-17
> **zorkerz said:**
> So I have had this happen on a few friends computers already. Basically something goes wrong with windows so it cannot boot (sometimes this will require a reinstall or just the recovery console). The solution is to install ubuntu while leaving the windows partition and its data intact.

Booting into a live ubuntu works fine but the installer and gparted cannot resize the ntfs windows partition.

If I try to mount the partition I get an error about it not being safe because windows shut down improperly (sorry I don't have the exact wording). The error provides a command to force the mount which allows perfect access to the partition. 

Is there any way to resize the partition from ubuntu?

I cannot delete the partition or boot windows.

I have this exact same problem! Thanks for posting.

---

### Post by zorkerz on 2009-02-17
dzark: how do you defrag from ubuntu? Again windows is currently unbootable.

---

### Post by dzark on 2009-02-17
Try booting windows, pressing F8 to get the boot menu, and booting to command prompt.

From there, 

```
chkdsk c: /p /r
defrag c: -f
shutdown -s
```

That'll scan the disk, defrag, and shutdown. After that you should be able to resize an UNMOUNTED disk with gParted. If not, please post error message.

Other alternative would be to boot live CD, plug an external harddrive in, copy over all important data (C:\Documents And Settings\..) and nuke the whole windows nightmare for good. What do you really need to keep? Photos, emails, etc..

---

### Post by zorkerz on 2009-02-17
Sorry dzark the whole point of this is that windows is **unbootable** which I have stated in every post. 

My ultimate goal is to be able to install ubuntu on peoples computers when windows borks itself without destroying windows or loosing data so that they have the freedom in the future to fix windows and have a dual boot system.

Backing up data is definitely a possible solution here however most people do not have easy access to a large enough external drive. Plus the invasiveness of destroying the current partition and borked windows install scares away a large number of people.

---

### Post by HermanAB on 2009-02-17
Well, like I said above, use BartPE to fix the HDD.  You cannot do that with Linux.

Cheers,

Herman

---

### Post by zorkerz on 2009-02-17
Oh im sorry I completely missed that part. Looks like another good solution but it appears its essentially the same as having a windows cd around (get me if im wrong here).

I was hoping to find some solution that did not require anything windows (ideal only live ubuntu).

What I don't understand right now is why I can mount an ntfs partition and read/write to it but cannot resize it. 
What could prevent the resize if the partition appears to work fine?

---

### Post by dzark on 2009-02-17
> **zorkerz said:**
> Sorry dzark the whole point of this is that windows is **unbootable** which I have stated in every post. 


Yes i understand that. But you have also mentioned recovery console which is something that you need.

Ubuntu isn't a magic silver bullet to fix a broken system. You can do a lot, but if you want to try and repair a broken windows system, use a Windows Live CD, such as BartPE or @Active or .. or ..

To try and take a broken windows system, install another OS on it, and then try to fix windows later is just plain asking for problems. Real messy problems. Fix windows first, _then_ install another OS. If you can't fix it you'll have to accept that it is broken and make the choice whether to reinstall windows or not.

Sorry if i come across harsh, but i too have spent many a time with broken windows and no harddrives to backup to. Backups are important. Photos are important. Emails are important. Word documents and spreadsheets are important. Warez software, MP3s, movies etc are NOT.

---

### Post by dzark on 2009-02-17
> **zorkerz said:**
> 
What I don't understand right now is why I can mount an ntfs partition and read/write to it but cannot resize it. 
What could prevent the resize if the partition appears to work fine?

That the partition is fragmented. There is data on the start and the end of the partition with bits of space inbetween. Like a book with a whole bunch of empty pages somewhere in the middle. If we re-arrange the book, so that all the empty pages are together at the end, then we can put in a new chapter :)

---

### Post by zorkerz on 2009-02-17
Ya i understand where you are coming from here. For me at least repairing windows is of minor importance I know how to do that. Usually I encourage people to reinstall windows once their data is backed up anyways to start fresh. My real motive here is to get someone to try out ubuntu.

Fixing the broken system is not the goal. Installing ubuntu without furthing breaking the system is.
For example a file on my friend's old dying dell has been corrupted making windows unbootable. He does not have dell cds and is not going to ask dell for them so he will never be able to access his recovery partition. I could not resize his main partition so our solution was to delete the 3.5 gig recovery partition and install ubuntu there. This gives him access to all his data, a working ubuntu, and leaves him the option to fix windows if he ever wishes. 

I like your book analogy. The fact that the partition can be mounted, all the files can be accessed, and the amount of free space is know, should i think mean that all the free space could be moved to one side of the partition and chopped off to make a new partition for ubuntu. For some reason this does not appear to be the case. I obviously only have rudimentry understanding of how filesystems work but I have not found a good explenation for this inability to resize. 

thanks for sharing your knowledge

elias

---

### Post by dzark on 2009-02-17
An excellent use of the recovery partition to 'recover' the usefullness of the computer! hahah

Without getting into specifics, book analagy is pretty close.. pages are around 1-4Kb.. So on a 30gig drive there's quite a few of pages.

Try [http://www.ubcd4win.com/](http://www.ubcd4win.com/) - It'll let you boot & defrag without the need for recovery cds. Always should keep a windows live cd next to your linux live cd - it (still) is the most popular OS in the world. 

Still, leaving broken windows on there seems pretty strange. If it's broken, either fix it or throw it. Otherwise it'll end up wasting a lot of valuable harddrive space no?

---

### Post by zorkerz on 2009-02-17
Oh i agree its silly to leave a broken windows around. He had not been using his computer for weeks and was waiting for somebody to get him an xp cd. I had ubuntu on a usb key and told him I could give him a working os. Although the only wasted space is on his 55 gig windows drive is windows itself and installed programs (quite a number of gigs come to think of it) all the rest of his data he can access and use now.

I wonder if I could get a usb key with ubuntu on it and UBCD or something else that would allow me to fix windows. I can't carry cds around with me cause i break them. The less I carry around the better but I do love having ubuntu on a usbkey you never know when it might come in handy.

---

### Post by dzark on 2009-02-17
[http://lmgtfy.com/?q=Windows+xp+live+usb&l=1](http://lmgtfy.com/?q=Windows+xp+live+usb&l=1)

:)

---

