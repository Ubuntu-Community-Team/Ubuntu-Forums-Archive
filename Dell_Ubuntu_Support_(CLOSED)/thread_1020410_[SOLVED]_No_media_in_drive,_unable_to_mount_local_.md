---
title: "[SOLVED] No media in drive, unable to mount local disk"
date: 2008-12-24
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Landra on 2008-12-24
I need help, this is my first time using Ubuntu.  I have a used Dell Inspiron 8200 with 2ghz 512mb RAM 70g hdd.  I am able to play audio CDs (doesn't include burned CDs) but not a DVD movie  (including burned DVDs).  I receive an error message (for thr CD) that read,"unable to mount local disk,No media in drive". When I try to play a DVD, the message reads,"An error occurred could not open location: you might not have permission to open file".  Please help me to utilize my CD-RW/DVD Rom drive.

---

### Post by gbrainin on 2008-12-24
Ubuntu does not come with the software necessary to play DVDs, because that software is proprietary and requires a license fee.  If you do some searching around, on this board or elsewhere, you can find some options for software you can install so DVDs will play.  (Dell preinstalled Ubuntu comes with a software package for DVD playback, but that's because Dell pays the license fee as part of your purchase.)

---

### Post by Landra on 2008-12-24
Ubuntu wasn't pre-installed.  The laptop came with Windows XP Home (which I have the license for), looks like the HDD was formatted and Ubuntu was installed.  I was able to purchased a burned XP Home CD, since the previous owner lost it, from a pc/laptop fix it establishment.  I am trying to install XP but since the CD drive will does not recogize the media, how can I resolve this without purchasing another DVD drive licence? This there a way I can find out if a license was already used/assigned to his laptop?  I know you stated to look on other post but I would not know where to begin(newbie).  I want to run both Ubuntu and XP so I can accomplish what I need to as well as learn more about Ubuntu.

---

### Post by Landra on 2008-12-25
I still wasn't able to resolve this issue, any help would be appreciated.

---

### Post by gbrainin on 2008-12-25
The first question is whether your drive is physically capable of reading DVDs.  It appears that the Inspiron 8200 line does have that capability, but you should double-check, since without that it doesn't matter what software you have.  Is there a DVD logo on the drive door?

Assuming you have the proper hardware, if you're planning to dual boot Ubuntu and XP, I think XP has DVD playback built in.  There are numerous tutorials on setting up your computer to dual-boot, and you should read and understand them before starting (don't just blindly follow instructions).  Depending on the method used, your existing data may be lost during the process, leaving you with a "fresh" install of each OS, so you'll need to back up any important data you have first.

As for playing DVDs from within Ubuntu, a google search on "ubuntu dvd playback" should give you more information than you need.

---

### Post by zrs_12 on 2008-12-25
Perhaps it is your optical drive?  I have an Inspiron 600m.  A while back, when I would try to burn a CD, it would say that no media could be found.  Sometimes it would play DVDs/CDs and other times it would give me errors like yours.  However, I got a new optical drive yesterday and it was able to detect the blank media in about 15 seconds.  You may want to try a newer optical drive if yours is more than a couple years old.

---

### Post by Landra on 2008-12-25
Yes on the door it says DvD and the previous owner stated it worked (cd and Dvd rom), so I'm assuming it is a user problem (me not knowing what I'm doing). Lol.  Yes my intentions is to run a dual OS (ubuntu and xp).  I figured XP would mopre than allow me to resolve my issue but I want to experience the Ubuntu environment.  I will try the option on google before I commit to purchasing another drive.  What is the best way to backup my existing information?  Another question: how do I change the username and password?  Under Terminal it shows the previous owners name.

---

