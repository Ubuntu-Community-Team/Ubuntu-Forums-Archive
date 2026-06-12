---
title: "problems creating USER account???"
date: 2006-01-04
forum: General Help
---

### Post by julianHigginson on 2006-01-04
hi,

I'm having a go at running Ubuntu alongside windows XP. the live disk seems to work fine, but I'm having a bloody frustrating time of getting the install CD to get me a working install.

Basically, It seems I can't create a user account. On the "install" phase of ubuntu, when it gets to the create accounts stage of the process, I enter my name "julian higginson" username "julian" and a password (a couple of lower case characters, and some numbers) but after the 2nd password, some error message flashes past too fast to read, I have no idea what it says or what to do about it.... it goes back to username, and again and again, ad infinitum....  and i have to quit out of the create user stage and pick the next step to continue....

THEN, in the setup phase of the process, it does the create a user account dance AGAIN, but starting just with the password... I type in a password twice, and still no joy. when I quit that, it asks to create a root password. I *CAN* do that. and it accepts my root password then it continues on its merry way, eventually finishing and leaving me with a lovely brown ubuntu login screen. 

except when I login as julian of course it doesn't know what the password is.

and, of course, I can't login as ROOT from that login screen.

when I reboot linux, It runs GRUB, I pick ubuntu, and it loads straight up into the brown login screen again.

I've installed this thing twice, and am beyond annoyed right now. why on earth wasn't the install CD letting me make a user password (or account?) and how do I fix it, please?

oh yeah. 80G HDD: 40G NTFS winXP, 1G swap, 20G linux3 UBUNTU, 20G FAT32. if that makes any difference?

---

### Post by mcduck on 2006-01-04
I've seen that happening, and it was caused by spaces or special characters/letters in either username or password.

Also username must start with small letter nad can't contain spaces, but it seems that your's is ok.

By the way, how do people end with installation asking for root password? I've never seen that.. I've heard that it happens if you do 'expert' install, but I've never seen any option for doing that too. I've used both manual and automatic partitioning, but sure that's not it.. (I'd like to know how to avoid that happening, as I prefer the Ubuntu's default way of no root access)

---

### Post by julianHigginson on 2006-01-04
well because I'm a maschoist, I thought I'd have another bash at it....

I rebooted with install disk, killed all linux partitions. recreated them, and sat down while the install CD put everything on the drive again.

again. endless loop with creating user accounts in install phase.... this time name = "julian" user="julian" password="julian" oh well.

