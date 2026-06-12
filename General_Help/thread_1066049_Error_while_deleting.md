---
title: "Error while deleting"
date: 2009-02-10
forum: General Help
---

### Post by charlescarroll1 on 2009-02-10
I keep all my movies, music, etc on an external Western Digital 1TB hard drive.  Recently, I was transferring a movie from my laptop to my slave and the cable was disconnected during transfer. Now there is a 30MB portion of the movie on my slave and I cannot remove it I get this error message:

> Error while deleting.
There was an error deleting Lucky Number Slevin[2006]DvDri&#18934; AC3[Eng]-FXG.avi.
Error removing file: No such file or directory

Also, in the same directory, there are several file name characters that have been replaced with odd characters (like the "P" in the above file name) and cannot rename and get the following error message:

> The item could not be renamed.
Sorry, could not rename "Jurassic Park &#18934;.avi" to "Jurassic Park 3.avi": Error renaming file: Input/output error  

Does anyone know how I can fix this problem?

---

### Post by charlescarroll1 on 2009-02-11
One other thing, when I am in Windows XP, only a small portion of the files in that directory will load up.  

I have searched other posts and google, but couldn't find a solution.

---

### Post by alexjtb on 2010-01-14
I have just (January 2010) had the same problem. While copying an .iso file to my external hard drive (Maxtor 1.5TB), the process was interrupted after only 70MB, and I was left with:

1. The 72MB fragment of the .iso file, with one of its characters now a Chinese ideogram;
2. Two other files whose names now also bore a Chinese ideogram, which I could not rename; and
3. The other .iso file on my external hard drive was now "Lesvisiteurs.[Chinese ideogram]so", which was now as unreadable as its file extension...

When trying to a) delete the .iso fragment or b) renaming files, I ended up with "input/output" errors.

Rebooted in Windows, no problems there, and I was able to delete the fragment and (just in case) rename the other files and the .iso extension.

Rebooted in Ubuntu, and it was as if nothing had happened! Joy! :D

---

### Post by rulitawyn on 2010-10-27
Same problem i created a ubuntu server and hooked up a 2 tb Seagate external hd set up a samba share that i was accessing with my Ubuntu 10.10 meerkat laptop. I had placed a shortcut to the desktop linking to the media folder on my external hd. the hard drive still functions normally but the link on my desktop is broken and cannot be deleted it gives "Error while deleting. There was an error getting information about 'share_name on xxxx.volume'. The specified location is not supported"

---

### Post by gradysghost on 2010-10-27
It could be a little dangerous, but have you tried deleting from the terminal with sudo?

```
cd /path/to/drive/
sudo rm filename
```

/path/to/drive/ will probably be somewhere in /media

---

### Post by rulitawyn on 2010-10-27
> **gradysghost said:**
> It could be a little dangerous, but have you tried deleting from the terminal with sudo?

```
cd /path/to/drive/
sudo rm filename
```

/path/to/drive/ will probably be somewhere in /media

I tried deleating the link from /home/user/Desktop and got > rm: cannot remove `xxxx.volume': No such file or directory

also the external hd is not local to this machine it is attached via a ubuntu 10.10 server and set up through a windows network via samba. the drive and server are still accessible from my windows computers but i cannot mount any files from the server but the icon is still on my desktop from before when it worked but it cannot be unmounted or deleted in any way as the OS seems to claim its not there.

---

### Post by blueridgedog on 2010-10-27
Looks like it is time to run fsck on that partition (if it is other than NTFS).  If it is NTFS, I recommend doing it from within windows with chkdsk.  If you tell me how the partition if formated, I can suggest a method to check and repair it for errors.

---

### Post by gradysghost on 2010-10-27
> **rulitawyn said:**
> it is attached via a ubuntu 10.10 server and set up through a windows network via samba.

Ubuntu is the host for the Samba share?  Who knows?  Maybe there are some kind of Windows file permissions or something preventing you from doing this.  Perhaps see if the "boot to Windows to delete it" thing works.

---

### Post by rulitawyn on 2010-10-28
OK the file share_name on xxxx.volume is a link to the old mount point for my remote drive located on server xxxx i have 3 windows laptops and one ubuntu laptop that uses the server xxxx as a file/print server. the server is up and running 100% correctly on all 3 windows laptops (roommate's, gf's, mine) but on my ubuntu laptop I cannot delete the link that i had placed on my desktop. when i boot the ubuntu laptop from a live usb and navigate to the /home/user/Desktop directory on the internal (ext4) hard drive the link file is not present. however when i boot from the internal hard drive sitting right on my desktop is an icon that i cannot delete that doesn't seem to really exist. 

let me restate that the nfts 2TB hard drive that is attached to the ubuntu server, (labeled "xxxx" for the sake of this thread) is 100% operational on all three windows machine and the ubuntu laptop when booted from a live usb stick. The problem i am having is not with an actual file on the external hd but a problem on the internal hd on my primary Linux laptop with a shortcut that shouldn't still be there

---

