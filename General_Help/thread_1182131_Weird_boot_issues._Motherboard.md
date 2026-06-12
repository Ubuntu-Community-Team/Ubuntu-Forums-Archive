---
title: "Weird boot issues. Motherboard?"
date: 2009-06-08
forum: General Help
---

### Post by Roasted on 2009-06-08
I have 4 drives in my computer. The main one dual boots Vista/Ubuntu.

I'm not sure why but there are certain times my computer will error out when booting up. Sometimes I get "error 18 selected cylinder exceeds maximum supported by bios." Other times I get grub error 22. When I check the BIOS for what SATA ports are active, it seems that my main one sometimes isn't found.

I have an ASUS P5QL Pro motherboard. I'm not sure what to blame. I don't know if it's the board itself or if it's something with Grub or what. What should I take a stab at? Any P5QL Pro owners here have any issues?

---

### Post by nacho32 on 2009-06-08
is their a bios upgrade? try re-flashing the bios

---

### Post by Roasted on 2009-06-08
The description of the BIOS updates is regarding the ExpressGate, which I always had errors with so I disabled it anyway.

I can't imagine it'd help, but I'll give it a shot...

EDIT - Even though I selected Linux from the OS menu, I'm left with a file... a .ROM file... that I have no idea how to use and I see no documentation on ASUS's web site on how to use it. (Go ASUS!)

Anybody know how to flash a BIOS in Linux with a .ROM file??

---

### Post by Wiebelhaus on 2009-06-08
For one , Asus is pure crap! But anyway it sounds like a faulty hard drive or controller , I'd test the HDD first.

---

### Post by Roasted on 2009-06-08
The ironic part is, the hard drive is brand new. I had an actual hard drive failure when 9.04 came out. 9.04 errored out saying there was a problem with my drive and it's almost definitely hard drive failure. I ran some scans on the drive and sure enough it was on its last breath, so I was able to pull an image of my Vista partition. Afterwards I forgot to shut off my PC. By morning the drive was non responsive. 

EDIT - I updated the BIOS and rebooted about 15-20 times. I didn't get an error a single time. Before I flashed it I was getting an error 3 out of 5 times I rebooted.

So far this board I have really liked. It's one of the better motherboards I've had. Updating the BIOS was a little confusing for me cause I'm used to Dell at work, where it extracts within Windows and flashes the BIOS from there, then reboots. With this ASUS board I had to put the .ROM file on a flash drive, reboot, and in the BIOS there was an update utility built in.

Not too shabby. Let's hope my problem was fixed....

---

### Post by Roasted on 2009-06-10
Hey! Guess what? Not fixed.

I keep getting error 18 with Grub. Every 3-4 reboots I get it and I'm forced to reboot again. I'm convinced it's something with Grub and not a motherboard problem at this point because I figured out error 18 is an actual error with grub. 

error 18 selected cylinder exceeds maximum supported by bios

I have 4 drives in my computer.
3 backups. 1 main. Main = Vista/Ubuntu

80gb NTFS - Vista
1gb Swap
20gb EXT3 - Ubuntu Root
380gb EXT3 - Ubuntu Home

I found out grub resides on /dev/sda6, which is my root partition for Ubuntu. 

So if grub is on my root partition, how in the *#$( am I getting errors?

---

### Post by Roasted on 2009-06-11
Okay, the BIOS is flashed to the newest version and it doesn't seem to help at all.

I booted up my computer this morning. I rebooted probably 15 times. Each time I got an error. Anything from Error 18, Error 16, Error 22, or "Please insert proper boot media and restart the computer."

Every time I went in my BIOS I checked the SATA configuration. It picked up the following.

1 - Not Detected
2 - Hard Disk
3 - Hard Disk
4 - Hard Disk
5 - Not Detected
6 - Not Detected

1 2 3 4 should have hard drives. Port 1 is Vista/Ubuntu. Somehow it magically decides it won't recognize it's available.

What the *$#( should I do? Is this a grub problem? Is it a motherboard problem? I just have no clue where else to go from here cause I don't have spare motherboards sitting around.

I didn't do this this morning, however if I unplug my 3 backup drives and only leave the main one plugged in, it'll boot. Then I plug in the other 3 drives and I'm all right for another 2 days or so.

What to do...

---

