---
title: "No menu bar in Gnome on startup"
date: 2008-07-31
forum: Desktop Environments
---

### Post by cajunaggie on 2008-07-31
Lately, whenever I log in, the menu bar hasn't been showing up. All other start-up programs run as normal, but there is no menu bar. However when I change my session to Failsafe GNOME, it works normally. Therefore I assume there is a problem in my start-up script. Where would I go to change my start-up script?

---

### Post by Potatoj316 on 2008-07-31
go in System -> prefrences -> sessions and add gnome-panel.  

(i think its prefrences, it might be administration, check both)

if you dont have those menus (thats your problem right?) you should be able to start it by pressing alt+F2 and typing gnome-panel

---

### Post by tuxxy on 2008-07-31
DO you mean the menu taskbar or the secondary one for open apps

---

### Post by cajunaggie on 2008-07-31
I mean the entire bar itself, where the applications, places, system menus normally reside. It does not load.

---

### Post by Potatoj316 on 2008-08-01
> **Potatoj316 said:**
> go in System -> prefrences -> sessions and add gnome-panel.  

(i think its prefrences, it might be administration, check both)

if you dont have those menus (thats your problem right?) you should be able to start it by pressing alt+F2 and typing gnome-panel

Potatoj316 had a good answer, try that.  alt+F2 and type gnome-panel and you will have your panels back, untill you restart.  Then add gnome-panel to your sessions.

---

### Post by cajunaggie on 2008-08-01
Fixed it! Thanks for your help.

---

### Post by cajunaggie on 2008-10-03
Just upgraded to Intrepid and my gnome-panel is gone again. Alt+F2 has no effect. Thoughts?

---

### Post by idealflame on 2008-10-09
I had exactly the same problem (read: symptoms) as you last night/this morning, but that was because I was trying to draw FF3 kicking and screaming onto my Lenny (Debian) system, so I don't know if my solution will help you :)

Either way, you can at least get to *try* to start the gnome-panel by creating an empty file on your desktop, right-clicking (right-click still works, right?) and then selecting "Open with Other Application". In "Use a custom command", type gnome-terminal
If you type gnome-panel from there (the terminal), you'll at least get an explanation as to *why* it's not working...mine was because of a GTK2 problem. I don't know what you'll get, but at least we'll have something to go on!

Good luck

---

### Post by saciar on 2009-07-07
Hi i have similar problem, no menu bar, no possibility to resize or close windows by selecting navigation icons in the upper right corner, still can acces window menu.
Acer Aspire One is my devil with Jaunty NBR. If i statrt gnome-panel through the command line i get this...

milan@milan-aspire1:~$ gnome-panel
** (gnome-panel:3192): DEBUG: Adding applet 0.
** (gnome-panel:3192): DEBUG: Initialized Panel Applet Signaler.
** (gnome-panel:3192): DEBUG: Adding applet 1.
** (gnome-panel:3192): DEBUG: Adding applet 2.
** (gnome-panel:3192): DEBUG: Adding applet 3.
** (gnome-panel:3192): DEBUG: Adding applet 4.
** (gnome-panel:3192): DEBUG: Adding applet 5.

(gnome-panel:3192): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -1 and height 24
** (gnome-panel:3192): DEBUG: Adding applet 6.
** (gnome-panel:3192): DEBUG: Adding applet 7.
** (gnome-panel:3192): DEBUG: Adding applet 8.
** (gnome-panel:3192): DEBUG: Adding applet 9.

(gnome-panel:3192): libglade-WARNING **: Unexpected element <requires-version> inside <glade-interface>.
** (gnome-panel:3192): DEBUG: Adding applet 10.
** (gnome-panel:3192): DEBUG: Adding applet 11.
** (gnome-panel:3192): DEBUG: Adding applet 12.

runing clasic interface, not the one inside netbook remix.

please help... quite new to linux as well as ubuntu

---

### Post by idealflame on 2009-07-07
Hmm. It doesn't sound like gnome-panel's dying from those messages (or does still it not come up even after those warnings?).

The way you describe the error, I wonder if your window decorator isn't running?
Try `metacity --replace` in a terminal, and see if that doesn't help. If it does, you just need to set MetaCity as your starting window manager (or maybe some other window manager? Your choice there :))

---

### Post by Platypus123 on 2009-07-16
I may have a similar issue: I recently revisted Ubuntu this week after several years of Windows and I've encountered a similar problem.  Both my upper and lower toolbars have disappeared and Alt+F2 does not bring up a Terminal window to enter the commands to make them visible again.  However, Ctrl+Alt+F2 thru F5 seem to switch from the GNOME desktop to a fullscreen Terminal.  When entering the commands here and switching back to the desktop (with and without a reboot) doesn't seem to correct the problem.  I think it may work if I can access Terminal from the File System as I created an icon on my desktop, but I'm not sure where it's located on the hard drive.  Any suggestions to getting the bars back?

---

### Post by Nero147 on 2009-07-16
if you hit alt-f2 it will bring up the run command dialog. If you type in gnome-terminal and hit enter it will bring up the terminal window.

