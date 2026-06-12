---
title: "ext4 issue??, this is real wierd"
date: 2009-06-19
forum: General Help
---

### Post by Sui Nim Tao on 2009-06-19
HI all,

i need a real guru for this one, it's a real stange one and it's a bit chicken or egg, I do not know if the issue is with ubuntu on ext4 or whether it's a php issue, it could go one of two ways.

I posted a help topic on the phpmyadmin site, to see if they could answer this, so i'm posting it below to see if you guys can help, as this is spooky.

below is what i posted on their forum

> HI, 
 
I use a one of the classes unzip.lib.php in an open source CMS solution. 
 
As the unzip class is open source, I use the file in my software to unzip files that are uplaoded for things like addiing plugins to the system. 
 
now this one has had me spooked for a while, but i finally tracked it down. 
 
If I create a zip file using windows or linux(ubuntu) upload the file, extract the contents of the zip and then save the files, the files all appear ok. 
 
now I just bought a new computer, I have ubuntu iinstalled using ext4 partitiioning, now for some reason if I create a zip file on this new pc, then upload them unpack them and save them, the files are currupted. 
 
It is not the zip being currupt, as i can unzip this manually and it's fine, it's not the upload as i can unzip the upload and it's fine. it's not the file saving as i can look at the data before saving to a file and it's currupted. 
 
So to sum it up, if i create a file on linux using ext4 i can unzip the file ok manually, i can unzip it on ubuntu using ext3 fine, but when i try to unpack the data using the php class the data gets currupted. Now i have tried this with other zip files created on ubuntu with ext4 and they too all show currupt , but when I try files created on ubuntu with ext 3 or windows they work fine. 
 
My question 
 
Is there possibly a bug in the class unzip.lib.php that is currupting files when unpacking them if they are created on a linux system using ext4, these files unpack fine on any pc, just fail with this class. 
 
any help would be good, as this could effectively give errors to people using phpmyadmin and uploading manually created zip files for restore. 
 
thanks 
 
Paul 

---

### Post by kerry_s on 2009-06-19
ext4 is still broken, the fix is in kernel 2.6.30, avoid ext4 till then.

---

### Post by Sui Nim Tao on 2009-06-19
Hmmm, thats about what i figured, it was just sort of spooky how it was happening, i guess at the end of the day I should have held back an used ext3, i should know better, i'm not exactly new to this stuff.

I thought new comp so i'll give it a try.

ah well looks like ext3 is prob the way to go, at least till the next few kernel releases to ensure no issues.

Will be interesting to see if the new kernel solves this or not..........

Paul

---

### Post by sgosnell on 2009-06-19
The .30 kernel has been out for some time...

You can find it [here](http://kernel.ubuntu.com/~kernel-ppa/mainline/).

---

### Post by WIGGMPk on 2009-06-19
> **kerry_s said:**
> ext4 is still broken, the fix is in kernel 2.6.30, avoid ext4 till then.

I have been using ext4 on my system since Jaunty's launch with no issues. I heard people having issues and also heard people (like me) who have no issues to speak of. I wouldnt exactly say its 'broken'.

---

### Post by Sui Nim Tao on 2009-06-21
Ok this just got weirder, I made a choice and decided as the new lappy had not had much use, I decided to reinstall on ext3, guess what the issue is till happening.

So on my system, acer aspire one d150 if i create a zip it is still currpted when extracted using the php class unzip.lib.php from the phpmyadmin project.

If i create a zip on my eeepc900 or fujitsu lappy, the files are unzipped using this class ok.

No the zip files can be manually unzipped on the lappy, and there fine it's just this acer aspire, and it only has issues with the php class.

So is this an issue with the zip, tool, it's the default one that comes with ubuntu, right click and create archive, or is this an issue with the php class, i'm it is certainly not ext4 as I am on ext3 now and this install is just about the same as the one on the eeepc.

i'm really confused now............

Paul

---

