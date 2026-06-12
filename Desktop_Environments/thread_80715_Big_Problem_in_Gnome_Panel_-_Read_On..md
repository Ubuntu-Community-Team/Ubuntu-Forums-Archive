---
title: "Big Problem in Gnome Panel - Read On."
date: 2005-10-22
forum: Desktop Environments
---

### Post by blouie on 2005-10-22
I really regret this. Maybe ubuntu is not designed for users to change things around. May be I should have been happy with the default system and not to mess around to get my "ideal". I tried to reconfigure the two panels. I removed the bottom panel. Then I moved the Menus panel to the bottom. A few clicks later, the panel stopped responding. the menu does not respond to mouse clicks. No response to right clicks on the panel itself either. I killed the ubuntu-panel process, hoping to restart it fresh. It does not work. Every time I kill it, the panel disappears - for about 3 seconds - and then it comes back with another pid, but still unresponsive. I tried restarting, even rebooting to no avail. Why does it behave like this? What should I do?

---

### Post by orzechowskid on 2005-10-22
try deleting your ~/.gconf directory then logging out and logging back in again.  I think that's where all the panel preferences are stored (as well as a lot of other GNOME settings, so back it up first).

---

### Post by blouie on 2005-10-23
The gnome panel is still dead. I can not access any of the menus. I renamed the .gconf to .gconf.backup. It still has the same symptoms. Any ideas?

---

### Post by blouie on 2005-10-23
Any ideas, anyone?

---

### Post by LorenzoD on 2005-10-23
The reason why the panels keep coming back is because they are set to automatically restart if they are killed. The idea is that the user wants panels.

Can you check your ~/.xsession-errors for anything relating to gnome-panel?

---

### Post by blouie on 2005-10-23
Thanks for the response.
The ~/.xsession-errors file is full of this:
```
** (gnome-cups-icon:8495): WARNING **:  IPP request failed with status 1030
```

---

### Post by blouie on 2005-10-23
Any ideas?

---

### Post by gillion on 2005-10-23
You can do this.

Log out of your desktop.

Do not log back in.

Drop to a terminal by pressing **Ctrl+Alt+F1**

Log in as a regular user ... then delete your **.gnome2** directory using the **rmdir** command. Please do this first ... **rmdir --help**

When you do that press **Alt+F7** to return to the gui login and log in as yourself.

You should have a fresh desktop.

The other alternative is to use **gconf-editor** 

to execute this program press **Alt+F1** and scroll down to *system tools*

if you don't see your menus press **Alt+F2** it will bring up a run program tool that you can type in the command gconf-editor.

Once in gconf-editor go here **/apps/panel** from there the rest is pretty easy to follow.

---

### Post by blouie on 2005-10-24
[QUOTE=gillion]You can do this.

Log out of your desktop.

Do not log back in.

Drop to a terminal by pressing **Ctrl+Alt+F1**

Log in as a regular user ... then delete your **.gnome2** directory using the **rmdir** command. Please do this first ... **rmdir --help**

When you do that press **Alt+F7** to return to the gui login and log in as yourself.

You should have a fresh desktop.

The other alternative is to use **gconf-editor** 

to execute this program press **Alt+F1** and scroll down to *system tools*

if you don't see your menus press **Alt+F2** it will bring up a run program tool that you can type in the command gconf-editor.

Once in gconf-editor go here **/apps/panel** from there the rest is pretty easy to follow.[/QUOTE]
I deleted .gnome2 as suggested. It did not fix. Thd panel is still as dead as before.
I also tried running gconf-editor, here is what I get:
> (gconf-editor:9781): GnomeUI-WARNING **: Whle connecting to session manager: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

---

### Post by blouie on 2005-10-25
I have even reinstalled gnome-panel and gnome-panel-data, and the panel is still dead. Does this tell me the problem is not in the panel or the data?

---

### Post by gillion on 2005-10-25
[QUOTE=blouie]I have even reinstalled gnome-panel and gnome-panel-data, and the panel is still dead. Does this tell me the problem is not in the panel or the data?[/QUOTE]
Not likely ... the error message you get with running gconf-editor  should not stop you from using the tool.

I get it myself and I have no issues tweaking my desktop settings from inside it.

when I get home I am going to experiment and try to reproduce your error.

It maybe a single file that you only need to get rid off and the panel will be rebuild as default.

Please be aware that it is possible that your panel is running but doing so in a mixed up state where you tinkered with the position and what not.

I have found GNOMES panel to be very finnicky and not in the least as user-proof and advanced as KDE.

As I said ... I should be home in a few.

---

### Post by blouie on 2005-10-25
I removed and then reinstalled panel, and it still did not fix.  Would removing and reinstalling the entire gnome-desktop make sense at all?  Considering that I don't have much in the system yet, I could even reinstall the system. But then I would not know even roughly what had gone wrong.

---

### Post by gillion on 2005-10-25
[QUOTE=blouie]I removed and then reinstalled panel, and it still did not fix.  Would removing and reinstalling the entire gnome-desktop make sense at all?  Considering that I don't have much in the system yet, I could even reinstall the system. But then I would not know even roughly what had gone wrong.[/QUOTE]
Good approach.

Never nuke a problem without understanding it first.

I think I might have found your angle.

```

/home/you_user_directory/.gconf/apps/panel

```

I beleive that is the offending folder ... delete it your gnome system should rebuild a fresh directory for you. I have tried it on a test account and it worked. I have not been able to create the problem as you have described it. A fluke maybe ?

Anyhoo... remove your **panel ** directory and that might solve it. 

The Panel folder contains all the settings for its name sake.

You need to do this not logged into your GUI.

you can use the failsafe terminal mode from your session menu at the gui login or do it the traditional way .. ATL+CTRL+F1

---

