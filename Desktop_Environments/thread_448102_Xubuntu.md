---
title: "Xubuntu"
date: 2007-05-18
forum: Desktop Environments
---

### Post by Sladi on 2007-05-18
Hi! 

I have some questions: 

Is there a way to easily copy shortcuts of existing programs to the panel? In Ubuntu I right clicked on a menu entry. 

I can't find the Nvidia control panel. Where is it?


Regards, 
Sladi

---

### Post by elfstone214 on 2007-05-18
For Nvidia settings type in a terminal: 

> nvidia-settings

---

### Post by Sladi on 2007-05-19
Thanks elfstone. :) 

How can I put Thunderbird on the panel where Firefox is? Should I do it manually or is there an easier way? 


Regards, 
Sladi

---

### Post by dolphin_oracle on 2007-05-19
xubuntu does not the gnome nice-ity of putting any installed app on the panel.  You have to manually add a launcher.

---

### Post by kerry_s on 2007-05-19
use the app finder, drag and drop the application you want to the menu editor to add it. You can also use the app finder to make launchers. Just drag the app from appfinder to the program launcher box on the left.

---

### Post by Sladi on 2007-05-20
Thank you! :D 
That's very cool! 


Regards, 
Sladi

---

### Post by dolphin_oracle on 2007-05-20
kerry_s

that's a neat trick.  i'm going to have to try that.  Thanks.

---

### Post by ugm6hr on 2007-05-20
@Sladi:
If you want Thunderbird on the top panel taskbar (next to Firefox), there are a couple of options.  

My solution is very slick (I think so anyway), and it alerts you to new emails when they arrive without requiring you to leave Thunderbird open all the time:
1. Right-click top panel (somewhere in the middle), -> "Add new item"
2. Select "Mail Watcher", click "Add"
3. Select "Mailboxes", click "Add", then select mailbox type (mine is "Remote POP3 Mailbox")
4. Enter POP3 mailbox details: e.g. Googlemail settings: pop.googlemail.com, *user*@googlemail.com, *password*; Advanced: "Use SSL/TLS on alternate port", tick "Use non standard POP3 port", port number "995", Then "Close"
5. External programs:
Run on click: "mozilla-thunderbird"
Run on new messages: "aplay /home/*user*/*sound.wav*
(change to whatever path your "You've got mail" sound is stored at or leave blank)
6a. Click on "Icons: Normal" and select file /usr/share/pixmaps/mozilla-thunderbird.png
6b. If you want to change the "New Mail" icon - do same as above (I downloaded a nicer envelope 32x32 .png icon from [www.iconarchive.com](www.iconarchive.com))
7. Click "View log", untick "Show log status in icon", then "Close" (this is not important, but if you don't do it, the icon will have a red alarm signal on top of it if it ever fails to connect to the POP3 server - possibly a useful piece of information, but less aesthetically pleasing)
8. "Close"

The icon will appear on the right side of the panel, if you want it by Firefox:
9. Right click Thunderbird icon -> Move
10. Click just to the right of Firefox (or wherever you want it)

If this is a bit excessive for you, you can just use "Program Launcher" instead of "Mail Watcher", and use "mozilla-thunderbird" in the "Command" box.  I tick the "Use startup notification" box, but I'm not 100% certain what that does!  This method allows you to add whatever you want to the top taskbar.  I like to use "gksudo thunar" (as Command) in a taskbar icon to allow me to file manage as root whenever I want (it will still prompt for password).

I'm still learning about the power of XFCE :)

---

### Post by Sladi on 2007-05-20
Thanks. The startup notification causes the mouse pointer to show a little clock while loading. :)

---

### Post by eeried on 2007-06-01
Silly question: Where do you find or how do you launch app-finder?

---

### Post by ugm6hr on 2007-06-01
> **eeried said:**
> Silly question: Where do you find or how do you launch app-finder?

In Applications->Accessories-> Appfinder

If you've lost it in the menu:
It's in */usr/bin/xfce4-appfinder*
so just enter *xfce4-appfinder* in Terminal

---

