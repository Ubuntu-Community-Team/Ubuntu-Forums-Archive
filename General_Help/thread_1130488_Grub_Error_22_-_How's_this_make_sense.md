---
title: "Grub Error 22 - How's this make sense?"
date: 2009-04-19
forum: General Help
---

### Post by Roasted on 2009-04-19
I have 4 drives in my computer. All SATA. Drive A houses Vista/Ubuntu and the other 3 drives are simply backups.

I was in Vista playing a game when Vista crashed. I couldn't even CTRL ALT DEL so I just powered off and back on. Then I got Grub Error 22. So I rebooted. Grub Error 22. Hmm?? I reboot and check out BIOS and I only see 3 drives. My main drive was missing, which is where Vista/Ubuntu are. The other 3 drives are simply formatted with a single partition of EXT3 and house backup data. That's all they do.

I unplugged the other 3 drives and left my main drive plugged in and I was able to boot. So then I powered down and plugged in my other 3 drives and powered on. Then all 4 plugged in were fine and here I am on Ubuntu again.

But I have a few questions.

1 - What could Vista do that would cause my hard drive to disappear from BIOS? Is this a sign of Vista being Vista or a sign of potential hardware failure? The drive works perfectly fine otherwise.

2 - Why do I get a Grub Error 22? I mean, think about it... if the boot loader is on Drive A, yet Drive A is not seen, how does my system even know Grub exists to give me a Grub Error? Is it due to the fact my other 3 drives are in /etc/fstab and fstab is able to detect, oh, Linux partitions, unable to boot... BAM Grub Error? Or what?

---

### Post by codeseer on 2009-04-19
Quite interesting...

I'd make sure my backups were up to date.

---

### Post by Roasted on 2009-04-19
The backups are basically rsync scripts and with the help of crontab, the backup script runs at 3:30AM and 3:30PM, so I know my data is recent, plus I have DVD backups of my pictures which is the most crucial thing to me. 

It's just a question of why my rig is running the way it is. The only time it acts up is when Vista FUBAR's like that.

---

### Post by meierfra. on 2009-04-19
> Why do I get a Grub Error 22? I mean, think about it... if the boot loader is on Drive A, yet Drive A is not seen, how does my system even know Grub exists to give me a Grub Error? Is it due to the fact my other 3 drives are in /etc/fstab and fstab is able to detect, oh, Linux partitions, unable to boot... BAM Grub Error? Or what?

Couple of possibilities

1)   Bios can be funny.  Maybe the Bios didn't correctly detect your main drive, but still tried to boot from it, say after trying unsuccessfully to  boot from the other drives.

2)   Grub is not only installed  to the MBR of your main drive, but also in one of your storage drive.