Once that is up you can try entering 
gnome-panel
and see if that works. then you can try the other suggestions offered in this thread.

---

### Post by Platypus123 on 2009-07-16
Is it possible the run dialog is opening off-screen?  When I hit Alt+F2, I can't *see* anything opening so I'm not sure it's working.  Can I just opening Terminal directly from the file system directory?

---

### Post by Platypus123 on 2009-07-16
Problem solved! It looks like I had inadvertently deleted gnome-panel.  Creating a file on the desktop with the custom line to run Terminal worked and I installed it with "sudo apt-get install gnome-panel".  Thanks for the help!

Time to add a Terminal icon to the desktop....

---

### Post by warreno on 2009-08-15
Huh. I've been having the *same* problem! Been 10+ years since I last did Linux (Red Hat!), and I've really been enjoying the Ubuntu netbook remix. (Jaunty.)

However, after rebooting, my top and bottom desktop menu bars also vanished. I could get into the console sessions (ctrl-alt-f1&#8230;f6), but that didn't let me do any of the nifty suggestions here (such as metacity --replace or gnome-panel). I could get a ps -A | more and see what was running, at least. In the GUI, alt-f2 did **not** bring up a run dialog box. Killing the Xwindows session didn't bring up the panels either. ctrl-alt-backspace in the GUI wasn't recognized; in fact **no** keyboard input at all was accepted in the desktop. More on that below.

I tried the trick of creating a new empty document to open with gnome-terminal; however, the "Alternate Command" dialog would not let me type anything into it, so I had to click the *Browse* button instead to select gnome-terminal from the list.

This did open a terminal window, but I couldn't actually type into it either; it didn't want to accept my keystrokes. The cursor was a hollow rectangle instead of the black, solid one: The terminal window wasn't active. At least I had some understanding of why none of the text input areas let me type into them.

I noticed that my screen effects settings had reverted to "None", and that I didn't seem to have active window borders (i.e., they lacked title bars, had no min/max/close buttons, and I couldn't drag or resize them), so I got into the "Visual Effects" tab in "Change desktop background" and selected "Normal". (My rationale was that maybe the reversion to no desktop effects had hosed gnome-panel somehow.) This didn't get me my gnome-panel, but it did reactivate the frames on the windows, which let me select (activate) and type into a terminal window at last.

Entering gnome-panel did in fact get me my system bars back; however my virtual desktops, of which I'd set up six, have reverted to two. And, of course, if I ctrl-c in the terminal window in which gnome-panel is running, I kill the process, and the menu bars go away again.

I got a libglade-WARNING too (Unexpected element <requires-version> inside <glade-interface>), and it doesn't look as though metacity --replace did anything to solve my situation.

This is very strange. Is there a config file someplace that's missing the gnome-panel command? If so, which one? (I don't see a "Sessions" setting in either the System or Administration menus.)

Overall I have to say I love the heck out of Ubuntu. The install and config have all been nearly painless. If I can find and lick this gnome-panel problem so I don't lose my system panels every time I reboot, I'll be a very cappy hamper.

Thanks for any suggestions. Best to all.

[COLOR=Green]**WORKAROUND**[/COLOR]: For now, I've created an Application launcher on the desktop that points to /usr/bin/gnome-panel for those days when a reboot happens to be necessary (or a shutdown; the Acer Aspire One I have &#8212; 8 GB SSHD &#8212; only has a 3-cell battery, for about 2.5 hours of unplugged use, and I might not be able to keep it suspended if power gets too low). It works. At least this way I don't have to worry about accidentally exiting the terminal window that has it running. But of course it would be most ideal to find out what's going wrong.

---

### Post by warreno on 2009-08-15
I think I might have solved my problem.

I poked around on [getdeb.net]("http://www.getdeb.net/") and discovered an app called [Ubuntu Tweak]("http://www.getdeb.net/app/Ubuntu+Tweak"). In addition to letting me get some software packages not visible in Add/Remove, it has a "Startup" editing section. One of the items in that section is "Autostart".

Scrolling through the list, I didn't see gnome-panel, so I added it.*

Restarting gets me my gnome-panel back, though I'm still going to keep my application launcher around for a while just in case.

This thread was *extremely* useful in getting me pointed in the right direction. I'm glad I stumbled across it.

====

* What is *also* in that list (but not marked as active) is "UNR Launcher" and "UNR Desktop Launcher". These are the launchers that come with the netbook remix, I think, and when I changed my UI to the full Gnome desktop I suspect they were switched off, but that gnome-panel didn't get added to the list as a replacement.

---

### Post by dk1 on 2009-08-15
fixed it on my system.  

On UNR, go to Preference-> Startup Applications.

Add these commands:
```

gnome-panel
metacity --replace

```

Restart and it should work.

I'm not sure why it ever stopped in the first place on my system though.  I just turned it off this morning after checking my email and when i turned it back on later it was giving me the same problem as everyone else.

---

### Post by warreno on 2009-08-15
Hey, dk1, that fixed it for me too. Nice catch, and thanks for passing it along.