### Post by RAOF on 2005-10-25
[QUOTE=blouie]I have even reinstalled gnome-panel and gnome-panel-data, and the panel is still dead. Does this tell me the problem is not in the panel or the data?[/QUOTE]
No, it doesn't.  The problem is almost certainly in some configuration for the panel, and reinstalling won't clear the configuration (which can be nice, or annoying, as in this case).  From the console, I think that
```
sudo dpkg-reconfigure gnome-panel
``` will get the default configuration back, and the panel should then work.

---

### Post by gillion on 2005-10-26
[QUOTE=RAOF]No, it doesn't.  The problem is almost certainly in some configuration for the panel, and reinstalling won't clear the configuration (which can be nice, or annoying, as in this case).  From the console, I think that
```
sudo dpkg-reconfigure gnome-panel
``` will get the default configuration back, and the panel should then work.[/QUOTE]

I tried that myself on the test account but it seems the reconfigure option doesn't go into user **.gconf** directories and does anything to them.

---

### Post by Joeb on 2005-10-26
[QUOTE=gillion]I tried that myself on the test account but it seems the reconfigure option doesn't go into user **.gconf** directories and does anything to them.[/QUOTE]


With all of the things you have tried, is it possible that you still have an instance of gnome-panel running and therefore the changes haven't taken place?  I'd try going back to the suggestion of logging out, dropping to a terminal and removing the .gnome2 directories.  Then I'd do a killall gnome-panel before doing the alt-f7 to log back in.  Alternatively, you go do a reboot while in the terminal, too.

---

### Post by drigloi on 2005-10-26
I had big troubles with gnome-panel back in the days of 2.8 (and it was in another distro). Certain kind of audio CDs with CD-text opened in Nautilus caused to suddenly kill the gnome-panel which was restarted but failed to start and was killed again in an endless loop.

I tried everything: wiping .g* dirs from my home dir, killing, messing with gnome-session-properties etc. Nothing helped.

But: the only thing worked for me is to create a brand new user for me. (of course I could reproduce the panel crash again with an audio CD, but fortunately after gnome-2.8 I haven't encounter this issue again).

I suggest you to create a new user. I think the command is something like "sudo useradd xxx" maybe "sudo adduser xxx" (sorry I'm not in front of Linux now). Also don't forget to add this user to the "admin" group to let sudo work with it. If you succeed with this solution you can remove your old user account and recreate it after.

---

### Post by blouie on 2005-10-27
[QUOTE=Joeb]With all of the things you have tried, is it possible that you still have an instance of gnome-panel running and therefore the changes haven't taken place?  I'd try going back to the suggestion of logging out, dropping to a terminal and removing the .gnome2 directories.  Then I'd do a killall gnome-panel before doing the alt-f7 to log back in.  Alternatively, you go do a reboot while in the terminal, too.[/QUOTE]

Not likely. I used "top" to make sure panel was not running.

---

### Post by Joeb on 2005-10-28
[QUOTE=blouie]Not likely. I used "top" to make sure panel was not running.[/QUOTE]

Top won't always detect gnome-panel.  If gnome-panel is sleeping, it won't show.  Try running the System Monitor under Applications under System Tools.  You'll see all kinds of gnome things running but they won't show under top.

---

### Post by flibble on 2005-10-28
Something to try:

Create a new user and login as that user. That should tell you whether it's a user specific .conf file that is corrupt. If it still doesn't work and you get really frustrated, you can always nuke it by totally removing gnome, remove all the config files completely, and reinstalling.

Sometimes, if you've accidently hosed a panel config, there can be extra panels floating around in the conf files that you don't really distinguish on the screen. These can make the panels you can see behave weirdly.

---

### Post by blouie on 2005-10-28
[QUOTE=Joeb]Top won't always detect gnome-panel.  If gnome-panel is sleeping, it won't show.  Try running the System Monitor under Applications under System Tools.  You'll see all kinds of gnome things running but they won't show under top.[/QUOTE]

What is the command-line for calling System Monitor?

---

### Post by GrumpyBob on 2005-10-28
[QUOTE=blouie]What is the command-line for calling System Monitor?[/QUOTE]

gnome-system-monitor

---

### Post by kashms on 2005-10-28
Or try "ps aux | grep panel" in a terminal (probably faster than finding it in system monitor).

---

### Post by gillion on 2005-10-28
Peraps Blouie is running around  like a frantic mouse ....

again ...

**Drop to a console login**

The easiest way to do this and make sure no instance of X is running is

**sudo init 1**

Then go to your **/home** directory

locate and delete this nested directory

**panel**

in this directory

**.gconfd**

I have used it over and over to delete flaky panel setups on a test ubuntu system.

when you are done deleting this directory/folder

run this command

**sudo init 2**

It will bring you back to a X login.

---

### Post by blouie on 2005-11-08
[QUOTE=gillion]Peraps Blouie is running around  like a frantic mouse ....

again ...

**Drop to a console login**

The easiest way to do this and make sure no instance of X is running is

**sudo init 1**

Then go to your **/home** directory

locate and delete this nested directory

**panel**

in this directory

**.gconfd**

I have used it over and over to delete flaky panel setups on a test ubuntu system.

when you are done deleting this directory/folder

run this command

**sudo init 2**

It will bring you back to a X login.[/QUOTE]

Gillion's advise worked. Many thanks to all thosed supported.
As a side note, for some reason, my "panel" directory was not in .gconfd.
```
find /home/blouie -name panel
```
yields
```
/home/blouie/.gconf/apps/panel
```
This is the "panel" directory I deleted.

I think my conclusion is that the panel customization functions are not robust. But now that I know how to reset it, I wouldn't hessitate to change it to my liking. Hopefully one of us can come up with a more precise account of the circumstances that can pin-point the error.

---

