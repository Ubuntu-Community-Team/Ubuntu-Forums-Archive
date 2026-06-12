---
title: "[SOLVED] Disable compiz from Recovery Mode's CLI"
date: 2008-01-28
forum: Desktop Effects &amp; Customization
---

### Post by Bruce M. on 2008-01-28
I'm running Feisty, and I started "compiz" - the experimental thing - to see if it would "wobble" my windows.  What it did was give me a White Screen and a Mouse.

Check [here]("http://ubuntuforums.org/showthread.php?t=680854") for more info about my problem, and things I've done so far.

This is a better place for this question, since it's not just the white screen anymore, I know I have to turn off compiz, I'm getting close to the answer, **replace metacity for compiz**, but in the white screen I see nothing, so I have to do it from the Recovery Mode CLI, or from here - Live CD for 6.06 LTS.

Problem is I have no idea what commands to use there to disable compiz, in my default session: xclient script, from the Recovery Mode CLI, nor from the Live CD.

Any help would be appreciated.
Thanks
Bruce

---

### Post by Bruce M. on 2008-01-28
sudo chmod 755 ~/.compiz -R

Will this work in the Recovery Mode for Feisty?
I'm still researching this.

---

### Post by Bruce M. on 2008-01-28
In failsafe Terminal (Feisty), will this work?

To remove compiz and beryl/emerald. Open a terminal and type in the following code

sudo apt-get remove compiz* && sudo apt-get autoremove

then:

sudo apt-get remove beryl* emerald* && sudo apt-get autoremove

The only reason I know about this is i too tried compiz and didn't like its results. Couldn't seem to get all settings to work.

Do I need to remove beryl and emerald?
What are they?
Will this remove "Ubuntu Desktop" or metacity?EDIT

**EDIT:** sudo apt-get remove compiz* && sudo apt-get autoremove, doesn't work.
**Help! Please, somebody!**

---

### Post by Bruce M. on 2008-01-29
SUCCESS!

ebash told me I needed to edit: %gconf.xml, and change references of compiz to metacity 

found here: /.gconf/desktop/gnome/applications/window_manager/%gconf.xml

I did this:

1. Booted to safe Terminal mode, that way I was in my system, not Live CD.
2. cd'd my way down one folder at a time to see if each existed.
3. Upon reaching: window_manager I did a DIR and saw the file.
4. Tried **nano %gconf.xml** ... it created an empty file, no not right, exited;
5. **sudo nano %gconf.xml** <<-- did the trick.

Bruce says: Thanks ebash, I owe you one.

---

