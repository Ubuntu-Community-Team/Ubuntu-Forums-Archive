---
title: "Help finding  w32codecs"
date: 2005-09-22
forum: Desktop Environments
---

### Post by MButterman on 2005-09-22
Just recently converted from Windows XP Pro to Unbuntu Warty Hedgehog and I have a few questions.

1. with mplayer plugin there is a package named "w32codecs" I require to finish this installation, I have tried to use synaptic to locate this with no success thus far. I have learned to add repositories to synaptic. Does anyone have repository information for this package?

2.Being new to this, Is there any reference books I can purchase to learn the commands of Ubuntu.

3. I use Kb3 and have it working but I would like to add its Icon to the panel so I don't have to goto run application everytime I wish to use it.

Thanks for the help and I look forward to using my new Ubuntu system and getting to know the forums and it's membership

MButterman

---

### Post by mlomker on 2005-09-22
> 
Thanks for the help and I look forward to using my new Ubuntu system and getting to know the forums and it's membership


You can start by reading through the [Ubuntuguide](http://www.frankandjacq.com/ubuntuguide/5.04/index.html).  

The Mplayer codecs were removed from the repositories, probably for legal/copyright reasons.  You can still download and install them from the [mplayer website.](http://www.mplayerhq.hu/homepage/design7/dload.html) If you search the forum you'll find plenty of posts regarding this.

---

### Post by John.Michael.Kane on 2005-09-22
You could also get your machine up and going, with this [http://ubuntuforums.org/showthread.php?t=30147](http://ubuntuforums.org/showthread.php?t=30147)

---

### Post by MButterman on 2005-09-22
Appreciate the help, any takers on the kb3 question?   :) 

All My Best,
MButterman

---

### Post by Blue1k on 2005-09-23
right click on your desktop and choose "create launcher"

In command name choose "k3b".
For your icon browse to /usr/share/icons-because it is a KDE app browse the kde folder in usr/share/icons and you will find the K3B icon :smile:

---

### Post by MButterman on 2005-09-23
Thanks for the information, I have a few glitches though

1. Add and Remove Applet no longer shows installed applications

2. mplayer plug in will show the web address for the streaming content and it indicates it's playing content (quicktime) but no playback occurs. In WMP it plays the audio but doesn't play the video part.

3. During the automated installation, it attempted to installed Real Player, Sticking to the defaults provided, installer was not able to find the installation package for this application. I have the icon in the menu but it does nothing when selected.

4. there are 3 pakages that are being ignored for upgrade. Using the Update manager it suggest running the smart update though synaptic which also ignores these packages. I also attempte apt-get dist-upgrade to also update packages with no success.

Everything else is in place and working, anybody else had these problems please let me know how you corrected it. Thanks again.

All My Best,
MButterman  :)

---

### Post by MButterman on 2005-09-24
Friends, Romans and Countrymen, Lend me your ear.  : :grin:  
Ignore my last post, The newbie section had all the neccessary fixes for my issues.  :idea:   It's funny what you learn when you RTFM !! I hope you don't mind keeping you in mind for the tougher questions.

All My Best,
MButterman

---

### Post by xthaparian on 2005-09-29
[QUOTE=MButterman]Appreciate the help, any takers on the kb3 question?   :) 
All My Best,
MButterman[/QUOTE]
Here is the Deal

Do this in the terminal

$ sudo gedit /usr/share/applications/k3b.desktop

Now add the Following Lines in the new file

[Desktop Entry]
Name=K3B
Comment=Excellent tool for Burning
Exec=k3b
Icon=**_Path to the icon you want to use_**
Terminal=false
Type=Application
Categories=Application;Utility

Now after doing this..save this file
now at terminal do

$sudo killall gnome-panel

and check the Drop down from top..you should see the K3B icon in the Accessories category.
:)

---

