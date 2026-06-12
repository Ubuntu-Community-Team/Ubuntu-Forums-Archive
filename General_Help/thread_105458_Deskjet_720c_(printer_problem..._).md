---
title: "Deskjet 720c (printer problem... )"
date: 2005-12-18
forum: General Help
---

### Post by mztriz on 2005-12-18
I'm having some problems with this printer, it prints out papers but cuts off the top of everything that I print. For instance, if I were to print a paper like this 

"Ozone is a kind of oxygen that has three atoms per molecule, 03.
This is not much of a difference from the air we breathe, 02.

Ozone-- Harmful or Helpful?
The small chemical difference between oxygen and ozone greatly affects the planet around"

the entire top part is cut off and I am left with
 "The small chemical difference between oxygen and ozone greatly affects the planet around"

Printed on the paper... What should I do?

---

### Post by zoiks on 2005-12-18
Hmm.  That's a tough one.  Sometimes the drivers don't work out-of-the-box.  I've had to try different drivers for the same printer before, but in your case it seems ubuntu may have only one driver.  Another thing I've done that helps is to try drivers for similar-looking printer models.  For example, see if you can get it to print using the 710C, 712C, or 722C drivers.  Just a guess.

---

### Post by mztriz on 2005-12-18
Okay, thank you I will try doing so.

---

### Post by mztriz on 2005-12-18
[QUOTE=zoiks]Hmm.  That's a tough one.  Sometimes the drivers don't work out-of-the-box.  I've had to try different drivers for the same printer before, but in your case it seems ubuntu may have only one driver.  Another thing I've done that helps is to try drivers for similar-looking printer models.  For example, see if you can get it to print using the 710C, 712C, or 722C drivers.  Just a guess.[/QUOTE]

I just tried all of those and it still cuts off the top of my page, maybe it is something with my settings? [http://img335.imageshack.us/img335/3532/screenshotdeskjet720cpropertie.png](http://img335.imageshack.us/img335/3532/screenshotdeskjet720cpropertie.png)

---

### Post by mztriz on 2005-12-18
Another thing I have noticed is that the printer only works correctly when printing through the text editor, the only problem with this is I have to print out ceritan things with different formatting such as colums etc and thoes do not work with the text editor. The printer does not work correctly in any browser either (it keeps cutting off the top of the page)

---

### Post by mztriz on 2005-12-18
[QUOTE=mztriz]Another thing I have noticed is that the printer only works correctly when printing through the text editor, the only problem with this is I have to print out ceritan things with different formatting such as colums etc and thoes do not work with the text editor. The printer does not work correctly in any browser either (it keeps cutting off the top of the page)[/QUOTE]
Any Ideas I really need to print some things for tomorrow :(

---

### Post by mztriz on 2005-12-18
:(

---

### Post by zoiks on 2005-12-18
[QUOTE=mztriz]I just tried all of those and it still cuts off the top of my page, maybe it is something with my settings? [http://img335.imageshack.us/img335/3532/screenshotdeskjet720cpropertie.png](http://img335.imageshack.us/img335/3532/screenshotdeskjet720cpropertie.png)[/QUOTE]

I don't know, I'm not that keen on the printer drivers.  Does a "Print Preview" look the same as a printout?  That might be another clue.  Did you change any of the settings before trying to print?  Does the printer work fine from another OS?

---

### Post by mztriz on 2005-12-19
[QUOTE=zoiks]I don't know, I'm not that keen on the printer drivers.  Does a "Print Preview" look the same as a printout?  That might be another clue.  Did you change any of the settings before trying to print?  Does the printer work fine from another OS?[/QUOTE]
yes, i have looked in print preview and it looks normal. I haven't tried chaning the settings of the printer but i have shown the settings to a few people and they said the settings were normal too. The printer worked fine in windows

---

### Post by hajk on 2005-12-19
I had a similar problem with my HP DeskJet 5850 network printer, installed via System/Administration/Printing: whatever I tried, the test page would always have the top 2.5cm cut off...

Somebody pointed me to the new HP Linux Imaging and Printing (HPLIP) setup, which is already running in Breezy by default. When installing the printer don't choose HP as manufacturer, but HP (HPLIP), then select your printer as usual from the list and accept the suggested driver. The test page printed fine in my case. (Another problem in my case was how to supply the printer network address... but that's another story.)

So I recommend HPLIP, try it.

---

### Post by mztriz on 2005-12-19
[QUOTE=hajk]I had a similar problem with my HP DeskJet 5850 network printer, installed via System/Administration/Printing: whatever I tried, the test page would always have the top 2.5cm cut off...

Somebody pointed me to the new HP Linux Imaging and Printing (HPLIP) setup, which is already running in Breezy by default. When installing the printer don't choose HP as manufacturer, but HP (HPLIP), then select your printer as usual from the list and accept the suggested driver. The test page printed fine in my case. (Another problem in my case was how to supply the printer network address... but that's another story.)

So I recommend HPLIP, try it.[/QUOTE]

okay, I will try this thank you very much :) I hope it works...

---

### Post by mztriz on 2005-12-19
[QUOTE=mztriz]okay, I will try this thank you very much :) I hope it works...[/QUOTE]
I just installed HPLIP but I have no idea where it went...

