---
title: "Help remove printer components (Ubuntu 11.10)"
date: 2011-12-17
forum: Desktop Environments
---

### Post by jgray152 on 2011-12-17
Hi Folks,

having a hard time installing my lexmark S605 printer. Worked on my first install of Ubuntu but had to reinstall. 

at first I tried and got the error "[FONT=Courier New]**(gksudo:2461): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap"**"

So I researched and found a fix **"**[/FONT][FONT=Courier New]**sudo apt-get install gtk2-engines-pixbuf"**

Now I don't get the error message but for some reason after what seemed a successful install of my printer it was saying it couldn't print. I forget the actual error message.

So I decided to remove the printer and its two components;
[/FONT][FONT=Courier New][B]-- lexmark-inkjet-legacy
-- lexmark-wsu-legacy[/B]

I tried again but installed **"lexmark-inkjet-legacy-wJRE-1.0-1.i386.deb.sh"** and I think I was supposed to install [B]"lexmark-inkjet-legacy-1.0-1.amd64.deb.sh"
[/B]
After installing **"**[/FONT][FONT=Courier New]**lexmark-inkjet-legacy-wJRE-1.0-1.i386.deb.sh"** There is no printer installed when opening the printer manager.

So I tried reinstalling with **"**[/FONT][FONT=Courier New]**lexmark-inkjet-legacy-1.0-1.amd64.deb.sh"** but it says there are two components which need to be removed before I can install...problem is I can't find these in the software manager...
[/FONT][B][FONT=Courier New]-- lexmark-inkjet-legacy
-- lexmark-wsu-legacy[/FONT][/B]

So I tried from the terminal to remove them.....
[B][I]justin@Jgray-Ubuntu:~$ sudo apt-get --purge remove lexmark-inkjet-legacy
[sudo] password for justin: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package lexmark-inkjet-legacy
justin@Jgray-Ubuntu:~$ sudo apt-get --purge remove --lexmark-inkjet-legacy
E: Command line option --lexmark-inkjet-legacy is not understood
justin@Jgray-Ubuntu:~$ sudo apt-get --purge remove lexmark-wsu-legacy
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package lexmark-wsu-legacy
justin@Jgray-Ubuntu:~$ sudo apt-get remove lexmark-wsu-legacy
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package lexmark-wsu-legacy[/I][/B]

[FONT=Courier New]This is the error I still get when trying to install the printer software
[/FONT][FONT=Courier New][B][I]The installer has detected previously installed components.

-- lexmark-inkjet-legacy
-- lexmark-wsu-legacy

Please remove all installed components and run the installer again.


[/I][/B]How can I completely remove all the printer components and software?[/FONT]

---

### Post by Old Greg on 2011-12-17
Bump :guitar:

---

### Post by jgray152 on 2011-12-18
Got me all excited! lol :) Thought there was an answer.

---

### Post by jgray152 on 2011-12-18
I suppose is there anyways to completely purge any and all components recently installed that may be hidden? Could there be some lines in a configuration file that is telling the installer these are still installed when they are not?

I tried making a new admin account but that didn't work. Short of .....reinstalling AGAIN not sure what to do.....

---

### Post by kw12589 on 2012-01-17
Use Synaptic to remove the components.

[LEFT] sudo synaptic
search for lexmark
select each component and mark for complete removal
apply
reboot.[/LEFT]

---