for setup phase, boot to GRUB (I assume there's a way to make GRUB have windows as the default choice, when everythings working. right?.... right??) and select linux...  

booting.

message basically says "empty password, you need to add one. (OK)"

and i'm back in the repeating password loop. though with MANY MANY repeated attempts at entering the password twice, and grabbing a word or 2 off the screen at a time, I got the error output.
"groupdel: group julian does not exist"
"chpasswd: line 1 unknown user julian"
"chpasswd: error detected, changes ignored"

hitting cancel (only way out of password loop) dumps me in the UBUNTU BASE SYSTEM CONFIGURATION menu.

hitting "setup users and passwords" gives me the magical, mystical "you need to setup a password for 'root' window. where I set a password for root This time i used password = "julian" just for the satisfaction of seeing this thing accept my name somewhere... enter twice. accept.

then I get a screen saying basically "its a bad idea to use root... blah blah... setup another account now.... blah... note that you may create it later.. blah blah... create now? (yes) (no) " 

I hit YES, and it's straight back to the "empty password" screen.... same problem. returns to previous screen. so this time i choose NO.

it dumps me back to the BASE SYSTEM CONFIGURATION MENU...

I set hostname default: "ubuntu" do apt-get stage, etc etc (now on setup packages section) 

looks like I'll be back where I was 2 hours ago again soon.... 

So I hope the info I managed to write down this time was of some interest to someone out there....

---

### Post by jonathanm on 2006-01-04
Hi i had this problem as well,
try installing again, this time using a different name to your username and password
e.g.
name = julian higginson
user = julian
password = password

The password can always be changed afterwards

---

### Post by starscream1 on 2006-01-04
I had this problem when trying to dual boot ubuntu 5.10 with windows xp pro and creating partitions manually. 

It was because I had created a partition for /home accidentally and it was the wrong filesystem blah blah blah....

If you try creating 2 partitions out of your free space (not your windows partition) instead (ext3 journaling filesystem) and a swap partition then the /home mount is automatically created on the root (/) ext3 partition. This solved my problem. Try it, make sure you only have 2 partitions a root and a swap, do not create a partition for /home.

Also make sure you install GRUB onto the 2nd partition of your first hard drive (if the 2nd partition is your ubuntu root partition. If you install it into your MBR (master boot record) you could fuxxor your hard drive or windows installation.

I used hd0,1 

hope this fixes you problem.

---

### Post by starscream1 on 2006-01-04
also make sure you havent tried to mount your fat32 drive as /home.

Are you following a tutorial on the net? I followed one that recommend a fat32 share os partition.

---

### Post by julianHigginson on 2006-01-04
^^^ that's what I did the first time....... 

:( 


so.. if I end up with another ubuntu login window, and no user accounts, is there ANYTHING I can do rather than a complete reinstall? can I kill the login window, get a console login for root, and make the damn user account myself?

oh, another interesting thing - this install process has asked me about my video card and some kind of virtual display driver (gah... forget what its called now) three times during the install... is this normal?

and right now its asking for me to select screen rsolutions, with a whole list of resolutions, and 3 have asterisks against them, but I have no means of changing the selections?? I can move around the screen with cursor & tab, but nothing changes anything, till i hit enter, and that just accepts and goes back to installing packages.....

---

### Post by julianHigginson on 2006-01-04
aaah!! lots of replies.. that last thing I said was aimed at jonathan.

It's possible fat32 has been mounted as /home I don't really know that much about linux or partitions (I can use a working install but this is my first go, and I'm basically just following what I read about having a partition for trading files with my NTFS based winXP... ) I just used the manual partition thing, and made the 3 partitions of 3 types. If ubuntu installer makes the fat32 partition /home by default, then it probably is... 

OK... so what can I do, short of a full (4th one!) reinstall?

PS, starscream.. I am already using GRUB on MBR. if worst comes to worst I'll start again with the whole drive, as I only reinstalled XP yesterday anyway. But it's working at the moment.... also, the ubuntu install CD seems to think that the MBR is the way to go for GRUB, rather than 2nd partition.

---

### Post by bonzodog on 2006-01-04
Right people!
Here is the experts guide on good partitioning.
You CANNOT use fat32 as a /home partition. forget it. create a 'shared data' partiton on fat 32.

Julian: It is advisable that you create a seperate /home partition.  Create your hard disk like so:

hda1  (primary): NTFS (WinXp)
hda2 -extended containing following logical partitions:
hda5: (logical)  Fat32 mount in ubuntu as /data.
hda6: (logical)  ext3 / partition containing ubuntu root system
hda7: (logical)  swap -**keep this below 500MB**
hda8: (logical)  ext3 /home ubuntu user directories.

This should work. Do a clean install, and clean partition.

Install grub to the MBR.

Any problems, ask!

---

### Post by starscream1 on 2006-01-04
like yourself, i'm no pro with linux but I do have 2 up and running dual boot ubuntu/winxp computers (laptop and desktop) and I did run into the problem you have. 

This is what I did and what I think you should do.

What I think I would do is fix the MBR with a DOS boot disk, windows 98 boot disk or something. Google for fox MBR. I think you will need your master boot record repairing back to windows XP then try booting in XP, make sure XP works ok. I am guessing either you have 2 partitions, a windows xp partition and a free space partition, or two physical hard drives, either way you need a partition to make the linux partitions in.

Ok once xp is ok and still booting ok I would then start the ubuntu installation. When in the partitioning utility I would leave the windows partition lone and then remove all other partitions so you have the windows partition and a load of free space. in this free space I would create an ex3 partition and call it Ubuntu, make it a primary partiton, change it to bootable and make sure it is active. Then I would make a logical drive and make it the swap file system. DO NOT make it bootable. 

Then I would make the fat32 partition and make sure it is not bootbale either (to make the root, ex3, /, partition bootable you need to give in a boot flag.

Make sure you do your calculations before partitioning so you dont run out of space. I would give swap 1 gig and make the other two (root and fat32) equal or just about. Make sure you do not mount the fat32 drive anything other than the default it gives, I think it makes it a media mount, leave it as that, make sure no partitions are /HOME

Then continue installation, when you get the GRUB installer DO NOT install to MBR, instead install it to the first part of your 2nd partition on your first hard drive that is
if you installed your root partition there. Most people following tutorials will I think.

If you installed it somewhere else you will have to give the device address or use the hd0 format

do not install grub to hd0 as that is the MBR, instead install it to hd0,1 if your root partition is the 2nd partition of the first hard drive or it would be hd1,0 if it was the first partition of the 2nd hard drive. basically the hd0 bit is hard drive 1 and hd1 is hard drive two the comma followed by a number is the partition 0 is partition 1 and 1 is partition 2, make sure you add it to the beginning of the partition you use as root if it asks. If you need more help you can email me or I can help via msn or something if you have another computer which you obviously do to be posting here.

remember though I am not  a pro, not even close, just giving you info on how to do what I did.

---

### Post by julianHigginson on 2006-01-04
well, I have no /home partition.... according to the boot disk I just stuck in again, I have one physical hard drive (IDE1 master - hda) partitioned as:

#1 primary 40.9G (lightningbolt) NTFS /media/hda1
#5 logical 1G SWAP swap
#3 primary 20G ext3 /media/hda3
#4 primary 20G FAT32 /media/hda4

I have a windows system that boots and works fine (and detects the fat32 partition) and what appears to be a linux system that has no users and no other way to get in... 

@ bonzodog. OK. you seem quite emphatic to know what you're talking about.. I'm doing one more install for the dummies (ie, me) the ubuntu install disk doesn't seem to display extended partitions, but interpreting what you wroote, if I delete everything except NTFS, and setup my partitions so the partition table looks like this:

#1 primary 40.9G (lightningbolt) NTFS /media/hda1
#5 logical 20G FAT32 /data
#6 logical 10G EXT3 /
#7 logical 500M SWAP swap
#8 logical 10G EXT3 /home

with GRUB on MBR again, you think it should work?

---

### Post by julianHigginson on 2006-01-04
alrighty!!! 

Partitioning did the trick, as above...  (except I named the NTFS win xp drive /windows to avoid confusion)  and it all seems good.

I'm posting this update from the now running linux install on my HDD, while autoupdate takes ubuntu to latest revisions of everything... 

I hope things work out for me and linux. haven't used it for years (since I had it in labs at uni) but I'm more and more attracted to the idea, the more and more scary microsoft get with sneaky DRM stuff.....

thanks for your help, everyone.

I really think some of the info from this thread belongs in the WIKI.ubuntu.org entry on dual boot with XP...  heh...  maybe I'll get around to adding it, so the next person like me that comes along doesn't have to install ubuntu 4 times and annoy a bunch of people on here to get it to work... 
;)

---

### Post by Lord Illidan on 2006-01-04
[quote=julianHigginson]alrighty!!! 
I really think some of the info from this thread belongs in the WIKI.ubuntu.org entry on dual boot with XP...  heh...  maybe I'll get around to adding it, so the next person like me that comes along doesn't have to install ubuntu 4 times and annoy a bunch of people on here to get it to work... 
;)[/quote]

That's the spirit!!!

---

