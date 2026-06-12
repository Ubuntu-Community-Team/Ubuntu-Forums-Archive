---
title: "What am i doing wrong..."
date: 2006-06-05
forum: Desktop Environments
---

### Post by Uhospaghetto on 2006-06-05
nOOb here... 

i have one 80gig HD, did fresh install of winxp prof x32 - then did ubuntu install x64 - when all said and done, ubuntu reboots and it says error finding system... why is this?

---

### Post by Rackerz on 2006-06-05
What is the exact error? Is it grub error 17? How are your drives setup?

---

### Post by Uhospaghetto on 2006-06-05
error cannot find operating system, this is the error - it doesnt boot into anything... this comes up right after bios loads... thats it... right now i went in and fixmbr so that i could format the drive again, and im going to reinstall windows, using the x32 install instead of the x64, im sure this wont work but i guess i want to figure this out, any suggestions...

Spagg

---

### Post by vanlol on 2006-06-05
This happened to me the first time I attempted to install but quit the installation while I was in the partitioning disks (step 4 or 5 I think) stage. I don't remember specifics but after cancelling I restarted the computer and was greeted with an error finding system message after BIOS.. eep .. /fixmbr won't do anything to help there..

So 1 windows re-install later and then attempted to install ubuntu again..

make sure you partition correcty.. 

1 big extended(logical with partition magic) partition (you can do this with Partition Magic in windows if you really want, I did then I did the rest of the partitions in ubuntu) after the windows partition then 2 logical partitions inside the extended partition (or 3 for /home),

make sure you make the root partition greater than 2GB or the partitioner will bug on you no matter how many times you delete and remake it .. which will require a restart of the live cd to fix (why... -_-)

---