---

### Post by mztriz on 2005-12-19
[QUOTE=hajk]I had a similar problem with my HP DeskJet 5850 network printer, installed via System/Administration/Printing: whatever I tried, the test page would always have the top 2.5cm cut off...

Somebody pointed me to the new HP Linux Imaging and Printing (HPLIP) setup, which is already running in Breezy by default. When installing the printer don't choose HP as manufacturer, but HP (HPLIP), then select your printer as usual from the list and accept the suggested driver. The test page printed fine in my case. (Another problem in my case was how to supply the printer network address... but that's another story.)

So I recommend HPLIP, try it.[/QUOTE]

When I go to system>administration>printing it doesn't list HPLIP?

---

### Post by mztriz on 2005-12-19
ahh wait i found it ok i'm trying this..

---

### Post by mztriz on 2005-12-19
now I have yet another problem [http://img450.imageshack.us/img450/5553/screenshotaddaprinter9ub.png](http://img450.imageshack.us/img450/5553/screenshotaddaprinter9ub.png) deskjet 720c isn't listed?

---

### Post by mztriz on 2005-12-19
I hate to do this but I had to put the printer in my brothers room, working fine now in windows.

Thank you to everyone who tried to help me, I really apprecaited the effort :D

---

### Post by jxt on 2005-12-29
[QUOTE=mztriz]now I have yet another problem [http://img450.imageshack.us/img450/5553/screenshotaddaprinter9ub.png](http://img450.imageshack.us/img450/5553/screenshotaddaprinter9ub.png) deskjet 720c isn't listed?[/QUOTE]

Hello all. I think I'm about to face a similar problem. I have an old HP 720c printer that I got with an old win95 box about eight years ago. The printer still has life in it, and I would like to recyle the printer to a Breezy Badger box that I'm setting up for the first time. Alas, I think the 700-series printers are somehow windows-only printers. Not sure why -- maybe the drivers rely on something in the windows os -- but I still can't understand why a Linux driver couldn't be written for it.

Has anyone ever gotten an HP 700-series printer to work in Ubuntu? If so, how?

Thanks.

---

### Post by jxt on 2005-12-29
[QUOTE=jxt]Has anyone ever gotten an HP 700-series printer to work in Ubuntu? If so, how?
[/QUOTE]

Well, this may be a "nevermind." I found this thread [http://ubuntuforums.org/showthread.p...t+720c+print](http://ubuntuforums.org/showthread.p...t+720c+print). I'll try that over the weekend and see how it works for me.

---

### Post by dixonstalbert on 2006-01-02
hi guys 

not sure if you saw this post by mr. guiri.
The post link above doesnt work for me so I have copied and pasted his post here
It finally got my 710c to work! thanks mr. guiri
 
Re: HP Printer doesn't print in Breezy. Solved with a hp 710c - 10-19-2005 

--------------------------------------------------------------------------------

I had have similar problem with a hp 710c

The solution was in the /etc/pnm2ppa.conf
I use pnm2ppa because 710 is only supported by this
In this document apears the following text

#-----------set the printer model---------------------------
# The printer model will normally be set by a -v <model> command
# line argument. Otherwise, if not set in the configuration file
# it defaults to the 710/720 series. Remove/comment out the line
# "version 0" below to get the default choice.
#
# If there is more than one "version" entry activated, the last one
# will be used. The printer version can also be set with the command line
# option e.g., "-v 720".

version
#version 720 # 710, 712, 722 also acceptable
#version 820
#version 1000

I only have to put the model in the version line
the tex now is

#-----------set the printer model---------------------------
# The printer model will normally be set by a -v <model> command
# line argument. Otherwise, if not set in the configuration file
# it defaults to the 710/720 series. Remove/comment out the line
# "version 0" below to get the default choice.
#
# If there is more than one "version" entry activated, the last one
# will be used. The printer version can also be set with the command line
# option e.g., "-v 720".

version 710
#version 720 # 710, 712, 722 also acceptable
#version 820
#version 1000

I suppose that with anothers printers the system configuration tool don't select the printer.

--------------------------------------------------------------------------------

Last edited by guiri : 10-19-2005 at 12:41 PM.

---