Out of curiosity, did your system download any updates prior to your last reboot? My Ubuntu netbook remix was a brand-new install as of Wednesday (had been running XP before); after install and restart it downloaded about 170 updates. But *I never rebooted* after those updates were retrieved, to the best of my recollection, until Friday night &#8212; and that's when my troubles began.

I'm just wondering if there was a very recent update posted &#8212; I'm thinking within the last week or so &#8212; that affected some installs. If you're using the netbook remix too, and if your system updated before your last restart, maybe that's the common point.

Anyway, thanks for posting the fix.

---

### Post by spawnconnery on 2009-09-25
I had the same problem on both an acer aspire one (reloaded) and a mini 9.  On the mini 9, I had only just installed mtpaint, rebooted, and boom no menu bar.  The above fixed it!  Thanks to all!  I do wonder what is the root of this problem.

---

### Post by HankB on 2010-01-28
I'm experiencing this difficult at the moment. Unfortunately <alt>F2 does not bring anything up. Fortunately I have a desktop shortcut to start up a terminal. Once the terminal is open, I tried running gnome-panel and get:
```
hbarta@bonsai:~$ gnome-panel
Cannot register the panel shell: there is already one running.
hbarta@bonsai:~$
```

I should also mention that desktop background (via drapes) is there as well as desktop icons. It seems the panel is running but stuck somewhere in initialization. I'm not sure how to find out where it is stuck and how to fix it.

I did shutdown the system and rebooted from the command line. I'm not sure how to logout from the command line. Following reboot and logging in again, I got the same result.

I had this problem once before and just started deleting config files under ~/.gconf until I could login and get working panels, but that's a pretty kludgey way to fix this. At that time the panel reverted to something that looked more like NBR desktop (which was originally installed on this PC but I have since switch to the normal Gnome desktop.)

Thanks for your help.

Edit: It occurred to me to try to kill gnome-panel so I did. It was restarted automatically and came up normally. When I logged out and logged in again, it seems to have started up normally. My problem seems to be resolved for now.

---

### Post by bobterri on 2010-01-30
I too lost both top and bottom menu bars.  

I started terminal per instructions posted earlier and issued "gnome-panel" command.  I got the following message:

gnome-panel: symbol lookup error: /usr/lib/libbonobo-2.so.0: undefined symbol: C

Also, I issued "killall gnome-panel" and this message came up:

gnome-panel: no process found

HELP!  I use this laptop at work.

---

### Post by HankB on 2010-01-31
> **bobterri said:**
> 
gnome-panel: symbol lookup error: /usr/lib/libbonobo-2.so.0: undefined symbol: C
Try the following command which will help identify the library that seems to be causing this problem and post the results:

```
hbarta@cypress:~$ ldd `which gnome-panel`|grep libbonobo
	libbonoboui-2.so.0 => /usr/lib/libbonoboui-2.so.0 (0x00007f6e888c5000)
	libbonobo-2.so.0 => /usr/lib/libbonobo-2.so.0 (0x00007f6e88438000)
	libbonobo-activation.so.4 => /usr/lib/libbonobo-activation.so.4 (0x00007f6e8821d000)
hbarta@cypress:~$ 
```

Maybe the following will show what is installed on your system:
```
hbarta@cypress:~$ dpkg -l|grep libbonobo
ii  libbonobo2-0                          2.24.2-1                                   Bonobo CORBA interfaces library
ii  libbonobo2-common                     2.24.2-1                                   Bonobo CORBA interfaces library -- support f
ii  libbonoboui2-0                        2.24.2-1ubuntu2                            The Bonobo UI library
ii  libbonoboui2-common                   2.24.2-1ubuntu2                            The Bonobo UI library -- common files
hbarta@cypress:~$ 
```

Also try:
```
hbarta@cypress:~$ gnome-panel --version
GNOME gnome-panel 2.28.0
hbarta@cypress:~$ 
```
or
```
hbarta@cypress:~$ dpkg -l|grep gnome-panel
ii  gnome-panel                           1:2.28.0-0ubuntu6                          launcher and docking facility for GNOME
ii  gnome-panel-data                      1:2.28.0-0ubuntu6                          common files for the GNOME Panel
```

I'm grabbing at straws here but it seems that gnome-panel is not happy with that library.

---

### Post by bobterri on 2010-01-31
Thanks Hankb, but I had to get this machine up and running.  As I stated, I use it at work, so I re-installed the OS.

This is the first time I have ever had a major problem with Ubuntu.  I started with Breezy and have run every new version since.  I have never had a show-stopper experience like this.

People who work in the real world with their computers simply cannot afford to have problems like this happen and then spend days hunting around for solutions.

---

### Post by itsjustarumour on 2010-02-08
Bug reported for gnome-panel failing to start when desktop loads:

[https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/518873](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/518873)

:)

---

### Post by Kognit on 2010-03-12
To me also all the bars disapered but then i tried once more to write in terminal:
```
gnome-shell --replace

```

and the it worked!

---

### Post by keyboardslave on 2011-05-09
I to had the same problem happen after the latest update 11.4 natty.

alt + f2 didnt work and i could not get terminal,
to get around this i simply created a lancher by right clicking desktop and under command gave it the above commands. then double click it.

---

