---
title: "Backing Up My System"
date: 2005-12-11
forum: General Help
---

### Post by TrumpetMan258 on 2005-12-11
Okay, I need some help.  I've tried a couple different backup programs, and read about many others, but none seem to suit my needs.  Everything seems to fall under three different catagories: it's not free, it only uses the command line (I would much rather use a GUI for this), or I just can't get it to work.  What I'm looking for is a program that will easily backup my computer to an external USB hard drive.  I would like it if I could specify what gets backed up, because I may just backup my home directory.  Not being able to find a good backup program is really discouraging to me.  Any ideas?

---

### Post by aysiu on 2005-12-11
[PartImage](http://www.partimage.org/screenshots.en.html)?

---

### Post by ScreemingBlue on 2005-12-11
Have you tried Simple Backup for Gnome. I think this will be the defacto desktop backup utility for the coming Dapper release. Correct me if i'm wrong. You can get it here... > sudo apt-get install sbackup

Cheers

---

### Post by mherring on 2005-12-11
Just grabbed sbackup and it looks like it has the right features--I am going to try it.

I noted that it was sponsored by the Google "Summer of Code".  REALLY great to see stuff coming out of that program.  Microsoft is right to be worried about Google......;)

---

### Post by TrumpetMan258 on 2005-12-11
I've tried simple backup, but when I click the backup button, a message comes up that tells me that a backup run has been initiated in the background, but nothing else happens.

I've heard a lot about partimage, and it seems worthy of trying, but am I the only one that can't go to partimage.org?  The site is always down.  Is there another place I can get more info about it or download it from?

---

### Post by mherring on 2005-12-11
[QUOTE=TrumpetMan258]I've tried simple backup, but when I click the backup button, a message comes up that tells me that a backup run has been initiated in the background, but nothing else happens.[/QUOTE]

Perhaps nothing else is **supposed** to happen---it can be moving files in the background and all you'll notice is the drive lights flashing.
 
Did you configure it first---ie specify where the backup copy should go?

Did you check in this location to see if something got copied?

---

### Post by aysiu on 2005-12-11
[QUOTE=TrumpetMan258]Is there another place I can get more info about it or download it from?[/QUOTE] Try Synaptic.

---

### Post by TrumpetMan258 on 2005-12-11
Drive lights don't flash, configured it, and nothing appears on the external hard drive.

---

### Post by TrumpetMan258 on 2005-12-11
Well, I guess I already have partimage.  Sorry, I didn't realize it.  Where does partimage save the image file?  I don't see any way to specify this.

I'm also still interested in a program that will let me back up only certain directories, if anyone knows of a good one.

---

### Post by aysiu on 2005-12-11
[QUOTE=TrumpetMan258]Where does partimage save the image file?  I don't see any way to specify this.[/QUOTE] You don't get a screen that looks like this?

---

### Post by TrumpetMan258 on 2005-12-11
Ohhhhhh....boy, do I feel dumb!  Yeah, but I didn't know I could whole directory paths in the "image file to create/use" area.  I was just putting in a file name, and that's it.  Duh!  Well, thanks for pointing that out.  I'll try it again and see what happens.

---

### Post by TrumpetMan258 on 2005-12-11
Well, I'm having some problems with partimage and my external drive.  However, I'm not really worried about that.  What I want to do right now is just backup my home directory so I can reinstall both Windows and Ubuntu and dual-boot.  Partimage might be useful to me later on, now that I know how to use it, but for right now, I just need a program that will only backup the directories that I choose.

---

### Post by aysiu on 2005-12-11
[QUOTE=TrumpetMan258]Well, I'm having some problems with partimage and my external drive.... for right now, I just need a program that will only backup the directories that I choose.[/QUOTE] Is there any reason you need a *program*, then? Why not just copy and paste the directories you want on to your external hard drive?

---

### Post by TrumpetMan258 on 2005-12-12
I've tried.  First, I get whole crapload of error messages saying that files couldn't be copied, and I have to skip them.  These are mostly .dll files and things like that.  Then, most of the stuff just doesn't copy over.  I'm having a heck of a time trying to manage my files right now.  Sheesh.

---

### Post by aysiu on 2005-12-12
If you're reinstalling both Windows and Ubuntu, I don't see why you should be copying .dll files. Everything you need to back up (unless it's entire partitions) should be in either C:\Documents and Settings or /home, right?

---

### Post by TrumpetMan258 on 2005-12-12
Here's all I did: in Ubuntu, I dragged my home directory folder over into my external drive, and while it was trying to copy files, I had all those problems.  Also, Windows isn't currently on my computer, but I want to put it back on as well as reinstall Ubuntu, and dual-boot.

---

### Post by aysiu on 2005-12-12
I realize you want to back up your entire /home folder, but here's what I would do (and I've done it before): just back up your email and web folders and your regular files (music, pictures, documents, movies). 

I happen to use Thunderbird and Firefox, so my settings to back up are /home/username/.mozilla-thunderbird and /home/username/.mozilla. It's important, when copying those files, not to have Thunderbird or Firefox (or whatever programs you use) open. You should also realize that they're hidden files, so you may need to control-h to see them.

When you reinstall Ubuntu, create a separate /home partition--that way you can reinstall again (say, if you want a clean reinstall for Dapper or you just happen to screw up your Ubuntu accidentally) and keep your settings without having to back them up.

