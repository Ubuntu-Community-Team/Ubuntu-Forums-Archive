---
title: "screen lock doesn't work in Xubuntu Gutsy 7.10"
date: 2007-10-21
forum: Desktop Environments
---

### Post by ybukhman on 2007-10-21
Hi,

I've just installed the new Gutsy 7.10 release of Xubuntu on my laptop, HP Omnibook XE3 GC.  The screen lock doesn't work: when I press Ctrl-Alt-Del or screen lock button, nothing happens.  It used to work in Feisty.  The screen lock is important to me: I have a 4 year old daughter who shows active interest in the computer.  Any ideas?

Thanks.

Yury

---

### Post by ezak on 2007-10-21
By default, it should be:

Alt+Ctrl+L 

I would also recommend adding the "Lock Screen" icon to your desktop panel for easier access to locking your screen :wink:

---

### Post by ybukhman on 2007-10-22
Alt + Ctrl + L doesn't work for me.  I did add the "Lock screen" icon to my panel, and it doesn't work either.

---

### Post by ezak on 2007-10-22
Maybe try going to "Keyboard Shortcuts" even? Manually configuring yourself a shortcut to lock the screen?

---

### Post by pac-man on 2007-10-22
I had the same problem, when I had xubuntu 7.04 it used to work. Now with gutsy it didn't anymore.

The solution is simple, do the following:

*sudo apt-get install xscreensaver*

And now everything should work as before.

---

### Post by pleclerc on 2007-10-23
Just to confirm that installing xscreensaver does work.  I can't get alt-ctrl-l to work but at least the screen lock button works.

One suggestion for people diagnosing issues like this is to view the Xsession errors logfile in their $HOME dir, i.e. $HOME/.xsession-errors
This led me to see that the locker was trying to run xscreensaver-command and why also trying to kick off xlock.  I actually ended up installing both but xscreensaver was probably enough.

---

### Post by pac-man on 2007-10-23
Well, if ctrl+alt+L doesn't work you should change the keystroke combinations of XFCE:

Desktop Settings > Window manager > Keyboard tab

and change the default "ctrl+alt+del" to the desired value.

BTW: what's bad about using ctrl+alt+del ?? i guess it's the same than ctrl+alt+L.. both choices are 3 keystrokes whats the big deal?

---

### Post by ybukhman on 2007-10-25
I have installed xscreensaver, and it does work.  However, I have to manually start it from the command line.  What do I need to do to make it start automatically when the computer boots up?

---

### Post by jlovell_esd189 on 2007-11-30
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/xubuntu-meta/+bug/68251](https://bugs.launchpad.net/ubuntu/+source/xubuntu-meta/+bug/68251) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I believe I have found the root of the problem and a workaround.

**The Problem**

Xubuntu 7.10 is setup to use the GNOME screen savers however the process doesn't get started when you load XFce .

To confirm this is your problem run gnome-screensaver from a terminal (inside your x session).
Now try to lock the screen, it should work.

**The Workaround**

1) Pull down the **Applications** menu.
2) Select the **Settings** menu.
3) Click on **Autostarted Applications**.
4) Chose **Add**.
5) Give it the name **GNOME Screensaver**.
6) Enter the description **So we can lock the screen**.
7) Provide **gnome-screensaver** as the command.
8) Click **OK**.
9) Select **Close**.
10) Now logout and back in.

---

### Post by RJ Hythloday on 2008-03-28
> **jlovell_esd189 said:**
> **This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/xubuntu-meta/+bug/68251](https://bugs.launchpad.net/ubuntu/+source/xubuntu-meta/+bug/68251) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
                I believe I have found the root of the problem and a workaround.

**The Problem**

Xubuntu 7.10 is setup to use the GNOME screen savers however the process doesn't get started when you load XFce .

To confirm this is your problem run gnome-screensaver from a terminal (inside your x session).
Now try to lock the screen, it should work.

**The Workaround**

1) Pull down the **Applications** menu.
2) Select the **Settings** menu.
3) Click on **Autostarted Applications**.
4) Chose **Add**.
5) Give it the name **GNOME Screensaver**.
6) Enter the description **So we can lock the screen**.
7) Provide **gnome-screensaver** as the command.
8) Click **OK**.
9) Select **Close**.
10) Now logout and back in.

I've done all that and gnome-screensaver shows up in autostarted applications but I still can't figure out how to lock the screen. I was expecting ctrl+shift+L

---

### Post by RJ Hythloday on 2008-04-04
I got screenlock working but the wierd thing is I can't reboot w/ ctrl+alt+del it locks the screen.

---

### Post by luke16 on 2008-05-03
Lock screen and launch system managers shortkeys have never worked for me either, and this still hasn't been fixed, even in hardy.

---

### Post by jis on 2008-05-04
gnome-screensaver is better option than xscreensaver because it locks screen if you have chosen "suspend when laptop lid is closed" in Screensaver Preferences / Power Management Preferences. Even that does not lock screen if you choose Suspend from Action Buttons.

---

### Post by d4v1dv00 on 2008-06-30
> **luke16 said:**
> Lock screen and launch system managers shortkeys have never worked for me either, and this still hasn't been fixed, even in hardy.

The correct way to get screenlock with Xscreensaver working in Hardy is follow:

1. Right click on Panel, select Add New Item
2. Choose Action Buttons from the list
3. You will see another Quit button, right click on the Quit button
4. Select Lock Screen from the Select action type drop down list
5. Right click to select Move to the right position

---

### Post by luke16 on 2008-06-30
> **d4v1dv00 said:**
> The correct way to get screenlock with Xscreensaver working in Hardy is follow:

1. Right click on Panel, select Add New Item
2. Choose Action Buttons from the list
3. You will see another Quit button, right click on the Quit button
4. Select Lock Screen from the Select action type drop down list
5. Right click to select Move to the right position

There is no "action buttons " item on my list. If you wanted to put a lock screen button on the toolbar, then there should a specific button just for that in the list.

What I meant in my post was that the lock screen *shortcut keys* and the launch system manager shortcut keys do not work. I didn't mean lock screen itself. I probably should have been more clear on that.

---

### Post by Skimmer on 2008-07-01
> **jlovell_esd189 said:**
> **This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/xubuntu-meta/+bug/68251](https://bugs.launchpad.net/ubuntu/+source/xubuntu-meta/+bug/68251) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I believe I have found the root of the problem and a workaround.

**The Problem**

Xubuntu 7.10 is setup to use the GNOME screen savers however the process doesn't get started when you load XFce .

To confirm this is your problem run gnome-screensaver from a terminal (inside your x session).
Now try to lock the screen, it should work.

**The Workaround**

1) Pull down the **Applications** menu.
2) Select the **Settings** menu.
3) Click on **Autostarted Applications**.
4) Chose **Add**.
5) Give it the name **GNOME Screensaver**.
6) Enter the description **So we can lock the screen**.
7) Provide **gnome-screensaver** as the command.
8) Click **OK**.
9) Select **Close**.
10) Now logout and back in.
Thank you, jlovell, for sorting this one out- it does seem that Xubuntu lightens the process load by not starting gnome-screensaver. Using your solution, I later discovered that I didn't have to put a lock icon on the panel, but could instead just press ctrl-alt-delete to lock the screen. Works great!

Cheers, SK

---

