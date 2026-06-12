---
title: "Gnome Panel does not appear"
date: 2009-07-12
forum: Desktop Environments
---

### Post by bertles86 on 2009-07-12
Hi,

I restarted just now and the Gnome Panel has completely disappeared.

If I run the Netbook desktop mode, I get my menus/apps but no Gnome Panel at the top, with the systray and menus.

If I run the Classic desktop mode, I just get wallpaper with the icon of my SDHC card and nothing else.

If I run 'gnome-panel' in a terminal it comes back fine, but on restart it's gone again...!

From searches here and on Google, I tried "metacity --replace" and the following comes up:

```
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x2200003
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
```

Can anyone please help me fix my 'pager' so my gnome panel comes back at the top!!!!?

---

### Post by danebramaged on 2009-07-14
I just posted a similar message.  No response so far.  

If some has a solution, ...please let us know.


thanx

---

### Post by danebramaged on 2009-07-15
Here try this:

Open up a terminal window and type:

sudo apt-get install gnome

wait for download to finish.

restart the system and logon.


hope this helps.

---

### Post by bertles86 on 2009-07-15
I found out from days of Googling that you 100% do not want to uninstall Evolution mail from the synaptic package manager because if you do then it automatically removes Gnome/the desktop with it. So you are forced to have Evolution, I tried allsorts of things to fix it but in the end reinstalled.

P.S. Also some bars disappear in NBR if you switch to a Classic desktop, but there is a patch for this which some geezer made online, if you need it then I can point you in the right direction. I'm no crusing on Ubuntu NBR with a Classic desktop...

---

### Post by gianluca.pettinello on 2009-07-15
Try to define a new user and see if its desktop has the panel
If this is the case then you have to copy all your data to the home of the new user and then switch to it

Ciao
Gianluca

---

### Post by danebramaged on 2009-07-15
> **bertles86 said:**
> I found out from days of Googling that you 100% do not want to uninstall Evolution mail from the synaptic package manager because if you do then it automatically removes Gnome/the desktop with it. So you are forced to have Evolution, I tried allsorts of things to fix it but in the end reinstalled.

P.S. Also some bars disappear in NBR if you switch to a Classic desktop, but there is a patch for this which some geezer made online, if you need it then I can point you in the right direction. I'm no crusing on Ubuntu NBR with a Classic desktop...

That is exactly how I got into this mess in the first place.  Now that I have everything working smoothly again I have 138 meg of bloated code sitting on my hard drive that I will never use.  And to think that people complained when MicroSlop did the same thing with Internet Exploder.  On top of which, Evolution Email is a Novell Product so, if that's what I wanted to use to  begin with, I'd be running OpenSuse.

tayl

---

### Post by graemev on 2009-07-19
You need to delete the file:


~/.gconf/desktop/gnome/session

This holds the 'session state' ... somehow the metacity & gnome-panel
are getting disabled ... remove it and get back default behavior
...it may get re-created (with better contents)

... better would be to find out why  this is happening:(.

---

### Post by mehta on 2009-07-20
I am new to xubuntu and just a few days ago changed my laptop to this OS.  Everything has been working well but the top statusbar and the bottom systray have disappeared from view.
Would be keen like others to get rid of this irritation and look forward to reading a step by step advice.

---

### Post by graemev on 2009-07-21
If I've understood what you want here , you would like the actual key presses ?

Well ... OK

ALT-F2
Type xterm, press enter
type rm ~/.gconf/desktop/gnome/session

logoff/logon

(pressing the tab key will reduce your need for typing)

---

### Post by drfox on 2009-07-22
Here's what you need to do to get your panels back:
Get a terminal session, either by logging on to a terminal session or by pressing Alt-F2 from your desktop and then typing "xterm"

Remove these folders:
.gconfd
.gconf
.gnome2
.gnome2_private
.config

by using the command: rm -r foldername

Once they are removed, reboot using the command: sudo shutdown -r now

Your panels will be back. 

HTH  Larry

---

