---
title: "Hotkeys for opening programs?"
date: 2008-07-05
forum: Desktop Environments
---

### Post by sr_guy on 2008-07-05
I have Ubuntu Hardy 8.04 installed. I'm wondering what the easiest solution to setting up keyboard short cuts to commonly used programs. For instance, I want to setup a keyboard shortcut to open Firefox, Thunderbird, SMplayer, or anything. Is there a program that can help set that up easily? Something simulre to the keyboard shortcut program in KDE.

Any help is appreciated.

---

### Post by p_quarles on 2008-07-06
Compiz config settings manager (ccsm) should have keyboard shortcut settings, does it not? (it's in the repos, if you haven't installed it already). 

If you don't want Compiz running, you'd need to use something  like the hotkeys package (also in the repos).

---

### Post by sdennie on 2008-07-06
As p_quarles said, ccsm can do this very well.  To install it:

```

sudo apt-get install compizconfig-settings-manager

```

Then, navigate to System->Preferences->Advanced Desktop Settings->General Options->Commands.  Then, in the Commands section you can set commands and in Hot Keys, you can assign hotkeys to that command.  These commands supersede application hotkeys so, you can also disable application hotkeys by assigning them in ccsm but not assigning commands to them.

---

### Post by hoooootz82 on 2008-07-06
If you need to add more shortcuts than the allowed 10 i believe you can add entries in the gconf-editor program. press ALT+F2 and type "gconf-editor", then navigate to /apps/metacity . I believe you can add entries to "global_keybindings" and "keybinding_commands" (probably have to match in name) but you just type the keyboard shortcut for the keybindings and then make your own custom command like "firefox" or whatever... (not exactly sure if this will work because metacity might not recognize any other entries than the default)

---

### Post by sr_guy on 2008-07-06
Hey thanks p_quarles. Compiz config settings manager works perfectly. I wish the ubuntu team built in a program into the preferences menu to link keyboard hotkeys to open programs. I tried Kbuntu and hated it. It crashed often and freaked out when I would remote desktop into the machine. I had Suse installed for the longest times and decided to go with Ubuntu because I was tired of the bloat in SUSE. Ubuntu has the basic all-in-one install without the unnecessary extras. Besides, if I want anything special, it's easy to go out and get with the software manager.

I have mythbuntu installed on a second machine that I use as a DVR.  The Ubuntu themed OS's have worked out well.

---