### Post by zrs_12 on 2008-12-25
I don't think you can change the username.  There are alot of things that depend on this name.  However, you could just create a new account and delete the previous owner's.  If you are wanting to back-up your HDD, I would just get a removable storage medium (since your optical drive isn't working, use a USB drive with enough space) and use "sudo mount /dev/(your HDD deivce here) /media/disk", then "cp -r --preserve /media/disk /(mount-point-of-your-usb-device)".  This would have to be done from a liveCD, or other linux partition.

---

### Post by Landra on 2008-12-26
everytime I try any function in Terminal the message reads:
[sudo] password for (username).  Is there a way to just reformat the HDD and start from scratch?  Would that possibly get the CDr/DVD to work? I just had surgery and this has been an added pain because I am not familiar with it.

---

### Post by Landra on 2008-12-26
I already tried the password that was used to log into the system but it did not work, is there a separate password that may have been used by the previous owner?

---

### Post by zrs_12 on 2008-12-27
That is unlikely to make your optical drive work.  It is more than likely a hardware issue.  If you don't know the password, then you may have to reinstall your operating system.  Since your optical drive is shot, use UNetBootin to install Ubuntu on a usb drive.  Then, boot your computer off of this usb drive and click the icon to install.  Follow the wizard.  This will format your disk (the partition you choose or you can use the entire disk) and will install Ubuntu on this selected partition.  This will likely only fix your problem with the password.  As I said, the disk drive issue is probably a problem with your hardware.

---

### Post by gbrainin on 2008-12-27
> **Landra said:**
> everytime I try any function in Terminal the message reads:
[sudo] password for (username).

That's exactly what it's supposed to do.  It's asking for the user's password to confirm that you are executing this command as a "super-user."

Two caveats:

1. If the user you are logged in as is not a member of the "root" group, that user is not allowed to execute super-user commands, so giving the password won't help.

2. When you use the terminal, passwords are not echoed back (*i.e.*, you do not get *** on the screen as you type).  This is normal.

---

### Post by Landra on 2008-12-29
I'm not sure I understand, I'm a newbie.  I did find out more information has I try to get more familiarized with the laptop.  It is running Mac OS and Ubuntu 8.04 Hardy.  I think I was retyping in the password since I did not see any ** or something on the screen indicating it was being accepted.  What command can i try to see if it will auto-mount the CDRW/DVD player?    

Should I be using this command in Terminal?
sudo apt-get update 
sudo apt-get install libdvdcss2

I was told the laptop has a wireless card but I have no idea how to get connected to the internet.  I do run a DSL connection on my home pc running XP.

---

### Post by Landra on 2008-12-29
Here is a screenshot I saved from the laptop to the Kingston flash drive to my pc (to add to this post). I hope this helps otherwise I may have to go with the last resort (knowing we are in a recession) which is replace the drive.

---

### Post by drsaamah on 2008-12-29
Well, let's take a step back to find out if its the hardware, or if its an install gone wrong.
You said that you wanted to double boot with Windows XP, and Ubuntu.  If you were going to do that, you always want to install Windows first anyways.  So grab an XP install disk (I'm assuming you have one...?) and put it in the drive.
Next, restart your computer and on the Dell BIOS screen, hit F12 to send you to the one-time boot menu.  There you can tell the computer to boot from the optical drive.
IF that works, then the drive is fine, and you at least install XP, and then come back here for instructions on how to install Ubuntu.
IF you weren't able to boot from disk, then its more than likely that your optical drive is shot.  In such a case, I'm very much sorry.  Search around Dell's refurbished shop or newegg.com to see if you can find a new one for super cheap.
Best of luck!

---

### Post by gbrainin on 2008-12-29
> **Landra said:**
> Should I be using this command in Terminal?
sudo apt-get update 
sudo apt-get install libdvdcss2

I was told the laptop has a wireless card but I have no idea how to get connected to the internet.  I do run a DSL connection on my home pc running XP.

I agree with drsaamah regarding testing your optical drive, but FYI regarding the above:

Yes, those commands (and pretty much any commands you type) are executed in the terminal.

sudo means "execute the following command with super-user privileges."  That's why it asks you for a password.

apt-get is a command to run the package manager.  apt-get update means to update the list of packages, and apt-get install XXX means install package XXX.

apt-get assumes, however, that you have an internet connection (there's a way to use it with packages that are maintained locally, such as on a CD, but the default behavior is to use the internet).  So if you don't have an active internet connection, the apt-get commands won't do anything useful.

---

### Post by Landra on 2008-12-30
Thanks to all on this issue.  I tried to install XP from the CD by selecting the F12 function.  A file was corrupted or missing (can't remember) so the Setup would not complete.  I tried it again and could never get back to the Windows XP setup.  I will try another disk, if I am still gettting the error message than I know my next step is to replace the optical drive.

---

