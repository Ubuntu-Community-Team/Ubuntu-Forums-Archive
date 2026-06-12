---
title: "Tool for renaming ISO images (internally) ??"
date: 2009-01-28
forum: General Help
---

### Post by inspired on 2009-01-28
Hi folks,
I am trying to find a comprehensive ISO image manager for Ubuntu / Linux.

On windows I am used to apps like UltraISO.

On Linux I've found numerous apps for managing ISO mounts points, and for making ISOs, but nothing like UltraISO when it comes to managing the actual content of an ISO. The main thing I want is the ability to rename the image name. This is not the name of the ISO file, but rather the "disk" within the ISO. For instance, when one mounts an ISO file it will use this image name for the disk name of that mount point.

In UltraISO there is a command for changing the image name, without having to extract and resave the data.

Apps I have tried are:
AcetoneISO2
GISOmount
gmount-iso
ISO Master
Furius ISO

As far as I can tell, none of these allow me to change the "disk" name within an ISO.

Any fingers points me in the right direction would be greatly appreciated.

Perhaps there is a command line method for what I want to do? That would suffice. Using fuse for instance. Please advise.

With much thanks,

Jonathan

---

### Post by bulletxt on 2009-01-29
You'll have to use genisoimage command from terminal and read the manual. It can do that almost for sure.



anyways maybe this can help:


-V volid
    Specifies the volume ID (volume name or label) to be written into the master block. There is space for 32 characters. Equivalent to VOLI in the .genisoimagerc file. The volume ID is used as the mount point by the Solaris volume manager and as a label assigned to a disc on various other platforms such as Windows and Apple Mac OS.
 
-volsetID
    Specifies the volume set ID. There is space for 128 characters. Equivalent to VOLS in the .genisoimagerc file.

---

### Post by inspired on 2009-02-05
> **bulletxt said:**
> You'll have to use genisoimage command from terminal and read the manual. It can do that almost for sure.

anyways maybe this can help:

-V volid
    Specifies the volume ID (volume name or label) to be written into the master block. There is space for 32 characters. Equivalent to VOLI in the .genisoimagerc file. The volume ID is used as the mount point by the Solaris volume manager and as a label assigned to a disc on various other platforms such as Windows and Apple Mac OS.
 
-volsetID
    Specifies the volume set ID. There is space for 128 characters. Equivalent to VOLS in the .genisoimagerc file.
Thanks a lot. I will try this out.
Regards,
Jonathan

---

