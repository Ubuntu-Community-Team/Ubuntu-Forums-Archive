---
title: "Completely Wiping A Memory Card?"
date: 2009-05-15
forum: General Help
---

### Post by phantomjoker on 2009-05-15
I am selling a memory card which had information i would not like the buyer to access on it.

I have deleted the files, but know that is not the end. How do i completely remove all traces of the file?

This is a solid state memory card - so nothing too demanding as i dont want to corrupt it.

Cheers

M

---

### Post by Slim Odds on 2009-05-15
You need to create a data file that writes to the entire device.

---

### Post by phantomjoker on 2009-05-15
ok, and how would i go about doing that?

---

### Post by kanikilu on 2009-05-15
Check out the **secure-delete** package. How-to: [http://www.techthrob.com/2009/03/02/howto-delete-files-permanently-and-securely-in-linux/](http://www.techthrob.com/2009/03/02/howto-delete-files-permanently-and-securely-in-linux/)

---

### Post by phantomjoker on 2009-05-15
ok. Cheers.

But now i have another problem - i cannot seem to mount my memory if the partition editor is open, and cannot open the partion editor if the memory is mounted. If i try and delete the files i get the following error -

Error while deleting.

Error removing file: Read-only file system

And it doesn't delete anything.

Whats going on?

---

### Post by phantomjoker on 2009-05-15
ignore the above. How do i find out what the name of the volume is called for use with the shred action?

/media/memory (which it says it is called) does not work...)

cheers

---

### Post by Brandon Williams on 2009-05-15
While you know the filesystem is mounted, on the command line, run 'mount | grep /media/memory'. This should tell you the device name (e.g. /dev/sdb1) for the device that is mounted as /media/memory.

Then, run 'umount /media/memory' on the command line. Don't unmount in a graphical file manager, since they typically will make sure the removable device is fully disconnected when you unmount the filesystem.

---

### Post by barraclou on 2009-05-15
Overwrite everything (to delete your data forever), then format your card.

---

### Post by Slim Odds on 2009-05-16
> **barraclou said:**
> Overwrite everything (to delete your data forever), then format your card.

WRONG!!!

Formatting touches very little of the card.

You have to write data to **every sector** on the card to make sure that you **overwrite** any important data that was on the card.

---

### Post by HuckleSmothered on 2009-05-16
> 
Quote:
[QUOTE]Originally Posted by barraclou
Overwrite everything (to delete your data forever), then format your card.
WRONG!!!

Formatting touches very little of the card.

You have to write data to every sector on the card to make sure that you overwrite any important data that was on the card.[/QUOTE]

Uhm, that's exactly what barraclou said. Overwrite everything, and *then* format.

---

### Post by Slim Odds on 2009-05-16
> **HuckleSmothered said:**
> Uhm, that's exactly what barraclou said. Overwrite everything, and *then* format.

My apologies... I misread his statement.

I'll be more careful next time......

---

### Post by pauna on 2009-05-16
> **phantomjoker said:**
> 
I have deleted the files, but know that is not the end. How do i completely remove all traces of the file?

This is a solid state memory card - so nothing too demanding as i dont want to corrupt it.


An useful command is "shred", which is installed by default. While the manual talks about overwriting "files", you can also use it to devices in /dev/, just unmount the file system first.

Example command: sudo shred /dev/sda1 -f -v -z iterations=1

---

### Post by phantomjoker on 2009-05-17
yup, cheers. 

I eventually used shred. Takes forever, but works.

Cheers guys

---

