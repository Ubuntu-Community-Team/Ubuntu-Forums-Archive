---
title: "Need some Windows to Ubuntu migration tips"
date: 2006-08-09
forum: Desktop Environments
---

### Post by harisund on 2006-08-09
Hello everyone!

I have a Windows laptop right now, that is working just perfectly. I want to install Ubuntu mainly for work related purposes (yes, I use Linux at work :) )

Since practically everything I use on Windows is Open Source, I am guessing migrating my settings from Windows to Linux shouldn't be hard. 

These are what I want to migrate: 
(1) - Firefox profiles. 
(2) - Thunderbird profiles.
(3) - Gaim profiles. 
(4) - GnuPG keys 
And pretty much nothing else. I can copy over my ssh id;s from my Cygwin, use cygwin's .bashrc profile settings and so on. But the above 4 are very very important to me. I intend to be able to share between my Windows and Ubuntu installations, so I plan on having them on fat32 partitions. Does it require sudo permissions to write to a fat32 partition in Ubuntu? Will it work properly? 

Also, I want to know the following: currently what *can't* I do on AMD64 version of Ubuntu? I haven't been reading/ keeping up with the AMD64 Firefox optoins.

I am thinking of the following: 
-- Some stuff related to Firefox, I believe? Some plugins and stuff. I am not interested in chrooting. If flash doesn't work I don't care, since I will be ubuntu at work only anyway and Windows at home. 
-- Any other stuff? 

Thanks a bunch !

---

### Post by spin2cool on 2006-08-09
This is the solution that works best for me:

1) When installing Ubuntu, set up a FAT32 partition on your hard drive to be used for data that needs to be shared between Linux/Win.

2) Copy all of your Thunderbird Mail profile data, Firefox profile data and Gaim profile data there.

3) Now, use your profile managers (for firefox and thuderbird).  Create a new profile, and choose the folder where you copied your stuff.  Voila!  Everything should come up fine.

4) For Gaim, follow these instructions to point to the correct profile location: [http://www.novell.com/coolsolutions/tip/15232.html](http://www.novell.com/coolsolutions/tip/15232.html)


5) I've heard that some firefox extensions don't play nice when shared, but I've never experienced problems.  If you do, then go back to your default firefox profile in Linux and just use symlinks.  You'd delete history.dat, cookies.txt, user.js, prefs.js, and bookmarks.html, then link them to the ones in the windows profile.

---

### Post by harisund on 2006-08-09
Nice link. 

And thanks a lot for your suggestions. I will give them a try over the weekend. 

--hari

---

### Post by Bawl on 2007-04-22
[QUOTE=spin2cool;1360908]
4) For Gaim, follow these instructions to point to the correct profile location: [http://www.novell.com/coolsolutions/tip/15232.html](http://www.novell.com/coolsolutions/tip/15232.html)

Thx a bunch... That was exactly what I needed. Been looking for a way to change the location of GAIM logs and settings for 4 days, and BAM! here it is. ;)

Just one more question: [SIZE="2"]How do I get GAIM to start with these settings as default?[/SIZE]

---

### Post by Bawl on 2007-04-22
Never mind... Finally nailed it, all by myself... *proud*

**gaim -c /path/to/profile/**

Stystem=>Preferences=>Main Menu=>Internet=>GAIM and then Settings and (of course) changing the the command for the shortcut...

And of course: System=>Preferences=>Sessions and just add the same command as in the shortcut above, and voila! It starts along with your session, everytime you boot...

Dead simple and yet sooo hard to figure out when you're still heavily influenced by the Windows-Way-of-Thinking. ;)

---

