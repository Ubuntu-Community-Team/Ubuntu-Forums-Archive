---
title: "problem with SWAP - help a newb =("
date: 2009-03-24
forum: General Help
---

### Post by gorucan on 2009-03-24
Hello.

I just migrated from xp and win7 to ubuntu and i have a little problem.
I shrinked my 140gb disk where i am still triple-booting windows 7, and left 100gb for windows and 40 gb for ubuntu. I left those 40gb unused without any formatted partition, and i did all of this with gParted live cd. 

Then i reboot my comp and install ubuntu 8.10... where it prompted me for partition select it automatically wanted to split that 100gb partition into smaller one, but i in fact wanted it to use the free space i did with gParted. So i did it manually, formatted with ubuntu tool to ext3 and flagged with /boot

Now the problem starts... when i wanted to continue the installation, it reminded me i don't have any swap partition and that it could cause slower installation if my ram is kinda low. With my 2 gig of ram i thought it shouldn't be any problem then and i skipped warning...

Install went all well, actually i am already quite used to ubuntu and running a lot of extern applications and i also am starting to learn shell =) Just then i wanted to hibernate it... :s and it says there is no swap partition found...

Ok now direct question for you proffies.
I went to ubuntu community - swap FAQ
and entered this line in terminal:

sudo dd if=/dev/zero of=/mnt/512Mb.swap bs=1M count=4048

Now the big mistake is, when i copied this from browser, i wanted to change swap to 2-times of my ram but i only changed the number on the end and not the middle one as well ! Now i think this took 4,2 GiB of hard disk space somewhere and i have no idea how to find it !
it's not in swaps directory and not even [ls -la] shows it anywhere.

How do i undo this? 

And how could i make a nice swap partition of 4 gig?

Not that i need it so much but i would really like to use hibernate on the laptop...

Thanks for any help,
J.

---

### Post by joelswatson on 2009-03-24
hi gorucan,

sorry for hijacking your thread, but ive got 4gb of ram, how big should my swap partition be? cause ive heard is gb for gb, but then some have say 2gb should be enough.

thanks

---

### Post by anaconda on 2009-03-24
yep. you created a 4GB file with that command. and it is located in 
/mnt/512MB.swap  
I mean it is located in /mnt and the name of the file is 512MB.swap  If you want, you can change the name to whatever you want.. or you can delete the file.

Or make it to be swap with mkswap and swapon... like the swapfaq undoubtedly tells you to do.... 

And you dont really need a separate swap partition, if you forgot to create it.. the swap file is as fast as a separate partition. (It used to be slower, but now that it is directly mounted from the fstab it is just like any partition)

Actually swap files are better, becuase you can easily change the size of your swap files..

And "joelswatson" 
if  you have 4GB of RAM you won't be needing much swap.. I have 512MB ram and (1Gb swap) and the swap isn't used that much...  However it is good to have some swap.. (500MB-1GB should be enough in your case)  Or if you need to hibernate then you need more..

---

### Post by 3rdalbum on 2009-03-24
If you want to hibernate, you need a swap partition. Hibernation doesn't work on swap files.

---

### Post by 3Miro on 2009-03-24
My advice is to reinstall. Linux in generally needs 2 partitions, swap and / (not /boot). The recommended size for the swap is between the size of your RAM and double the size of your RAM. I have 4GB of RAM and 4GB of swap, hibernate works for me on my laptop and my desktop.

---

