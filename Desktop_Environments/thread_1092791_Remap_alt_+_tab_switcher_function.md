---
title: "Remap alt + tab switcher function"
date: 2009-03-10
forum: Desktop Environments
---

### Post by nolanpro on 2009-03-10
I'm using intrepid on a macbook and I'm trying to figure out how to remap the switcher (alt+tab) to apple+tab (super key) instead. The problem is that I've gotten use to this functionality on windows and mac probably more than is good for me and I've gotten use to the positions of the keys. Hitting alt/option and tab to switch just feels wrong.

I've played around with xbindkeys but I don't think that program can execute a set of key commands, only terminal commands.

---

### Post by fatbuttlarry on 2009-04-15
> **nolanpro said:**
> I'm using intrepid on a macbook and I'm trying to figure out how to remap the switcher (alt+tab) to apple+tab (super key) instead. The problem is that I've gotten use to this functionality on windows and mac probably more than is good for me and I've gotten use to the positions of the keys. Hitting alt/option and tab to switch just feels wrong.

I've played around with xbindkeys but I don't think that program can execute a set of key commands, only terminal commands.
Edit:  I booted the live Jaunty CD (9.04 beta) and figured this out... 

For Gnome Users:
[FONT=Courier New][COLOR=Red]     System --> Preferences --> Keyboard
     Layouts Tab --> Layout Options
     Alt/Win Key Behavior --> Left Alt is swapped with Left Win[/COLOR][/FONT]

For KDE 4.x Users:
[FONT=Courier New][COLOR=Red]System Settings --> Regional and Language
Keyboard Layout --> Layout Tab --> Enable Keyboard Layouts
Advanced Tab --> Alt/Win key behavior --> Left Alt is swapped with Left Win[/COLOR][/FONT]



This may differ slightly on Intrepid, but the option should be there. [Here's a screenshot]("http://ubuntuforums.org/attachment.php?attachmentid=109928&stc=1&d=1239833678") of where it in in Jaunty.  Note that unlike the Xmodmap changes, this is immediate (you don't even have to close out the dialog to test it).

-Tres


-----------------------------------------------------------------


> Nolan,

I got it to work with Intrepid pretty easily (through the GUI, not though a series of commands).  Instructions for Feisty involved changing the [xmodmap for my keyboard]("http://www.linuxquestions.org/questions/linux-newbie-8/how-do-i-remap-alt-to-a-super-key-696858/") and actually broke my profile when upgrading to Intrepid, but Intrepid had the setting for sure.  [Here's the same tutorial on the Ubuntu message boards]("http://ubuntuforums.org/showthread.php?t=82729").

I'm not running gnome right now so I can't immediately offer instructions, but look at your keyboard preferences in gnome.  I want to say Intrepid has a common work-around for this.

[OSX users have it easy in this regard... :)]("http://www.macosxhints.com/article.php?story=20020319103828754")

I'm searching for an equal work-around for Kubuntu.  Cheers.

Post your success if any!

-Tres

---