You can  verify 2) with  the boot info script:[https://sourceforge.net/projects/bootinfoscript/]("https://sourceforge.net/projects/bootinfoscript/")

Download the script to your desktop and run it with

```
sudo bash ~/Desktop/boot_info_script*.sh
```

That will create the file "RESULTS.txt" on your desktop. The first few line of the file will tell you where Grub is installed. If you need help interpreting the file, post it here (make sure to use the code tags).

---

### Post by Roasted on 2009-04-20
I always had problems with Ubuntu when I installed it with other drives present. If I had 4 drives in my computer, and installed Ubuntu on drive A, but then drive C later died, I wouldn't be able to boot my system, which I found to be completely stupid that because a backup drive with no operating system died I was still getting a grub error.

As a result, all of my installs are done with all drives unplugged except the main one the OS goes on. So when I did my install, all 3 backup drives were unplugged except the main one. Then after the install is done, I find the UUID of each drive and add it to /etc/fstab accordingly. 

Having this as part of the equation, I'm not seeing how grub was installed on any of the other drives unless it happened after I mounted the drives when my main drive with the OS was running.

---

### Post by sir_cheats_a_lot on 2009-04-20
My question is... if you have 4 drives.. why the heck are windows and linux sharing one, as opposed to having their own? 
 i mean.. the base vista(without SP1) install is 14.3GB, without installing anything...not to mention it would have prevented this problem and you'd have only had to reinstall windows, :lolflag:

---

### Post by Roasted on 2009-04-20
Because of the way I have things set up. For one, I find it easier to keep Windows + Linux on one drive personally.

A - 500gb
B - 500gb
C - 250gb
D - 250gb

A = Vista (60gb partition) + Ubuntu
B = Rsync'd copy of Ubuntu's home directory.

Drives C and D are completely different. Drive C is a samba network drive for the other computers in the house, and D rsyncs drive C. So even though I have 4 drives in my computer, only 2 of them are used for storage by me personally... in which, of those 2 drives, 1 is a backup, so I only work off of 1 drive at any given time. The rest are strictly backups for designated purposes.

Also - I used to run XP/Ubuntu on separate drives, but I always ran into issues that was a pain in the ***. Granted, those were IDE drives with jumpers and whatnot, so that may have been an issue, but I just find it easier to deal with operating systems on 1 drive, so I've always kept it like that. I really don't see any advantage in having separate drives for separate operating systems, because whether or not I have Vista on my main drive or a separate drive, I've still had Grub crap out on me if something happened to my windows install.

And to your comment about "only having to reinstall windows", I'm not seeing what this means. You can reinstall Windows, not install Ubuntu, and tweak grub accordingly. So that really has no bearing in this case.

---

### Post by codeseer on 2009-04-20
Having them on separate drives lets you install each system at the front of a drive, therefore increasing performance in accordance to the way non-SSD drives are designed.

---

### Post by meierfra. on 2009-04-20
> If I had 4 drives in my computer, and installed Ubuntu on drive A, but then drive C later died, I wouldn't be able to boot my system, which I found to be completely stupid that because a backup drive with no operating system died I was still getting a grub error.


You can avoid this problem by installing grub to the MBR of the Ubuntu drive and  set your bios to boot from the ubuntu drive.(you don't need to unplug the other drives)

Also this isn't really a big problem, since it's fairly easy to reinstall Grub from the LiveCD .  (Or you could get SuperGrub  and reinstall Grub  in no time)

> As a result, all of my installs are done with all drives unplugged except the main one the OS goes on. So when I did my install, all 3 backup drives were unplugged except the main one. Then after the install is done, I find the UUID of each drive and add it to /etc/fstab accordingly.

Having this as part of the equation, I'm not seeing how grub was installed on any of the other drives 

"As a result": This  makes it sounds  like  at  some earlier point in time you installed Ubuntu with the storages  drives plugged in.  And if grub ever got installed to the MBR of one of the storage drive, it mostly likely is still on that MBR. 

Anyway, just run the boot info script and you will know.

---

### Post by sir_cheats_a_lot on 2009-04-20
> And to your comment about "only having to reinstall windows", I'm not seeing what this means. You can reinstall Windows, not install Ubuntu, and tweak grub accordingly. So that really has no bearing in this case.

  actually that was kinda the point of having them seperate.. wouldn't have to tweak grub at all. just unplug the linux drive install windows on the second, and just install grub on the linux drive and simply change the boot priority back to the linux drive after windows was replaced.  don't know if its just me but whenever windows goes out like that on my mom's computer.. it has a habbit of taking out the boot sector with it.  this just makes it less of a headache IMO.   

  Also for futher clarification:  i dual boot with my windows install on my secondary drive ubuntu on the main.  also... what codeseer mentioned is a nice little bonus too.

---

### Post by Roasted on 2009-04-20
Okay, figure this out.

for kicks and giggles I installed Ubuntu 8.10 first on my spare rig, then installed Windows XP after it. Naturally, XP wiped the grub boot loader and only XP would boot.

I restored Grub by the method provided by the LiveCD.

Now, only Ubuntu boots. Windows is not seen whatsoever.

LOL?? How do I get both working again?

---

### Post by sir_cheats_a_lot on 2009-04-20
ever hear of the command: sudo update-grub ?   that usually does the trick.  if not.. you can manually edit grub. by running gksu gedit /boot/grub/menu.lst, and adding:

title MS Windows XP
root (hd1,0)
savedefault
map (hd0) (hd1)
map (hd1) (hd0)
makeactive
chainloader +1

to the end of it, then save; reboot.. and it should be there. this assumes of course your windows install is on the second drive.  if they are installed on the same drive, the root line should be :
root (hd0,4)(assuming you didn't customize the partitions)
and you won't have to add the 2 map lines...i don't think.

---

### Post by Roasted on 2009-04-20
I'm familiar with update-grub. Didn't work.

I manually edited the menu.lst to what you said, leaving out the map sections.

Didn't work.

Am I supposed to use hd1 for the mapping to include them too? Or should I put them to hd0? Not too sure about that part...

---

### Post by sir_cheats_a_lot on 2009-04-20
if you are using 1 drive of the spare computer.   looking at my partitions...well im tempted not to let the partition automatically do it for me any more.  for me its showing my ubuntu drive as follows:
sda1: /
sda2: extented
sda5: swap

why the hell did it skip 3&4? :???:

well.. from what i gather if you are using a single drive the root entry for windows could be hd0,3,4, or 6.  I'd say:
map (hd0,6) (hd0,1)
map (hd0,1) (hd0,6)
or if those don't work try that combination of the other two numbers.

  I don't know.. something was changed with GRUB in the last few releases that has made it impossible to detect windows partitions on it's own. I've never had to do the whole mapping thing until Feisty..but then again I've only been using two separate drives since Dapper.  i just have to remember to backup my menu.lst this time so i don't have to go through that trouble next time i get "bored".

---

### Post by codeseer on 2009-04-21
> **sir_cheats_a_lot said:**
> if you are using 1 drive of the spare computer.   looking at my partitions...well im tempted not to let the partition automatically do it for me any more.  for me its showing my ubuntu drive as follows:
sda1: /
sda2: extented
sda5: swap

why the hell did it skip 3&4? :???:

well.. from what i gather if you are using a single drive the root entry for windows could be hd0,3,4, or 6.  I'd say:
map (hd0,6) (hd0,1)
map (hd0,1) (hd0,6)
or if those don't work try that combination of the other two numbers.

  I don't know.. something was changed with GRUB in the last few releases that has made it impossible to detect windows partitions on it's own. I've never had to do the whole mapping thing until Feisty..but then again I've only been using two separate drives since Dapper.  i just have to remember to backup my menu.lst this time so i don't have to go through that trouble next time i get "bored".

It skips 3 & 4 because there's no more primary partitions.

---

### Post by sir_cheats_a_lot on 2009-04-21
i see...still its an unnecessary thing to skip a number.  it seems.. illogical.

---

### Post by sir_cheats_a_lot on 2009-04-22
also i vaguely remember using the super grub cd to install repeatedly finds and picks it up on occasion.  was like once out of 17 attempts or something. :lolflag:  who knows.. maybe grub-install will work the same way.   yet another reason to always install windows first. ;)

---

### Post by Roasted on 2009-04-22
Oh I know about having Windows first. That's why I tried this on a spare rig for learning purposes. :) 

I just couldn't think of another way to purposely kill my MBR, other than to install Windows second... 

Do you know of a way I could somehow screw up Grub with XP first/Ubuntu second? I still want to try this so I can fix Grub on my own accord if it sincerely dies on my main rig.

---

### Post by sir_cheats_a_lot on 2009-04-22
recently run into this page:
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)
has a good deal of info on GRUB.
on the other hand there is always the community documentation.
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)


