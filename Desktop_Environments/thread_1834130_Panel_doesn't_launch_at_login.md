---
title: "Panel doesn't launch at login"
date: 2011-08-27
forum: Desktop Environments
---

### Post by scruffyeagle on 2011-08-27
This post is about a problem in Ubuntu v10.04 LTS using Gnome, on a Dell Inspiron 9400 laptop.

I did a extended session of selecting and installing hardware this evening. After that, I visited the forums here, checking on previous posts because I have an issue w/ my external HD not being allowed available for more than one user during a given boot session (i.e., rebooting allows a different user to access it). I added both users to the "disk" group, and when I switched users discovered that the gnome panel was missing. I tried several things including several reboots and removing the users from the "disk" group - but nothing worked. Lucking, the Admin profile still had the panel available. I used Firefox to come here and research seeking solutions. The only problem I've found in the Admin profile so far, is that FF had lost all its settings. I had to reset it from scratch, except for the add-ons.

After researching it here, I returned to the User profile, opened a terminal, and tried a few things.

*) Using gconf-editor, I found that the panel variable in the desktop sessions was still set as gnome-panel.

*) Entering the command ```
gconftool --recursive-unset /apps/panel && killall gnome-panel
``` didn't work. The system responded with the message "no process found".

*) I found that entering "gnome-panel" in the terminal launched the panel, with nothing missing. But, it would only remain as long as I left that terminal open; i.e., closing that terminal terminated the panel's program.

*) For the moment, as a work-around until I find an actual solution, I've created a launcher on the desktop. The command in it is simply "gnome-panel".

Can anybody help me? I've pretty much run the gamut on the solutions I was able to find on the forums here, without being able to fix this panel problem.

---

### Post by jerrrys on 2011-08-28
that usually works...

open synaptics and do a complete removal and reinstall.  that should restore the config settings

---

### Post by scruffyeagle on 2011-08-29
> **jerrrys said:**
> that usually works...

open synaptics and do a complete removal and reinstall.  that should restore the config settings

Thank you for your reply! Yes, I'd read a thread where the OP was advised to do that. He did, and it worked - but, a side effect was the loss of applets from the panel. He wrote that it required a lot of work, restoring those applets. I've done a lot of software installation in this system, and also a lot of tweaking of the menus to make it more structured & logical. I'd really hate to lose the menus, because then I'd have to go through all that, all over again. Given the sluggishness of the "Main Menu"'s reactions to changes, it's very time-consuming.

I was hoping that someone would have an editing solution... I know I'd learn a lot in the course of following the instructions, relaying results back here, etc.

---

### Post by false truths on 2011-08-29
If it's not launching on login, you can add it to your login commands to force it to start with everything else.

Go to system, preferences, Startup Applications.

Add a startup application and put the command as gnome-panel. You can name it and label it whatever you want, it doesn't affect the functionality but if the name is misleading it may confuse you later.

Once you've added the panel as a startup application, log out and back in to see if it worked.

---

### Post by scruffyeagle on 2011-09-01
> **false truths said:**
> If it's not launching on login, you can add it to your login commands to force it to start with everything else.

Go to system, preferences, Startup Applications.

Add a startup application and put the command as gnome-panel. You can name it and label it whatever you want, it doesn't affect the functionality but if the name is misleading it may confuse you later.

Once you've added the panel as a startup application, log out and back in to see if it worked.

You know, I was _sure_ I'd tried that before - and, that it hadn't worked. But, just to make that 100% certain before replying here, I tried it again. And, it worked! At that point, I returned to the Admin profile and removed the User from the "sudo" group. Rebooted, and tried the User profile again, and it's still working. I find this functioning result to be puzzling, but it is better than my work-around of using a launcher on the desktop. So, thanks for the suggestion!

Of course, despite the improvement, it is still just a work-around to compensate for a loss of automated activity in Gnome. In the original setup of Gnome, the panel was launched without being listed in the startup applications menu. Which means that something changed to cause the loss of functionality. Somewhere in the scripts, there's a glitch that's preventing Gnome from automatically starting up the panel without being prodded to do so by me (via the startup applications menu). So, although the disfunction isn't anywhere near the level of issue it was before, I can't really consider this to be "fixed" or "solved" until it's corrected.

---

