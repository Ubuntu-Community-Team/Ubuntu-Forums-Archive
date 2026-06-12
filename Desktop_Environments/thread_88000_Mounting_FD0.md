---
title: "Mounting FD0"
date: 2005-11-09
forum: Desktop Environments
---

### Post by WBC on 2005-11-09
I am having a lot of trouble trying to use the floppy drive from command line.
I tried to access it by: ls fd0
I then thout that it was not mounted so typed: sudo mount fd0
That did not work either?
I looked it up in the man files and tried everything that was there and looked it up on Google and anything elase I could find.
No Success :( 

I am using Ubuntu Breezy Badger

Please, help anyone.

WBC

---

### Post by Kyral on 2005-11-09
Try

```
mount /media/floppy
```

---

### Post by canadianwriterman on 2005-11-09
This worked on mine....

[QUOTE=paddyg]the bug fix has been available for some time now.

you've got to enable---for once (then comment the line)--- the following dapper repository in /etc/apt/sources.list

```
deb http://archive.ubuntu.com/ubuntu dapper main restricted
```

then just use synaptic to download and install

pmount 0.9.6-1

PS: on my box it works fine![/QUOTE]

---

### Post by Kyral on 2005-11-09
Ahhh!

Don't go Dapper unless you know what you are doing. I meant if mounting it on /media/floppy doesn't work, go ahead and use his fix, but then disable the Dapper Repo. Dapper is still in development and breakage is going to happen. Just a word of caution

---

### Post by canadianwriterman on 2005-11-09
[QUOTE=Kyral]Ahhh!

Don't go Dapper unless you know what you are doing. I meant if mounting it on /media/floppy doesn't work, go ahead and use his fix, but then disable the Dapper Repo. Dapper is still in development and breakage is going to happen. Just a word of caution[/QUOTE]

You're quite right, Kyral. Perhaps this is a better option for fixing pmount that doesn't involve opening Dapper repositories:

Go to Web site: [http://archive.ubuntu.com/ubuntu/pool/main/p/pmount/pmount_0.9.6-1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/p/pmount/pmount_0.9.6-1_i386.deb) . This will download the file pmount_0.9.6-1_i386.deb

Then, in a Terminal window, type:

 **sudo dpkg -i pmount_0.9.6-1_i386.deb**

After installing this fix for pmount, you'll be able to open "Computer" and right click on the floppy icon and select "mount" or "unmount" successfully.

---

### Post by WBC on 2005-11-09
[QUOTE=canadianwriterman]You're quite right, Kyral. Perhaps this is a better option for fixing pmount that doesn't involve opening Dapper repositories:

Go to Web site: [http://archive.ubuntu.com/ubuntu/pool/main/p/pmount/pmount_0.9.6-1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/p/pmount/pmount_0.9.6-1_i386.deb) . This will download the file pmount_0.9.6-1_i386.deb

Then, in a Terminal window, type:

 **sudo dpkg -i pmount_0.9.6-1_i386.deb**

After installing this fix for pmount, you'll be able to open "Computer" and right click on the floppy icon and select "mount" or "unmount" successfully.[/QUOTE]
I am using Ubuntu Breezy Badger 5.10 which is a server and command line only(as far as I know).  I just need floppy0 to work in command line,  do I still follow your instructions?
Thanks,
WBC

---

### Post by canadianwriterman on 2005-11-09
[QUOTE=WBC]I am using Ubuntu Breezy Badger 5.10 which is a server and command line only(as far as I know).  I just need floppy0 to work in command line,  do I still follow your instructions?
Thanks,
WBC[/QUOTE]

I'm not familar with using Breezy as a server and not sure whether mounting through the command line uses pmount. Certainly you wouldn't need to get the graphical interface for mounting and unmounting working.

Does anyone else know whether the fix to pmount impacts mounting through the command line?

---

### Post by WBC on 2005-11-09
[QUOTE=canadianwriterman]I'm not familar with using Breezy as a server and not sure whether mounting through the command line uses pmount. Certainly you wouldn't need to get the graphical interface for mounting and unmounting working.

Does anyone else know whether the fix to pmount impacts mounting through the command line?[/QUOTE]
More information:
I tried this command: **sudo mount -t vfat /dev**
and got this response.....
mount: mount point /floppy does not exist

I also tried: **mount /dev/fd0 /mnt/floppy**

-----------
I hope this helps,  I have a dead system here until I get some things sorted out.  Maybe the best idea would be to just keep using my SUSE fileserver for the time being and wait until the documentation is further along.  I just find it surprising that I can't get the floppy to work?
I will keep checking this thread to see if anyone has the answer.  After a few days of this I am tired. 
Thanks,
WBC

---

