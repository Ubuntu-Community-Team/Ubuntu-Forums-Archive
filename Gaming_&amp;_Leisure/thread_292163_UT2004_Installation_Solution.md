---
title: "UT2004 Installation Solution"
date: 2006-11-03
forum: Gaming &amp; Leisure
---

### Post by Jvaldezjr on 2006-11-03
While this is not meant to be an end all be all solution for UT2004, if you search these forums and a few other ubuntu sites, there are other ways of getting this game installed with no problems.

However, I tried all those other methods listed, and I still had problems, so this was the way I came up with.

First download the necessary patches, packs and mods you will need to update UT2004.  You can get more info from [this link]("http://liflg.org/?catid=6&gameid=17")

Now insert and mount, one at a time, each UT2004 CD or DVD and copy them directly onto a folder on your harddrive.  The purpose of this step is to convince UT2004 that you have all the data in one place to install from.  This will help solve problems for having to switch CDs when prompted by the installer.

ISSUE: If you specify the install directory on the installer, other than what is already listed as the default directory- the installer will put a "/" at the end.  This causes problems because when files are copied, they get copied to "/your_directory//" instead of being copied to "/your_directory/".  A better example is this- if you run the installer with user privledges, the default install directory is /home/foo/ut2004.  If I changed that to something else like /home/foo/game/ut2004, the  installer then puts a "/" at the end of it- giving me /home/foo/game/ut2004/, which causes the copy problem of having files copied to /home/foo/game/ut2004//.  So, unless there is a better way of running the installer, or someone knows how to edit the install script to stop doing this.

NOTE: You may see an error message about copying a file "Help/ut2004.ico" or something to that effect.  It is ok to skip that error and continue copying.  That is a MS Windows icon file, and the installer ends up copying an XPM file that you can use in linux for a UT2004 icon.

```
mkdir ut2k4Setup	# copy all cds/dvds to this directory

```
Now you are ready to install ut2004
```

export SETUP_CDROM= <path to>/ut2k4Setup
```

Example- I installed my CDs to /home/elektra/ut2004CD, this needs to be the path that you set the variable SETUP_CDROM.

```
cd ut2k4Setup
sh linux-installer.sh
```

Follow the prompts, and the installer will begin copying from your SETUP_CDROM path.  If all goes well, everything should copy as normal.  Some of my CDs had issues copying files over, so I had to re run the installer a few times.  After it completes, you should be able to play the game by ./ut2004 from the installation directory.

I installed this on Kubuntu 6.06- and should work for other versions of Ubuntu.  Read the resource information from the following links to get help with patch updates, and module add ons.

[http://ubuntuforums.org/showthread.php?t=8140]("http://http://ubuntuforums.org/showthread.php?t=8140")
[http://gaming.gwos.org/index.php?option=com_content&task=view&id=75&Itemid=63]("http://http://gaming.gwos.org/index.php?option=com_content&task=view&id=75&Itemid=63")

Another way of installing this is figuring out what the files are that get copied by the installer, and copying them all directly to your directory of choice, and possibly having to change config files to get the game to run right.  I haven't figured that out yet.

Have fun!

---