Taking just your files, email, and web stuff over will mean you may have to reconfigure some other things once you reinstall, but if you keep a separate /home partition, this reconfiguration will be a one-time deal.

---

### Post by tomwell on 2005-12-12
Aysu,

When i want to back up just so that in the event of a crash or if i wanted to reeinstall on a new pc i would have everything done for me "ie" settings, Gdesklets and all the multimedia codecs and all...

Do i need to use partition magic ( I am worried since i have a rather big partition 10gb used...I suppose i could back up all the docs sepaprately)

Or

Should i use The back up my Home directory method...???

Bit confused as to whgat backing up my home directory does if it carries everything... all installed progs + Multimdeia codecs, deklets...

Sorry If this is a stoopid question but i really cant figure it out.....

Peace

Tom

---

### Post by akiro.yamamoto on 2005-12-12
The simple answer is this:
The /home directory stores basically (by default) all your documents as well as configuration files. Under normal circumstances your programs that you install via Synaptic of apt-get will be installed in the main system (under / ).
So backing up the /home folder will NOT back-up these programs. 
If you use Simple Backup choose custom back-up and add the following
directories under the include tab :
/etc/apt/ 
/var/lib/apt/ 
/var/cache/apt/
This will back-up the downloaded .debs that synaptic retrieved from on-line and any .deb packages you installed manually with dpkg -i <package>.deb . So those can be re-installed after a system failure.

Hope this helps

---

### Post by tomwell on 2005-12-12
Akiro,

Once again Thank you...Now it is all clear...

Peace

Tom

---

### Post by TrumpetMan258 on 2005-12-12
Okay.  I guess that's what I'll do.  I'll just go through my home directory and pick and choose what I want to save.  I'm at college, and this is finals week, so it'll be a couple day until I get a chance to do it.  How would a seperate home partition work?  What filesystem should I make it?  How much space should I set aside for it?  I planned on dividing my 40 GB hard drive in half; half for windows and half for ubuntu.  I'm just not sure how much of that 20 GB should be for the home directory, and how much should be for the other ubuntu partition.  Thanks for the help, guys

---

### Post by aysiu on 2005-12-12
Are you going to have a FAT32 partition to share files between Windows and Ubuntu, or will all your files live on Ubuntu? By files I mean documents, pictures, music, etc.

---

### Post by John Jason Jordan on 2005-12-12
Like Trumpetman, I'm in the university (but finals were last week -- Yay!!). I have a laptop with Ubuntu Breezy 64-bit and I want to back it up. My needs are similar to his. I have an external USB 60 Gb pocket drive mounted as /media/usbdisk.

Simple Backup looks really good. Only problem is it doesn't seem to work.

First, I created a folder on the USB drive "Simple." Then I went through Simple Backup's configuration and set it to back up everything from / to this folder. I also went into the Exclude tab and removed all the exclude items (like I DO want my mp3 files backed up!). I told it to Save and then I clicked on Start Backup Now. 

The hard drive light on the laptop flashed a bit, and four small files were created on the USB drive in a folder with today's date and the time of the backup. But the tar.gz file never showed up. I waited hours, but no backup was ever created.

Then I read more about Simple Backup on its wiki page and evidently there is a problem writing to external media. So I set the configuration back to the default folder /var/backup and tried again. This time it made six files in a folder with today's date and the time of the backup in /var/backup, and one of them was a tar.gz file. However there was never a message that it finished. After hours and the tar.gz file remained the same I concluded that it was done. But the tar.gz file was only 528 Mb. Before doing this I knew that 12 Gb of the 60 Gb hard disk on this computer is used. I know tar is compressed, but that doesn't seem possible.

So then I went back and double checked the Include and Exclude tabs and told it to make another backup, also to var/backup -- I changed nothing. Still told it to back up everything. This time it created a new folder with the date and time, and four small files inside it. But again, no tar.gz file was created.

So then I deleted all the folders and files from the USB disk and from /var/backup, and told it to make another backup. This time it did nothing at all. Not even a folder. I've tried all kinds of things, but it no longer seems to function at all.

There is another problem with it. You have to be root to run it, and all the folders and files it creates (if it actually does create them) are owned by root. You can't change, delete or move such files in Nautilus unless you launch Nautilus from the command line as root. This is a PITA.

There isn't much about Simple Backup on their wiki page. Does anyone know of another place where there is more information, troubleshooting tips, and discussion about it?

---

### Post by TrumpetMan258 on 2005-12-12
I guess the best thing to do would be to share files.  So my home partition should be FAT32 then?

---

### Post by rplantz on 2005-12-17
Simple Backup just saved me a lot of work. I did something really stupid and deleted my entire home directory. Fortunately, I had done a backup onto an external (usb) disk a few days ago.

I did not completely trust SB, so I also used tar cvfz on my important directories and copied the .tgz files to the external disk. (I did that so I would not lose modification dates.)

Well, Simple Backup Restore worked just fine. Whew!

By the way, the really stupid thing I did was to rm my /chroot/ directory. Installation wasn't going well, so I decided to start over. And, I had just read a warning against deleting the home directory in /chroot/.:oops: The stuff that increases my wisdom. :-)

---

