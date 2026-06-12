---
title: "Screensaver has locked"
date: 2009-11-18
forum: Desktop Environments
---

### Post by Eathray on 2009-11-18
My screensaver has locked in 9.04:

I reset my timeframe to 2 hours so that I and my kid could watch movies, then we started going through the choices of screensavers, deciding which one to pick. We came upon one called "Molecules" and decided to have a look. The screen went black, and written on the top left was "Constructing Molicules..."

It is now locked, and will not do anything once it reaches that point. The computer has to be restarted. The mouse curser turns black. It will not allow you to select a different screensaver. I have even tried reinstalling the Screensaver from the Synaptic Package Manager, and it does nothing.

I believe I need a code to enter from the terminal telling it to reset itself to the default settings of the Screensaver. Does anyone have such a command line?

Your help will be greatly appreciated.

Thx.

Eathray

---

### Post by Eathray on 2009-11-18
Can anyone help me out on this one?

Please?

Eathray

---

### Post by Eathray on 2009-11-19
Help please...

Eathray

---

### Post by karlson on 2009-11-19
> **Eathray said:**
> My screensaver has locked in 9.04:

I reset my timeframe to 2 hours so that I and my kid could watch movies, then we started going through the choices of screensavers, deciding which one to pick. We came upon one called "Molecules" and decided to have a look. The screen went black, and written on the top left was "Constructing Molicules..."

It is now locked, and will not do anything once it reaches that point. The computer has to be restarted. The mouse curser turns black. It will not allow you to select a different screensaver. I have even tried reinstalling the Screensaver from the Synaptic Package Manager, and it does nothing.

I believe I need a code to enter from the terminal telling it to reset itself to the default settings of the Screensaver. Does anyone have such a command line?

Your help will be greatly appreciated.

Thx.

Eathray

When the molecules first comes up it had the same affect on me.  My advise would be to login to the machine from another host on the network and kill the molecule process.

I was able to run the screensaver configuration afterwards.

---

### Post by Eathray on 2009-11-19
Okay, I found great directions and it fixed my screen saver, so I wanted to share with everybody:

[http://ubuntuforums.org/showthread.php?t=550126](http://ubuntuforums.org/showthread.php?t=550126)

Also, here are the pertinent directions:

[INDENT][INDENT] 				 				***Re: How do I reset the screensaver?*** 			
 			 			 		   		 		 		[I]Few steps that takes 11 minutes... just kidding.

Right click the Ubuntu logo in the top left corner.

goto edit menus

from the menu column select system tools

under the items column select configuration editor

hit close at the bottom right


Now click Applications > System tools > Configuration editor

got to on the left column  / > apps > gnome-screensaver

next within the right column scroll down to "themes" double click it

remove the theme from the values list and hit OK.



That should be it.[/I]             


[/INDENT][/INDENT]These exceptional directions came from Technophobia, going all the way back to Sept. 2006.

Thanks to Karlson, the only person to reply to my thread ;)

Thanks to Revord for posting his identical screensaver problem and Technophobia for the clearest Ubuntu instructions ever.

Really coming to enjoy Ubuntu, by the way.

Eathray

---

