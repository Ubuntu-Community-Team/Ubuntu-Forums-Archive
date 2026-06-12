---
title: "Unity Launcher Problems in 11.10 with Dual Screen"
date: 2011-12-31
forum: Desktop Environments
---

### Post by M1GEO on 2011-12-31
I have Ubuntu 11.10 running on my Office PC with the new Unity Launcher (I'm not sure of the exact terminology, just 'as it comes').  Having got used to the new style on my work machine, I decided to set it up on my home box too.

This machine has dual monitors, with an Nvidia card.  I've never had any trouble with this setup until now.  Allow me to elaborate:

[LIST=1]
[*]Minimised windows can be impossible to get back.
[*]The Launcher (left hand task-bar/window list remplacement) won't open if a window is "fullscreen" even when I bash with the mouse on the left screen side - This works on my Office PC (as expected)
[/LIST]

This is my main computer and Ubuntu is my only operating system; It has been for almost all Ubuntu's life.  I understand that dual-monitor systems cause major problems at the moment, and that they will be addressed in 12.04, but for the time being, is there anything that can help?

I would really appreciate any advice as it's driving me mad!

Thanks people - Happy New Year!

---

### Post by howefield on 2011-12-31
> **Compu-king said:**
> Minimised windows can be impossible to get back.

Alt + Tab or Super +W or clicking on the minimised app icon doesn't work ?

> The Launcher (left hand task-bar/window list remplacement) won't open if a window is "fullscreen" even when I bash with the mouse on the left screen side

Try installing compizconfig-settings-manager, then press Alt + F2 and run the command about:config, what's the Hide Launcher set to ?

> Happy New Year!

Same to you :-)

---

### Post by BC59 on 2011-12-31
I'm not very familiar to this problem but I could suggest you to install the latest NVIDIA drivers, if you already didn't install them.

And I found this answer in ask Ubuntu:

> Open nvidia settings. Note not to press the apply button.
Configure settings for the monitors to your liking for twin view.
Click save to x configuration file and an error message should appear.
After the error message, an option to save to the xorg.conf file will appear. Click on the "show preview" button.
Now in a terminal window, type "sudo gedit /etc/X11/xorg.conf." Be sure to save a backup of the text already in the xorg.conf file on your desktop or something. If something goes wrong, just revert to the original xorg.conf.
Copy the text from the preview window into the xorg.conf file. Save the xorg.conf file, close it, exit completely out of the nvidia settings without applying or saving any data, and restart your computer.
If all went well, the two monitors should work together.
When I was dealing with this problem, the original text in the xorg.conf file only had a section labeled "Device." The text pasted from the nvidia settings creates this section for you. Therefore, you should transfer what was in the original device section to the new device section.
answered Oct 16 at 13:45 bwright1558

---

### Post by M1GEO on 2011-12-31
> **BC59 said:**
> I'm not very familiar to this problem but I could suggest you to install the latest NVIDIA drivers, if you already didn't install them.
[snip snip]


Hi, thanks for the advice, but I'm already past that. I have the Nvidia drivers all installed, and they're all working fine. The two monitors work a treat. The issue is the desktop environment has some issues when using two monitors. It is all working from a hardware point of view, and I have Nvidia's twinview running fine. I just cant switch windows, the window manager seems to loose them for me?!

---

### Post by BC59 on 2011-12-31
I don't know if you tried to logon to GNOME Classic or GNOME Shell options offered during logon, to see if there is a difference in window management.

---

### Post by M1GEO on 2011-12-31
> Alt + Tab or Super +W or clicking on the minimised app icon doesn't work ?

I'm afraid not. I get the window switcher (I really have no idea for the proper names of these!) and all my windows are listed. Those with multiple instances such as web browsers (with different windows open) offer an expansion when I delay on them, but if they are "lost", for want of a better word, my only option is to kill them, and re-open them.  It's really weird.

> Try installing compizconfig-settings-manager, then press Alt + F2 and run the command about:config, what's the Hide Launcher set to ?

I managed to fix this issue though, with the command you mentioned.  The Hide Launcher parameter was set to Dodge Windows, but the reveal mode was set to Bottom. I changed this to match the launcher's location (Left) and was told that this conflicted with Desktop Wall Flicker (something like that) which I disabled.

I can't tell you how grateful I am for this piece of advice! It's been a slow month or so of me looking around going "It must be something I've done" and not getting anywhere.  No idea how this other plugin got enabled.

At the minute this seems to have fixed the other issue too; though quite how, I am unsure!  Where are these settings kept within my home folder? I'm half tempted to remove the folder and let Unity start again. I guess there must have been some residual stuff from the earlier 11.04 Unity (before I went back to the old style Gnome).

Just once again, Thanks very much. Have a good evening :)

---

### Post by M1GEO on 2011-12-31
> **BC59 said:**
> I don't know if you tried to logon to GNOME Classic or GNOME Shell options offered during logon, to see if there is a difference in window management.

I hadn't thought of that, I'll give that a try too.  It seems that there were some old configuration files floating around in my home folders (they're mounted on another HDD) and so don't get cleared with updates.

---

### Post by howefield on 2011-12-31
> **Compu-king said:**
> I managed to fix this issue though,..

Good to hear.

> Where are these settings kept within my home folder?

Could be ~/.config/compiz-1

---