as far as intentionally messing things up goes...could always pull the ide/sata cable from the drive while the computer is on... but i wouldn't recommend it.  there is no telling how much or little it might take with it. could end up taking all the data on the drive with it.  not to mention i remember it being a painful experience when i last went through it.  Don't even remember why i did it in the first place to be honest.   I imagine it could seriously damage the drive if done.

---

### Post by Roasted on 2009-04-22
There's things I always wanted to do to junk computers just to see what would happen.

My most recent idea was to remove the RAM while the computer was running...

Anybody got a computer to donate for purely experimental and useless reasons? :lolflag:

---

### Post by egalvan on 2009-04-22
> **sir_cheats_a_lot said:**
> if you are using 1 drive of the spare computer.   looking at my partitions...well im tempted not to let the partition automatically do it for me any more.  for me its showing my ubuntu drive as follows:
sda1: /
sda2: extented
sda5: swap

why the hell did it skip 3&4? :???:



An** extended partition** must be the last on the drive.
The first **logical partition **must start with 5...

So on your drive,
the first partition, a primary, is 1
the next partition, an extended (the only extended one) is 2
the next partition must be a logical, so it's 5

hence the "skipping" of 3 and 4....


Another way of looking at it...

A drive (partition table) can have a maximum of four primary or extended partitions.
These are numbered from 1 to 4
logical partitions always start after the last extended,
so it starts with 5.
**leaving room to grow the partition table** in case you did not use up all four primary/extended partition entries.

If you had only an extended partition, it would be number 1,
and the first logical would still be number 5

"room to add/move"
"room to add/move"
"room to add/move"
sda4 (extended)
sda5 (logical)


sda1 (primary)
"room to add/move"
"room to add/move"
sda4 (extended)
sda5 (logical)

sda1 (primary)
sda2 (primary)
"room to add/move"
sda4 (extended)
sda5 (logical)

sda1 (primary)
sda2 (primary)
sda3 (primary)
sda4 (extended)
sda5 (logical)

---

### Post by meierfra. on 2009-04-23
> An extended partition must be the last on the drive.
Wrong.   For example I currently have four primary/extended partitions and the extended partition is /dev/sda3.

---

### Post by k3ntegra on 2009-04-23
> Were you sure to mount the other partitions you made under windows while installing ubuntu?

If not, next time while you install ubuntu make the windows partition mountable. to do this go to "use as" drop menu and select ntfs. After that go to "mount point" drop down and type in /windows/[partition letter] , keep in mind you can name it what you want, just make sure you set a decent path.

For any linux system i make sure i have swap (1.5 times the size of your ram), / (8gb minimum), and /home (this is where your documents pictures desktop items and stuff will be stored)

I learned this from the OpenSuse dual boot installation guide.

I had this same problem before and said screw it. Then i came across a guide on how to install opensuse.

---

### Post by Roasted on 2009-04-26
Is there a hard drive utility scanner for Ubuntu to test if the drive is okay?

I just unplugged my 3 backup drives and ran the installer on LiveCD for 9.04 64 bit. As always, I re-mount the root partition to be formatted and leave the home directory partition alone.

After 30% in the installer it said something about "Errno 30 - The installer failed due to a read only file system /whatever/the/path/was/X11 - This is usually a sign of a faulty hard disk drive."

I wonder if my main drive is starting to suffer and that's why it FUBAR'd with grub when I originally made this post?

EDIT - I just tried to install Ubuntu 8.10. It got farther along than 9.04 so I got excited. Then... I got the error there too. Yippee!

---

