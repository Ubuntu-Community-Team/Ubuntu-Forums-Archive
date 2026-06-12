---
title: "&quot;unknown/glibc-2.0&quot;  error"
date: 2009-07-03
forum: Gaming &amp; Leisure
---

### Post by lowping on 2009-07-03
Hola!

I've been trying to install Quake3Arena and am unable to install the necessary 'point release' files.  At the bottom of this post I will paste tutorial I am using for reference. 
The error I am currently stuck on is this:

$ [COLOR=Navy]sudo sh /usr/local/games/quake3/linuxq3apoint-1.32b-3.x86.run [/COLOR]
[INDENT]Verifying archive integrity... [COLOR=DarkGreen]All good[/COLOR].
Uncompressing Quake III Arena Point Release 1.32b..............................................................................................
This installation doesn't support glibc-2.0 on [COLOR=DarkRed]Linux / unknown[/COLOR]
(tried to run setup)
The setup program seems to have failed on [COLOR=DarkRed]unknown/glibc-2.0[/COLOR]

[/INDENT]Any and all help is greatly appreciated  :)
I am running Ubuntu 9.04_64-bit


----------------------------------------------------------
Originally posted by "Obsidian" on Oct31 2006

Installing Quake III Arena on a 64-bit Linux box isn't that bad actually. I couldn't find instructions anywhere on how to do this, so after figuring it out I'm writing them down here.
[COLOR=#FF9933]**You will need:**[/COLOR]


[LIST]
[*]Linux x86_64 with updated video drivers
[*]Quake III Arena install CD (Windows)
[*][Linux Q3A Point Release 1.32b]("ftp://ftp.idsoftware.com/idstuff/quake3/linux/linuxq3apoint-1.32b-3.x86.run")
[*][Q3A Point Release 1.32c]("ftp://ftp.idsoftware.com/idstuff/quake3/quake3-1.32c.zip")
[/LIST]
Download the two point releases somewhere handy. I just downloaded them to my Desktop (/home/obsidian/Desktop)
[COLOR=#FF9933]**Installation:**[/COLOR]


[LIST=1]
[*]Open up a Terminal session and create a new directory to install everything (usually /usr/local/games/).
[LIST]
[*]sudo mkdir -p /usr/local/games/quake3/baseq3
[/LIST]
[*]Insert Q3A CD in your drive and copy the pak0.pk3 file to your baseq3 directory (can take a while).
[LIST]
[*]sudo cp /media/cdrom/Quake3/baseq3/pak0.pk3 /usr/local/games/quake3/baseq3
[/LIST]
[*]Quake 3 is a 32-bit application, so you will run into a [known issue]("http://zerowing.idsoftware.com/linux/q3a/#64bits"). You can get around this by installing a couple of packages that will allow you to emulate 32-bit programs in your 64-bit environment.
[LIST]
[*]sudo apt-get install ia32-libs linux32
[/LIST]
[*]We can now invoke the Quake 3 install script to work. Note that your directory may be different than below. Then follow the on-screen instructions, they should be pretty self explanatory.
[LIST]
[*]sudo linux32 sh [COLOR=#999999]/home/obsidian/Desktop[/COLOR]/linuxq3apoint-1.32b-3.x86.run
[/LIST]
[*]Extract the 3 files in the "linux" directory of quake3-1.32c.zip to your desktop (or where ever else) and copy them over to your Quake 3 install directory.
[LIST]
[*]sudo cp[COLOR=#000000] [COLOR=#999999]/home/obsidian/Desktop/1.32c[/COLOR]/* /usr/local/games/quake3[/COLOR]
[/LIST]
[/LIST]
[COLOR=#FF9933]**Notes:**[/COLOR]

[LIST]
[*]Most distros use *su* instead of *sudo*.
[*]x86_32 users can follow the same process, but omit step 3, and do *sudo sh /home/obsidian/Desktop/linuxq3apoint-1.32b-3.x86.run* on the last step instead.
[/LIST]
Have yourself a little fragfest.

---

### Post by Machiavelli on 2010-10-18
Just install q3pointrelease_132.exe thru wine at the base3q folder and you should be fine.

---