### Post by Roasted on 2009-06-14
I left my computer powered off for the 3 days I was gone this weekend. I came back and was unable to boot. My computer was giving me various errors each time I rebooted, but in no particular order. According to [http://www.uruk.org/orig-grub/errors.html](http://www.uruk.org/orig-grub/errors.html) here are the errors, however when I got the error all I saw was Error 16, Error 18, Error 22, etc. I had to google these to match up what each # corresponds with.

Error 16 - "Device string unrecognizable"
Error 18 - "Invalid or unsupported executable format"
Error 22 - "Must load Multiboot kernel before modules"

I found by unplugging my 3 backup drives and booting to only my main drive that would sometimes allow me to boot up. Then I'd just power off, plug in my other 3 drives, and boot up and I'd be okay for a few more restarts. Well, this time around after my 3 day vacation, I can't boot PERIOD. When I boot up with the single drive, before the grub selection screen it gives me "insert proper boot media and select any key" or something of that nature, even though my main drive is plugged in. The BIOS also has trouble seeing it sometimes.

So I unplugged all 4 drives from ports 1 2 3 4 and plugged them into SATA ports 3 4 5 6. So far, so good.

Is it possible a single port on a SATA controller can go bad? I'm not sure what to do now... RMA the board? (less than 1 year old) or just buy a new one of a different brand? The only other one I was eyeing up was a Gigabyte...

---

### Post by Roasted on 2009-06-22
All right. Yet again the problem has surfaced. It seems as if things will be fine for a few days then I have an hour long headache trying to boot my computer.

This thread is getting bumped till this gets working. I'm not so sure it's motherboard related, because every single time I have an issue, I can reboot it 40 times if I want, but what fixes it is disconnecting my 3 spare hard drives and booting once on the main drive. Then, power down, connect my 3 spare drives, and bam, everything works.

What is it I need to do?

Here's my /etc/fstab. Is something wrong with it??


# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=a11c8bb8-2175-4a8e-9813-0e67ac45e8a3 /               ext3    relatime,errors=remount-ro 0       1
# /home was on /dev/sda7 during installation
UUID=498359fb-1c75-474d-94ea-fcb26f84c012 /home           ext3    relatime        0       2
# swap was on /dev/sda5 during installation
UUID=eacce669-8150-428b-9ac9-fe04025b027b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


#BACKUP DRIVES
#Local Backup Drive
UUID=b2354e40-cd24-41eb-b41b-0aadc9933166       /media/localbackup      ext3    defaults        0       2

#Main Samba Network Drive
UUID=772764b7-e571-4897-ba6d-ded412a5e814       /media/storage          ext3    defaults        0       2

#Backup Samba Network Drive
UUID=b862f78f-4fcc-4d41-9d64-b7534da2dc84       /media/storagebackup    ext3    defaults        0       2

---

### Post by mdurham on 2009-06-22
Is it possible that bad memory could cause this? Or power supply problem as the big drive maybe needs more power?

---

### Post by Roasted on 2009-06-23
> **mdurham said:**
> Is it possible that bad memory could cause this? Or power supply problem as the big drive maybe needs more power?

Why would the big drive need any more power than the local backup drive? They're both identical 500gb drives. I have a 650w PSU which checked out fine on my meter.

I was thinking it was something with the boot process because it alternates in between different grub errors, sometimes 16, sometimes 22, and often times 18. I also get a secondary error 18 which sounds like a motherboard error. Something about too many cylinders for the BIOS. When I googled the error, that particular error was in regards to motherboards that didn't support hard drives past 8 gb in size. LOL? My system was built in October. I can't imagine my motherboard would have trouble with 8 gb drives....

---

### Post by Roasted on 2009-06-23
This thing is seriously going to be out the window.

This morning - I shut my computer down. Properly. I went through the shutdown menu and selected "shut down." 

The computer shut itself down seconds after.

I went to work. Came home. Powered it on.

Unclean shutdown, checking drives: 

What? Really? I shut the computer down like normal and you're telling me it's an unclean shutdown? No. Just.. no. 

Oddly enough, this has happened several times. It's so hit or miss. It's like I'm afraid to shut my computer off cause I don't want to fight with it for 2 hours to get it powered on again.

What can I do to get this computer running the way it should be? When it boots, it works fine. But it seems as if Ubuntu may have issues booting + handling my spare hard drives, cause it seems to get confused on which one is which, despite my BIOS being set to the drive in SATA port 1. 

What can I do?



EDITTTTTT - I have 1 drive plugged in. I booted up, unclean shutdown blah blah did that scan... came back with a root@computername prompt... I did sudo fdisk -l

I saw several partitions. The first was NTFS - Which is Vista. That partition had the * for boot. So the boot section is on NTFS... Is that right? Shouldn't it be under root?

---

### Post by Roasted on 2009-06-24
All right. I need the hardware experts to chime in here. I've finally cleared up the file system checkdisk problem I was having that couldn't seem to cure itself. Turns out I had to manually run fsck on each partition, not just sudo fsck in general.

Okay fine. But I was in Vista earlier and things were randomly working, other times they randomly stopped. I automatically said "eff vista" and went to linux.

An hour later, things started acting weird. For example, when I open terminal, I don't see any of the options at the top - file, edit, etc. When I type in terminal, I don't see it. I opened other menus from the system - preferences menu, and they all do the same thing.

Then pidgin stopped logging messages. Every time I IMed somebody it said CANNOT LOG MESSAGE. Then pidgin all together stopped responding, yet firefox was fine. Then, they flip flopped.

Ubuntu and Vista are both acting extremely strange. I would naturally suspect the hard drive, however, my old hard drive (which was bought brand new in october 2008 ) was replaced under warranty last month because I thought it was bad. But sure enough even with the brand new drive, issues are still surfacing.

I'm considering another motherboard. What do you guys think? I'm running an ASUS P5QL Pro.

---

### Post by cariboo on 2009-06-24
I would really suggest you use the hard drive manufacturers diagnostic tools, and check the hard drive first. Even brand new hard drives fail. 

Also run memtest from the Live CD, I've had defective ram do strange things.

---

### Post by Roasted on 2009-06-25
> **cariboo907 said:**
> I would really suggest you use the hard drive manufacturers diagnostic tools, and check the hard drive first. Even brand new hard drives fail. 

Also run memtest from the Live CD, I've had defective ram do strange things.

So far memtest has done 2 passes with no issues, however I'm letting it run throughout the night and while I'm at work tomorrow.

I'll check the hard drive, but my gut instinct is telling me it's the motherboard, mostly due to the way it acts prior to the hard drive even booting. I get weird errors and things just don't seem... right. And yes, I flashed to the latest BIOS.

---

### Post by jdeppel on 2009-06-25
> **mdurham said:**
> Is it possible that bad memory could cause this? Or power supply problem as the big drive maybe needs more power?

I'd definitely check your memory modules (as you say your doing). I had one stick go bad about 2 years ago, and I was having all sorts of weird booting issues...granted I was still only using XP then...but I wouldn't be surprised if that's your problem.

Another thing I can think of is maybe swapping SATA cables if your haven't already, and see if this issue with one drive not being detected migrates to another drive.

Though it may very well be a mobo issue if the above checks out, I'm not sure if I buy that. I would think you'd have had an issue (or two) while flashing your BIOS or seen a problem related to something else in addition to the one hard drive. But I've been known to be wrong time to time and YMMV.

---

### Post by Roasted on 2009-06-25
9 hours.
10 passes.
0 errors.

jfkdla;jflkjdsaflkjsd;lkasd

---

### Post by beacon on 2009-06-25
I'm not certain this is the correct thread, but my query does concern weird boot issues. I have been using the new version of Ubuntu for several months with no problem. Suddenly, it has all gone wonky. For a time, when loading it halted at Bluetooth for quite a long time, so I removed bluetooth. Now it stalls when the motherboard logo appears, but begins again after three or four minutes. After that, there are all kinds of weird events; for example, the USB logitech mouse doesn't function for about five minutes. Strange things happen with firefox, and it is all very slow.

I would give up and start from scratch, but I don't want to lose any information, and so far I haven't been able to burn a back-up disk, which is probably simply a matter of ignorance.

Has anyone any idea why this has suddenly happened. I have done nothing except load the suggested updates and remove bluetooth.

---

### Post by Roasted on 2009-06-25
beacon - are you dual booting? I was suspecting Ubuntu until I saw Vista was having hardcore issues too. If you're dual booting, what's your other operating system act like?

---

### Post by beacon on 2009-06-25
Thanks for the quick reply. No, I only have Ubuntu.

---

### Post by Roasted on 2009-06-25
I honestly wish I could put a pointer on it and say, yes, it is Vista/Ubuntu/Whatever that's F'ing up... but geez... when both operating systems on the 2nd brand new hard drive in 9 months are doing it and you ran a memtest for 10 hours with no problem... what else COULD it be??

---

### Post by Roasted on 2009-06-25
Found my problem...

It was the SATA cable.

I ran Seagate Diagnostic Tools in Vista and my primary drive failed. I remembered then I used a different type of SATA cable for my primary drive because the other SATA cables I used for my 3 backup drives were JUST short enough that it couldn't reach my primary drive.

Found a different SATA cable, popped it in, booted to Vista, ran diagnostics - pass.

I booted to Ubuntu and I got the same error at first. It said unclean shutdown but ultimately failed and went to the command prompt looking screen. I ran sudo fsck /dev/sda6 and sudo fsck /dev/sda7. It fixed something with sda6 (root), but said sda7 was clean. When I ran it on /dev/sda6 again, it said clean.

I rebooted twice, each time I booted fine. No issues. All because of a damn SATA cable...

---

