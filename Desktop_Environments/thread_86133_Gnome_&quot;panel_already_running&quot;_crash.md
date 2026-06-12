---
title: "Gnome &quot;panel already running&quot; crash"
date: 2005-11-04
forum: Desktop Environments
---

### Post by ibanez88 on 2005-11-04
Yes the dreaded "I've detected a panel already running and will now quit" crash has reared its ugly head in my basically fresh Breezy install.  I was installing a Be-OS theme from gnome-look.org when it happened. 

I can't get a working panel happening to use the gnome tools to try and get the process to stop.  Kill -9 and reboot does nothing to help.  Curiously there is only one gnome-panel process listed in my ps waux to begin with.

I've also tried editing my ~/.gnome2/session file (after backing it up), removing all entries related to the panel (entries with the same number).  This removes the error dialog but then I still have no panel.  In this situation the panel crashes (but without the "already running" dialog) when I enter gnome-panel restart in a terminal. This probably has something to do with my editing the session file, so I can use the old one again but that brings me to the original problem.

I've also purged and re-installed gnome-panel and gnome-applets, that didn't help.  

I found this which might be a similar problem but killing bonobo doesn't help in my case:
[http://bugzilla.gnome.org/show_bug.cgi?id=87681](http://bugzilla.gnome.org/show_bug.cgi?id=87681)

If anyone has a possible solution I'd greatly appreciate it!

Thanks.

---

### Post by tomski on 2005-11-04
this happend to me this morning after i did an update.
 i run hoary, so it may be a package that was backported but the panel did restart and the problem has not been back since (as far as i know (im at work now))

---

### Post by ibanez88 on 2005-11-04
I'm all up to date with universe, multiverse, etc.  Not using backports.

I tried removing ~/.gnome2    Still get the error, no panel.

---

### Post by Irony on 2005-11-04
This happened to me to with Breezy. I followed the advice of some others on the forums and did the following...

I deleted the panels then put them back.

Make sure you delete one then reinstate it, then delete the other and reinstate it.

Don't delete both at the same time, otherwise there is nothing to click on to reinstate.

---

### Post by ibanez88 on 2005-11-04
Sorry I should have been clearer.  There already are no panels on the screen; if I could get one then I might have something to work with.  Yet my ps waux | grep panel tells me that a gnome-panel is running:

adrian    7771  0.3  1.8  18964  9516 ?        Ss   13:32   0:00 gnome-panel --sm-config-prefix /gnome-panel-GGqITl/ --sm-client-id 10112ac563000113100358800000111240003 --screen 0
adrian    7776  0.2  1.8  18148  9428 ?        S    13:32   0:00 /usr/lib/libgnomeui-0/gnome_segv gnome-panel 11 2.12.1


I think that the gnome_segv is the error message window.  Trying to kill -9 the process or type gnome-panel restart doesn't work, in the latter case it spawns the "panel already running" message window.

My .gnome2/session looks like the following:


[Default]
0,id=10112ac563000113100358800000111240002
0,RestartStyleHint=1
0,Priority=40
0,Program=gnome-volume-manager
0,CurrentDirectory=/home/adrian
0,CloneCommand=gnome-volume-manager --sm-config-prefix /gnome-volume-manager-aK1UWj/ 
0,RestartCommand=gnome-volume-manager --sm-config-prefix /gnome-volume-manager-aK1UWj/ --sm-client-id 10112ac563000113100358800000111240002 --screen 0 
1,id=10112ac563000113100358800000111240003
1,RestartStyleHint=2
1,Priority=40
1,Program=gnome-panel
1,CurrentDirectory=/home/adrian
1,CloneCommand=gnome-panel --sm-config-prefix /gnome-panel-GGqITl/ 
1,RestartCommand=gnome-panel --sm-config-prefix /gnome-panel-GGqITl/ --sm-client-id 10112ac563000113100358800000111240003 --screen 0 
2,id=10112ac563000113100358900000111240005
2,RestartStyleHint=2
2,Priority=50
2,Program=gnome-cups-icon
2,CurrentDirectory=/home/adrian
2,CloneCommand=gnome-cups-icon --sm-config-prefix /gnome-cups-icon-1t4lWj/ 
2,RestartCommand=gnome-cups-icon --sm-config-prefix /gnome-cups-icon-1t4lWj/ --sm-client-id 10112ac563000113100358900000111240005 --screen 0 
3,id=10112ac563000113100358800000111240001
3,RestartStyleHint=2
3,Priority=40
3,Program=nautilus
3,CurrentDirectory=/home/adrian
3,CloneCommand=nautilus --sm-config-prefix /nautilus-eSgYPj/ 
3,RestartCommand=nautilus --sm-config-prefix /nautilus-eSgYPj/ --sm-client-id 10112ac563000113100358800000111240001 --screen 0 --no-default-window 
4,id=10112ac563000113100370200000111240007
4,Program=gnome-terminal
4,CurrentDirectory=/home/adrian
4,CloneCommand=gnome-terminal --sm-config-prefix /gnome-terminal-8ZZr2j/ 
4,RestartCommand=gnome-terminal --sm-config-prefix /gnome-terminal-8ZZr2j/ --sm-client-id 10112ac563000113100370200000111240007 --screen 0 --window-with-profile-internal-id=Default --show-menubar --role=gnome-terminal-11306-1153245907-1131003702 --active --geometry 79x24 --title adrian@ubuntu:\\ ~ --working-directory /home/adrian --zoom 1 
5,id=10112ac563000113100358800000111240004
5,RestartStyleHint=1
5,Priority=50
5,Program=update-notifier
5,CurrentDirectory=/home/adrian
5,CloneCommand=update-notifier --sm-config-prefix /update-notifier-YTNbzn/ 
5,RestartCommand=update-notifier --sm-config-prefix /update-notifier-YTNbzn/ --sm-client-id 10112ac563000113100358800000111240004 --screen 0 
6,id=10112ac563000113100358700000111240000
6,RestartStyleHint=2
6,Priority=20
6,Program=metacity
6,CurrentDirectory=/home/adrian
6,DiscardCommand=rm -f /home/adrian/.metacity/sessions/1131004043-11214-2480068989.ms 
6,CloneCommand=metacity 
6,RestartCommand=metacity --sm-save-file 1131004043-11214-2480068989.ms 
num_clients=7


As stated previously, removing all of the entries beginning with 1 doesn't help any, I still get a panel crash at startup.  

You might say that I'm "up a creek without a panel". ;)

EDIT:
Is it possible to change my theme from the command line?  I wonder if its possible (since installing the Clearlooks-BeOS theme is what apparently caused the crash originally) that reverting back to default theme might help?

---

### Post by ibanez88 on 2005-11-04
That did it!  

I hit control L from a window in Nautilus, and typed
themes:///
to select a new theme.

I chose one, rebooted, and all is well again.

I'd use caution with the Clearlooks-BeOS theme!

Thanks to all who replied.

---

### Post by bobbob1016 on 2006-12-01
I know this thread is dead, but I just wanted to post how to fix it so anyone who needs it, knows how to fix it.

It helps if you are online when you do this, because you might need to download packages.

Sign in to the failsafe terminal, by clicking the Options button on the bottom left of the login screen.
Then click Failsafe terminal, and Change Session.
Login as normal.
You might see a warning saying you are in failsafe terminal, just click ok.
Type:
sudo apt-get remove gnome-panel
This will say that it will remove gnome-panel, and ubuntu-desktop, this is FINE, say type Y.
Type exit.
Then click Options again and Reboot.
Get back into the failsafe terminal, once Ubuntu boots up.
Then type:
sudo apt-get install ubuntu-desktop
Logout, then log back in, but under normal mode.
You still might notice there are no panels, this is still fine.
Right-click a blank area on the desktop, and click Create Launcher.
Type whatever you want as a name for the launcher, and enter "/usr/bin/gnome-panel".
You should see your panels now.

This took a few times for me to repeat it before it worked, so keep that in mind.  I am not an ubuntu/linux expert, I'm just posting what I figured out to get it to work for me.

---

### Post by be4truth on 2007-08-12
I've detected a panel already running and will now exit.

Problem: Suddenly Gnome logins get the error message: "I've detected a panel already running, and will now exit". One can with a right click open a terminal and write 'killall gnome panel' then 'gnome-panel'. 

What triggered this on my computer was that another user (in my case root) changed the desktop background (no joking!) and used a .png file. After either removing the file or use a .bmp the problem was solved. 

Check that out.

---

