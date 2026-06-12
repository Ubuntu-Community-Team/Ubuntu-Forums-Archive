---
title: "I/O error when copying VCD's to HDD"
date: 2006-09-09
forum: Desktop Environments
---

### Post by binary_goofy on 2006-09-09
[SIZE="2"]hi,
i'm using ubuntu 6.06 onto my system, am unable to copy any VCD's using a direct copy, paste onto my HDD but the VCD's play just fine. i don't think there's problems with the cd's itself as so many cd's cud not be bad, especially d ones i bought new and never watched before. also the same cd's copy fine in windows. using dd also gives an I/O error and terminates the copy. is there some sort of copy protection dat ubuntu has in place due to which this is happening? my drive is a 1 week old sony dru-820A, so i doubt there are probs with it. googling didn't bring up much. any suggestions?[/SIZE]

---

### Post by rykel on 2006-12-17
> **binary_goofy said:**
> [SIZE="2"]hi,
i'm using ubuntu 6.06 onto my system, am unable to copy any VCD's using a direct copy, paste onto my HDD but the VCD's play just fine. i don't think there's problems with the cd's itself as so many cd's cud not be bad, especially d ones i bought new and never watched before. also the same cd's copy fine in windows. using dd also gives an I/O error and terminates the copy. is there some sort of copy protection dat ubuntu has in place due to which this is happening? my drive is a 1 week old sony dru-820A, so i doubt there are probs with it. googling didn't bring up much. any suggestions?[/SIZE]

Hi,

It's true. It's a real pain to copy VCD's .dat files to the hard disk, unlike in Windows, where it's a drag-and-drop affair.

If you know the solution, please share, as I believe many of us are booting into Windows just to copy the DAT files over. Not good.

---

### Post by manmath on 2007-11-27
But, there is always a way in Linux. You can try the following tricks to copy VCDs onto your HDD.

I copy the disc to the hard disk as a raw/iso (dd if=/dev/cdrom of=/tmp/image.iso) then I use vcdgear to extract the dat to mpg:

vcdgear -raw2mpg /tmp/image.iso movie.mpg


This is pretty much the method I would recommend as well, the one change I would add is that I use readcd as it handles copying from the CD medium much better than dd, IMHO.

"vcdgear -fix -cue2mpg" has been reliable in extracting a working mpg from a standard image file set.

Just tried with DD and had an issue. readcd is a good tool, I prefer cdrdao myself and this command line should get you a lovelly bin/cue to use vcdgear on:

cdrdao read-cd --device ATA:1,1,0 --driver generic-mmc-raw --read-raw image.cue

Change the device for whatever is your reader!

OR

install readvcd and then 

# readvcd 2 > mv.mpg

OR

Install vcdimager
# vcdxrip

OR

install cdfs
mount -t cdfs /dev/cdrom (or whatever your drive is) /home/movie (or whatever your destination)

---

