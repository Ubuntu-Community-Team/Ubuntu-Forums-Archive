---
title: "Avant-Window-Navigator Startup Problem"
date: 2007-04-06
forum: Desktop Effects &amp; Customization
---

### Post by FrostyFlames on 2007-04-06
Followed this HowTo to install AWN : [http://awn.wetpaint.com/page/Ubuntu+Edgy+Repository](http://awn.wetpaint.com/page/Ubuntu+Edgy+Repository)
I also followed this to install Beryl: [http://forum.beryl-project.org/viewtopic.php?f=36&t=4781](http://forum.beryl-project.org/viewtopic.php?f=36&t=4781)

AWN works fine when I run it from a terminal. The problem I have is that when I go to "System -> Preferences -> Sessions" and click on the Startup Programs tab I can add it (I add either "/usr/bin/avant-window-navigator" or "avant-window-navigator" but not both) and then close it. I reboot and AWN does not load up. I check the Startup Programs tab in the Sessions preference and it's looks like it didn't save and has no listing of the AWN command.

So my question is how the heck can I get AWN to load up with out constantly running a terminal?

---

### Post by PaulFXH on 2007-04-07
That's weird. I didn't do any more than you (although I installed the SVN version--you didn't say which you installed) and put "avant-window-navigator" in Start Up Sessions and it loads fine at Start Up every time.
Does AWN show up in Applications>Accessories?

---

### Post by phoenixfirebird on 2007-04-07
Mine starts up fine, but only on one desktop, I have to manually start it on the other ones

---

### Post by brokencrystal on 2007-10-19
Not working in Gutsy.  Seems that when I close the sessions manager window after adding it, or anything for that matter, it is lost next time I open the sessions manager window again.  I cannot get AWN added to my Gutsy startup for anything.  I need it to load after compositing, yet Ubuntu Gutsy seems to have a major error with their sessions manager program.  Should this be turned in to Ubuntu as an error report?  "Faulty Sessions Manager"  If anyone has this problem with the Sessions Manager in Gutsy, please feel free to report it as a bug as I don't have the extra time at the moment.

Please let me know if anyone else has this problem.  

Thanks

---

### Post by brokencrystal on 2007-10-19
UPDATE:

If I type "sudo gnome-session-properties" in a terminal, I can add new items to startup, and they save if I go back to terminal and type "sudo gnome-session-properties" again and look.  However, this does not solve the problem.  If I go to System>Preferences>Sessions again, it's not there and will not save.  It only saves if I enter the program using sudo from command line.  It still does not startup when I log in.  This means that I can't start anything from the sessions manager in Gutsy!  I can't auto start screenlets, AWN, or anything.

Any assistance or work-arounds would be appreciated.

Thanks again

---

### Post by brokencrystal on 2007-10-19
UPDATE: UPDATE:

I submitted a bug report.  It can be found here:
[https://bugs.launchpad.net/ubuntu/+bug/154685]("https://bugs.launchpad.net/ubuntu/+bug/154685")

---

### Post by brokencrystal on 2007-10-19
UPDATE: UPDATE: UPDATE:

I figured out a work-around to get by for now...

Just make a launcher and put it in /usr/share/gnome/autostart and it will add it to the Startup Tab of the Gnome Sessions Manager.

I hope this work-around makes someone happy!   :guitar:

---

### Post by Depressed Man on 2007-10-28
Thanks! I've been trying to get it working. Never got around to filing the bug report though since I thought it was just me.

---

### Post by smolloy on 2007-10-30
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/154685](https://bugs.launchpad.net/ubuntu/+bug/154685) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Check your ~/.config/autostart/. When I looked at mine, autostart was a file, not a directory. I looked at the file and saw info about screenlets. I checked the screenlets install and saw that it created the autostart file. I fixed this by deleting autostart and creating an autostart directory. The file "screenlets-daemon.desktop" from the screenlets package will need to be copied into this new autostart directory. I am now able to add programs to the startup list and they stay! I put this information into the bug report listed above.

---

### Post by robostang 548 on 2007-10-30
I am having the same problem.  My sessions manager won't let me save the changes I make to it.  I noticed that if you open the sessions manager from a terminal you can see when you try to add somthing it says somthing in the terminal about not being able to save the change.  I also noticed that when I go into my screenlets settings to try to make certain screenlets begin on startup, the checkboxes dont stay checked when I go back into the screenlets manager.

-Don

---

### Post by contactpraveen2001 on 2008-03-05
I m having the same problem

---

