---
title: "Install printer, Cups, and Kprint"
date: 2005-08-09
forum: Desktop Environments
---

### Post by Chan on 2005-08-09
Has any body come across literature or websites, that spells out to Newbies (that have used Windoze for years),  on how to install a printer (Canon i560), then how to make sure Cups is properly installed, and finally how to make sure that KPrint is installed properly.  I know this sounds like a tall order, but I've been laboring for weeks on trying to get a print system working.  I've looked in a lot of places, but not the right one, yet.  As a Newbie, I don't have enough background to know the relationship of all the pieces in the puzzle, and how to make "em shake hands.

Any good references to the overall printing arrangement in Kubuntu would be very much appreciated.  Thanks a lot for reading this.  Chan   ](*,)

---

### Post by rosslaird on 2005-08-09
It's easy to become bewildered by the complexity of cups in particular. It's an arcane system. And you could read through lots of guides before finding a solution. Why don't you tell us exactly what's going on with your printer? What happens when you try to set it up through the control center? Where are you getting stuck?

You can test to see if cups is working properly by typing this into a terminal:

sudo /etc/init.d/cupsys restart

This will restart the cups system, and if it fires up OK it will just say [ok]
If that works, you're halfway there. Then what's the next issue?

Ross

---

### Post by coolclassic on 2005-08-09
If printing doesn't work first time with linux it can be difficult to set up for new users. I found a package from turbo print very usefull, configuration is very easy by just following instructions for the tgz.

[http://www.turboprint.de/english.html](http://www.turboprint.de/english.html)

---

### Post by drizek on 2005-08-10
i installed an hp printer in kubuntu in under 5 minutes. just went into printer settings in kcontrol, clicked "add printer," picked the port(it displayed which port the printer was connected to, i just had to confirm). picked the driver, clicked next, printed a test page, and it worked. 

have you tried setting it up using kcontrol or what?

---

### Post by Chan on 2005-08-12
Re rosslaird, and drizek,it appears that while Cups is installed, the Canon i560 is not.  ( Actually, I am trying to load a driver for a Canon BJC 7000, because it's so difficult to get a driver/PPD file for the i560).  I just can't seem to get an acknowledgement that the printer is actually installed, even though it should have installed from each of the three approaches I've taken.  

I need a single approach that is complete and has worked for someone.  An approach that can be followed keystroke by keystroke.  What may be throwing me off is that there are so many different files that have the word "Print" contained in them, and I'm not familiar enough with Linux to know what folder/ directory to go to for the RIGHT ones.  

My career in Linux is so short, that I'm having a tough time getting around, because I don't know what folders are used for what purpose.  None of the books that I have will  take me thru a complete download, filing it, and installing it.  I guess that before I can do anything useful, that I will have to devote a lot more time studying the vernacular.  In the meantime, I could use some detailed info on how to get this printer installed.  I need an online source of  "How To's" for Newbies.  Any suggestions?  Thanks, Chan

---

### Post by coolclassic on 2005-08-13
As some new to linux there is a simple solution at: [http://www.turboprint.de/english.html](http://www.turboprint.de/english.html)
The instructions give on the there web site are clear and easy to follow.

---

### Post by Footer on 2005-08-15
[QUOTE=Chan]I need a single approach that is complete and has worked for someone.  An approach that can be followed keystroke by keystroke.  What may be throwing me off is that there are so many different files that have the word "Print" contained in them, and I'm not familiar enough with Linux to know what folder/ directory to go to for the RIGHT ones.[/QUOTE]

Well, I have a Dell A920 AIO which is actually a Lexmark X1150 AIO that uses the Lexmark Z601 driver.  I used the instructions at this link:

[INDENT][http://members.cox.net/twsnnva/Linux.html](http://members.cox.net/twsnnva/Linux.html)[/INDENT]
scroll to the bottom and look under the section "Setting up printing".  He mentions the Canon i860 which may be similar to your printer ... dunno for sure.  The trick is to find and install the correct drivers.

Good luck and I hope this helps a little!

---

### Post by incinerator on 2005-08-15
A good website to check if your printer is supported is
[http://www.linuxprinting,org/](http://www.linuxprinting,org/)
If you cannot find your printer in their database you will have to check your manual or google around in order to find out if there is a supported printer yours is compatible with.

For your Canon i560 quick googling revealed that you can treat it as a BJC7000.

Kubuntu (actually KDE) comes with a very sophisticated printer setup application. All the necessary software to use printers should have been installed by default, at least that was the case with my Kubuntu Hoary install. Use that "Printers" application to set up your printer.

Once you got your printer running it would be nice if you'd made some effort to tell the guys'n'gals at linuxprinting.org that your printer works.

Also, linuxprinting.org offers advice on which printer to buy to make sure you get the best out of it with GNU/Linux.

Regards,
Dominik

---

