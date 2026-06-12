---
title: "Enable boot booster for the eee pc in linux"
date: 2008-12-30
forum: General Help
---

### Post by myusername on 2008-12-30
This how to is to show you how to enable boot booster on the eee pc for faster boot ups.
this involves partitioning and it can really mess up your system if done wrong so USE AT OWN RISK!

1. partition hard drive
open up gparted (or any partition manager you're comfortable with) on the first PRIMARY partition (this is very important) create a 16mb partition with the type set as "Do not use". it doesn't matter where just as long as its on the first partition

2. open terminal

3. formatting partition
type sudo cfdisk /dev/THEPARTITION (mine was sda7)
then use the left and right keys to select "TYPE" and for the type select EFI and press enter then select "Write" then exit

4. naming the partiton
run sudo sfdisk --change-id /dev/THEPARTITION ef in the terminal (FORTHE DEVICE use this format e.g. sda7 = sda 7 notice the space between sda and 7)

5. Enabling bootbooster
reboot computer and press F2 till you get to the bios setup. go to boot and enable bootbooster. then save changes and exit . AND YOU'RE DONE!

if i missed something just tell me

---

### Post by tomsimmons on 2009-04-25
I've just finsihed installing 9.04 Remix on my 901, and I'm impressed.

However, when it starts up is says that Boot Booster can't be used this time, using normal boot.  I know that this extra partition isn't on my drive, I had to go and remove the swap that had been created during install, so I know that I'm down to a single partition.

Why doesn't it (or at least an option for it) perform this boot boost partitioning during install?

What kind of improvement in speed do you see?


Tom

---

### Post by KhaaL on 2009-04-25
I just wanted to add that I used another method that worked, taken from [URL="http://forum.eeeuser.com/viewtopic.php?id=25178&p=2"]eeeUser forums 
[/URL]. it was originally written by kazuni but i modyfied it a bit.

[I]
[INDENT]
boot into linux and enter the terminal
type "fdisk /dev/sda"
press p and hit enter.
you should be able to see a list of tables, like these:

/dev/sda1 * 1 488 3919828+ b W95 FAT32

Yours may be different depending on what you already have on the disk. make a new partition by typing "n"

command action will come up

press "p" for primary partition
then press 4 
(this will create a primary partition as sda4)
once that's done, press p again
you should see this table now:

/dev/sda1 * 1 488 3919828+ b W95 FAT32
[COLOR="Red"]/dev/sda4[/COLOR]  489 490  16065 [COLOR="Red"]83 Linux[/COLOR]

(the values may be different, but the most important thing is highlighted in red)
now, you have created a partition /dev/sda4 at the end of your first ssd. now you need to change its type into efi.
in the prompt, press t, then 4, then "ef" (without quotes)
then p again to see this:

/dev/sda1 * 1 488 3919828+ b W95 FAT32
[COLOR="Red"]/dev/sda4[/COLOR]   489 490  16065[COLOR="Orange"] ef EFI (FAT-12/16/32)[/COLOR]

the oranged part indicate changes from the past display

once that's done, **press w to write the modification to the partition table** or your changes will be lost.
reboot and then you're done![/INDENT][/I]

I will modify this further and post it to the ubuntu wiki ( [https://help.ubuntu.com/community/EeePC/Using](https://help.ubuntu.com/community/EeePC/Using) )

---

### Post by MaxFactor on 2011-11-11
The method described by myusername was easier to use compared to the plain fdisk /dev/sda because it is menu based and you don't need to be a root.

Thanks!

---

### Post by maulynvia on 2012-01-16
I struggled to get this fdisk solution described here [https://help.ubuntu.com/community/EeePC/Using]("https://help.ubuntu.com/community/EeePC/Using") to work, but did succeed in the end. Here are my tips:

1. I used GParted from the Lubuntu live CD, this was straightforward

2. When running fdisk, make sure this is as sudo (on the live disk ubuntu is user name and password is blank)

3. Setting the size of the partition was confusing - but then I could neither figure out the relationships between MB, MiB Sectors and Blocks nor find the right way to create the suggested 8MB partition. I went back to GParted to try and create the reqiured partition there, but I think this may not be possible (the right format type is not supported).

4. Try again. The linked article suggests 8MB is required, I went back to GParted, deleted my first attempted partition and created a new one with **16**MB (or was it MiB?) of unallocated space and then followed the fdisk instructions, accepting the defaults for the size which meant that all the 16 MB were used.

A couple of reboots later, all was is working. :)

---

### Post by Doctor Colossus on 2012-12-24
I've followed the above advice, but can't get this working with a GPT.
I suppose Boot Booster can't understand it. \-:
You guys are all using an MBR, I presume?

---

### Post by oldos2er on 2012-12-24
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

