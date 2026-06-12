---
title: "gDesklets : IRC sensor not found"
date: 2005-11-11
forum: Desktop Environments
---

### Post by DeadcAlm on 2005-11-11
I have searched thru the forums with little luck in finding someone who has had this problem.  Either because I'm doing something wrong, or nobody else uses this particular desklet :)

I am running Ubuntu 5.10.  I have recently installed the gDesklets Shell along with the gdesklets-data package.  There are a few desklets that wont start for this reason or that, I'm sure it's just stuff I don't have installed that I should.  The IRC desklet is one of these that wont start.

irc ver. 1.0 by Seth Remington
when I start the desklet, I get the message box:

Could not find sensor 'irc'
/usr/share/desklets/Displays/irc/irc.display

A sensor could not be found.  This usually means that is has not been installed.

So...I went to the gdesklets.gnomedesktop.org site to investigate.  I found the very same irc desklet and saw that I must have Twisted Python installed.  As it turns out, I already have it.  Synaptic says i have version 2.4.  The IRC desklets doesn't actually say what version of Twisted I need, so I going with what I've got.  I went ahead and downloaded the irc-1.2.tar.gz from gnomedesktop.org which said that it contained both the sensor and display.  I then installed the desklet with the desklet manager and attempted to start it.  I get the very same error message as the first time, but that the path it looked in was in my home directory.

I'm assuming there's this small easy step that I'm missing, but I need someone to point it out to me.  Thanks in advance for any help.  Let me know what other information would be helpful.

---

### Post by Kyral on 2005-11-11
One note that in general the GDesklets-Data package is busted...

---

### Post by DeadcAlm on 2005-11-11
I was afraid of that.  Is it something that has enough users to actually get fixed?  Hmmm, is the KDE version any better?

---

### Post by Kyral on 2005-11-11
You mean SuperKaramba? I haven't had enough experiance with it, but I haven't heard anything bad. If you want to get GDesklets to work you should uninstall the gdesklets-data package and manually install the Desklets from the site. Actually allows you to drag and drop the link into the "GDesklets Shell" window to install IIRC

---

### Post by DeadcAlm on 2005-11-11
I don't recall the name of the KDE version either.  I actually did uninstall the gdesklets-data package and install the irc package directly.  Unfortunately it didn't fix my problem.  I am somewhat concearned though, the version or irc that came with gdesklets-data said it was version 1.0 but the latest version is supposed to be 1.2.  When I installed the package from gdesklets.gnomedesktop.org, it showed up as 1.0 as well.  I don't know if that's just a bug in the conf file for the package or what.  I'm going to email the author to see if he has any ideas.

---

