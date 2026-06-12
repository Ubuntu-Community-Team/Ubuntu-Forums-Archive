---
title: "startup issues on XUBUNTU"
date: 2013-06-12
forum: Desktop Environments
---

### Post by jfbooth on 2013-06-12
Running Xubuntu 12.04 with XFCE 4.8.  On startup, I get the following:

**No running instance of XFCE4 - PANEL was found.  Do you want to start the panel ......**

and the options to cancel or execute.  Clicking execute gives:

**Modifying the panel is not allowed.  Because the panel is running in kiosk mode, you are not allowed to make changes to the panel as a regular user.**

and a close button.  Clicking on Close gets me to the desktop.  Please advise on correcting this condition and achieve normal operation.

Thank you in advance.

---

### Post by Bashing-om on 2013-06-12
[COLOR=#000000]jfbooth; Hi !

When you boot up your system; Are you intending to obtain a Desk Top manager ? which, if so,
Are you booting to a TTY text login ? -> what command are you using to start the X session and Desk Top ?
[/COLOR][INDENT=2][COLOR=#000000]
process, one thing then another


[/COLOR][/INDENT]

---

### Post by jfbooth on 2013-06-12
> **Bashing-om said:**
> [COLOR=#000000]jfbooth; Hi !

When you boot up your system; Are you intending to obtain a Desk Top manager ? which, if so,
Are you booting to a TTY text login ? -> what command are you using to start the X session and Desk Top ?
[/COLOR][INDENT=2][COLOR=#000000]
process, one thing then another


[/COLOR][/INDENT]


This started happening after some kind of update from Update Manager.  Before, it would smoothly boot up to XFCE with no errors ... then this started happening.  Sorry, .. I have been confused for years about GNOME, XFCE, KDE ... etc, etc.  To some extent, these are selectable desktop 'environments' .. I guess.  I prefer XFCE (from what little I know).  That is why I listed XFCE 4.8 in my post . not enough info???

I boot to an XUBUNTU 'GUI' login screen ... user name, p/w, and XFCE chosen/default.  Hope that answers that question.  It is not a TTY text screen.

As mentioned . not using any 'command' to start X session/Desktop.  It WAS all done automatically after entering P/W ... and still does .... but with these error messages/notifications.  I hope I have answered substantially ... and THANK you for your reply/support.

---

### Post by Bashing-om on 2013-06-12
[COLOR=#000000]jfbooth;

Yeah, the desk top environments are but the eye candy for the interface to the kernel...different strokes for different folks.

xfwm4's panel error... lets try this:
boot up xfce4 and do terminal code:
```
rm ~/.config/xfce4/panel
``` will be rebuilt upon next login to the default values.
So, after removing the file, log out and log back in.

What results ?
[/COLOR][INDENT=2][COLOR=#000000]
cheers

[/COLOR][/INDENT]

---

### Post by jfbooth on 2013-06-12
> **Bashing-om said:**
> [COLOR=#000000]jfbooth;

xfwm4's panel error... lets try this:
boot up xfce4 and do terminal code:
```
rm ~/.config/xfce4/panel
``` will be rebuilt upon next login to the default values.[/COLOR]


```
jb@jb-Compaq-PC:/$ rm ~/.config/xfce4/panel
rm: cannot remove `/home/jb/.config/xfce4/panel': Is a directory
```

and here are the contents of that directory:

```
jb@jb-Compaq-PC:~/.config/xfce4/panel$ ls
[COLOR="#0000FF"]launcher-10  launcher-12[/COLOR]  netload-16.rc
[COLOR="#0000FF"]launcher-11  launcher-9[/COLOR]   xfce4-notes-plugin-18.rc
jb@jb-Compaq-PC:~/.config/xfce4/panel$
```

with folders in [COLOR="#0000FF"]BLUE[/COLOR]

EDIT:  So .. I renamed 'panel' and REBOOTED.  Logged back in and got the same startup errors.  Looked at the folders/files and here is what I find:

```
jb@jb-Compaq-PC:~/.config/xfce4/panel$ ls
netload-16.rc  xfce4-notes-plugin-18.rc
```

and ICONS are now generic on PANEL 2 (bottom of screen).

---

### Post by Bashing-om on 2013-06-12
[COLOR=#000000]jfbooth; Yukk !

Let me do some homework on this.. fyi , my output with xfce4 desktop:
[/COLOR]> 

sysop@1304mini:~$ ls -la ~/.config/xfce4/panel
total 8
drwxrwxr-x 2 sysop sysop 4096 May 24 00:24 .
drwxrwxr-x 6 sysop sysop 4096 Jun  3 23:45 ..
sysop@1304mini:~$ 
 Totally different !

Must be something in the desktop managers you have installed...
[INDENT=3]
I be looking

[/INDENT]

---

### Post by jfbooth on 2013-06-12
> **Bashing-om said:**
> [COLOR=#000000]jfbooth; Yukk !

Let me do some homework on this.. fyi , my output with xfce4 desktop:
[/COLOR] Totally different !

Must be something in the desktop managers you have installed...
[INDENT=3]
I be looking

[/INDENT]


Just to let you know ... when it did not get fixed ... I deleted 'panel' folder and went back to the ORIGINAL ... rebooted ... expecting to work (fail) as before.  It did fail as before .. but now, .. the panel at the bottom of the desktop has just some generic icons ... which were different from originally:

[ATTACH=CONFIG]243768[/ATTACH][ATTACH=CONFIG]243768[/ATTACH]

No big deal .. just wanted you to know.  I predicted that would not change.

At the moment, here is what we have:

```
jb@jb-Compaq-PC:~/.config/xfce4$ ls
[COLOR="#0000FF"]desktop     panel[/COLOR]              xfce4-notes.rc      [COLOR="#0000FF"] xfconf[/COLOR]
helpers.rc  xfce4-notes.gtkrc  xfce4-screenshooter  [COLOR="#0000FF"]xfwm4[/COLOR]
```

```
jb@jb-Compaq-PC:~/.config/xfce4/panel$ ls
[COLOR="#0000FF"]launcher-10  launcher-12[/COLOR]  netload-16.rc
[COLOR="#0000FF"]launcher-11  launcher-9[/COLOR]   xfce4-notes-plugin-18.rc
jb@jb-Compaq-PC:~/.config/xfce4/panel$
```

and most importantly, .. THANK YOU.

---

### Post by Bashing-om on 2013-06-12
[COLOR=#000000]jfbooth; Hey.
looking about and this is the suggested solution from several forums:
log out of xfce
ctl+alt+f1 to get a console
in terminal enter:
```
rm -rf $HOME/.cache/sessions
```
ctl+alt+f7 (GUI) and log back in.
All now should be back to defaults, so have to reset all.

> 
For reference here is my listing - yours will differ somewhat.
[/COLOR]> sysop@1304mini:~$ ls -la $HOME/.cache/sessions
total 32
drwx------  4 sysop sysop 4096 Jun 12 19:50 .
drwx------ 12 sysop sysop 4096 Jun 12 19:52 ..
drwx------  2 sysop sysop 4096 May 20 00:46 thumbs-1304mini:0
drwx------  2 sysop sysop 4096 May 24 18:52 thumbs-1304mini:1
-rw-rw-r--  1 sysop sysop 2341 Jun 12 19:50 xfce4-session-1304mini:0
-rw-rw-r--  1 sysop sysop 2341 Jun  9 02:46 xfce4-session-1304mini:0.bak
-rw-rw-r--  1 sysop sysop 2030 May 24 18:52 xfce4-session-1304mini:1
-rw-rw-r--  1 sysop sysop    0 May 24 18:52 xfwm4-22afcbde7-da73-40dd-a992-64145bb19889.state
-rw-rw-r--  1 sysop sysop  364 Jun 12 19:50 xfwm4-2b9216a38-3b45-49ff-9e3d-abe1c58ecb2f.state
sysop@1304mini:~$ 


I expect this to fix xfce, then look at the window managers... see if they survive intact or have to be repaired as well.[INDENT=2]
progress small steps at a time

[/INDENT]

---

### Post by jfbooth on 2013-06-12
Thank you for the valuable time you are spending.  I really appreciate it.

> **Bashing-om said:**
> jfbooth; Hey.
looking about and this is the suggested solution from several forums:
log out of xfce

**I take that to mean 'log out' ... which will take me to a LOG IN screen ... which wants my P/W to the desktop (xfce).  At THAT screen, hit:**

> ctl+alt+f1 to get a console

**and get:**

> in terminal

[B]Right???  I have never 'logged out of xfce' except to just log right back into it.  After getting in terminal, don't I have to log in there before I can proceed?

Confirm all this, and I will proceed.  Thank you.[/B]

> 
 enter:
```
rm -rf $HOME/.cache/sessions
```
ctl+alt+f7 (GUI) and log back in.
All now should be back to defaults, so have to reset all.

**Not sure what is meant by "reset all."  If that means Application menus etc etc ... most everything I have is DEFAULT ... I would not know how to reconstruct (much).**

> 
I expect this to fix xfce, then look at the window managers... see if they survive intact or have to be repaired as well.

**Window Managers???   Uhmmmm, ... maybe I need to back something up b4 I proceed.  NEVER done a backup of any kind with Linux.  In this case, isn't it just make a copy of HOME directory and put it somewhere safe (thumb drive or CLOUD) ... or is it more complicated than that (backing up whatever I need to back up)?.  Sorry to be so ignorant.**

---

### Post by Bucky Ball on 2013-06-12
Yes, backup the /home directory, but not hidden files or Desktop or Lost&Found. Hit ctl+h to see hidden files if you want to have a look, and again to hide them.

Back to the current situation. Once you're at the terminal, then input the command, but you may need a 'sudo' if you are not already root:

```
sudo rm -rf $HOME/.cache/sessions
```

Just a heads up; please use default text rather than bold. I realis this may not have been intentional but just letting you know. Thanks. :) 

From the forum Code of Conduct:

> Use color and font properties for highlighting portions of your text, and not for all of the text in your post. Please use the default font color and properties unless you need to highlight or draw attention to a part of your post. ALL CAPS is interpreted as screaming. [size=2][COLOR=pink]Funky[/size][/COLOR] non-uniform font size/color is difficult for those who are visually impaired. If you are having problems with reading the font, please adjust your browser.

---

### Post by Bashing-om on 2013-06-13
[COLOR=#000000]jfbooth;

It is most wise to be cautious. 
I do not anticipate that anything we do at this point can affect anything else than the WM and the settings for the xfce desktop.
And yes, doing that "rm -rf" command and logging back in, you will loose any and all alterations you have made to the xfce desktop.
In the event you have made extensive alterations from default that you desire to resort back to... what can be done is save all the files residing in /.cache/sessions ...upon re-activating xfce one can - one at a time - copy a saved file back and log-out and in to see the effects. A very long and tiresome process to be sure. That method will isolate the file that is producing the errors.
Backups: backing up ones "/home" directory should be a standard policy if one does not regularly make backups of important files via other means. I know of no reason in a standard install to back up any other files. In the event of catastrophic system corruption, (re-)installation is the cleanest solution to restore.

As you use a windows manager to log into the xfce desk top... I would expect when one logs out from xfce that one would return to the login gui screen. If you do indeed -when logging out of xfce - you get a text login terminal... that will work just as well for the purpose of removing "$home/.cache/sessions.

It is of no shame to have ignorance .. none of us were born knowing what we know, you are but lacking and that given time is amendable !

There is no hurry on my part to resolve the error in xfce... nor do I mind taking things in small steps - sometime I prefer to.
Can you now login to your xfce desktop ? When booting are you booting  to the GUI login or are you getting a text login ?
We need to know where you are to give the requested guidance.

Now here is what is: I am tired now and preparing to retire for the night, I have to be away from the keyboard most of tomorrow but I will return in my eve (GMT-6). In the meantime I want you comfortable with executing this minor procedure, Rest assured we are not messing about with any system files. Just config files that are replaceable (that is what we are doing). Take your time and be aware of exactly what we are doing to your computer. I want you knowledgeable. aware, and comfortable.

Be advised there are hundreds of people to "take up the slack" if there is a problem following the guidance given and I am not available to take care of that situation.

From the GUI login screen, by all means play around with the console (terminal), ctl+alt+f1 -> CLI, then look at your computer from a files perspective:
terminal command:
```
ls -la $HOME/.cache/sessions
ls -~/.cache/sessions
```
Ask yourself why the output is the same...look at the lines in the output, a lot of information is there. A line starting with a "d" is a directory (ok ya may call it a folder ), a line starting with a "-" is a file ...Files may be accessed by many means and one can see what is in a file:
```
 cat ~/.cache/sessions/<file_name>
```Never any harm in just "reading" a file.[INDENT=2]
'till tomorrow eve [/INDENT]
[INDENT=6]cheers
 [/INDENT]

[/COLOR]

---

### Post by Bashing-om on 2013-06-13
[COLOR=#000000]jfbooth;; Hey,

Just checking on your status... I will be away for a few hours... I check back in then.
[/COLOR][INDENT=2][COLOR=#000000]
later

[/COLOR][/INDENT]

---

### Post by jfbooth on 2013-06-13
> **Bucky Ball said:**
> Yes, backup the /home directory, but not hidden files or Desktop or Lost&Found. Hit ctl+h to see hidden files if you want to have a look, and again to hide them.

The result of what I did was a bunch of empty directories .. so I did not bother to back up $HOME at all.

> Back to the current situation. Once you're at the terminal, then input the command, but you may need a 'sudo' if you are not already root:

```
sudo rm -rf $HOME/.cache/sessions
```

Did entire list of instructions.  NO startup errors .. all original problems appear fixed.  Everything appears normal except those 4 'dead' icons on the lower panel.  Must not be too tragic ... at the moment, I don't even remember what they were linked to..

> Just a heads up; please use default text rather than bold. I realis this may not have been intentional but just letting you know. Thanks. :) 

From the forum Code of Conduct:

My apologies.  My intent was to make the post EASIER to discern.  I will not do that again.  Thank you for the advice.  I am thinking this thread is resolved .... and I want to thank you immensely ... for your technical help and your patience with me.  Thank you again.  :D

EDIT:  Isn't there some way to compliment you on/to the forum for your assistance?  Some forums offer that, but I don't see it here.

---

### Post by Bucky Ball on 2013-06-13
We don't have that here. Marking the thread solved by following the link in my signature will suffice. Cheers. ;)

PS: Good news it appears to be running ok.

---

### Post by Bashing-om on 2013-06-13
[COLOR=#000000]jfbooth; Pleased ya got it resolved... up and running.

That lower panel is "panel 2" and from the settings menu you may add whatever you like to it ...I found that second panel of no value to me and from the setting menu i removed it.

And as far as an expression of gratitude... you have... as our moderator advises - it is not done here ! - We are all of a friendly group, our purpose is to assist and promote ubuntu... The greatest thanks is to pass this along to someone else in need and your having attained the ability to help.

Remember, we are here ... and there is no such thing as a stupid question.
[/COLOR][INDENT=4][COLOR=#000000]
enjoy
 [/COLOR][/INDENT]

---

### Post by Bucky Ball on 2013-06-13
Never use that bottom panel myself and always remove first thing post-install, but then I like things clean and few bells and whistles. Auto-hiding top task bar so when I boot my computer I end up looking at just the wallpaper, no icons, taskbars or anything else. Just the way I like it ... boring! ;)

---

### Post by jfbooth on 2013-06-13
> **Bucky Ball said:**
> Never use that bottom panel myself and always remove first thing post-install, but then I like things clean and few bells and whistles. Auto-hiding top task bar so when I boot my computer I end up looking at just the wallpaper, no icons, taskbars or anything else. Just the way I like it ... boring! ;)

Panel 1 seems ample enough.  First time I saw an UBUNTU desktop .. first thing I noticed was Panel 2.  I am more amused with it than need it.  I keep it around and put first this and then that on it.  Teaches me a little bit about the GUI.  Thank you all again.  :D

---

### Post by llanitedave on 2013-06-14
I use the bottom panel as a popup launcher.  It stays out of the way unless I need it.

---

### Post by jfbooth on 2013-06-15
I thought my problem was fixed.  Sadly, I just discovered:

On 'restart', I get the XFCE login screen.  I provide p/w, ... then get the same screen again.  Log in again and am at desktop where everything works OK.

During that _restart_, I notice that all those messages that scroll along as you restart ... _before_ the log in screen, are severely scrunched vertically.  Before, they scrolled up in normal size 'terminal' text.

I THINK I must be running two XFCE 'sessions' ... or sumptin(?).    :(

EDIT:  Also .. system overall seems noticeably sluggish.

---

### Post by Bucky Ball on 2013-06-15
I advise you post another thread with a descriptive title about this new issue to improve your chances of help. Whatever info you can think of and in the appropriate sub-forum. 

You'll have more luck rather than buried 20 posts deep on a thread with an unrelated title. Good luck. ;)

---

