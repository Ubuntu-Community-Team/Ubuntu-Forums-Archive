---
title: "Compiz Fusion not using my gnome keyboard shortcuts and other settings"
date: 2007-08-14
forum: Desktop Effects &amp; Customization
---

### Post by glosman15 on 2007-08-14
Hello, I recently noticed that I can't use any of the keyboard shortcuts i have setup in GNOME when im running in XGL with compiz fusion, also my sound settings and power management settings dont work either.  Is there a solution for this?

---

### Post by praet on 2007-08-16
Compiz fusion actually has its own set of keyboard mapping
System > Preferences > CompizConfig Settings Manager

Select the "Actions" tab and customize your keyboard shortcuts there.

What sound and power management settings are not functional? No issues here.

---

### Post by ZoraQ on 2007-08-20
I have a similar problem. Initially when i installed compiz fusion, it would do my keybindings just fine.  I had set my left "super" or "windows" button to open a terminal, and it worked fine before. 

Now, after updating to the newest release of compiz-fusion, every other keybinding OTHER than the one to launch the terminal works. It is so strange because it doesn't matter what I change the binding to, it just won't open a terminal. Furthermore, I tried to follow the above instructions, but i saw no "Actions tab".  I also tried editting their 'run a custom command' dialogues, but there is no option to bind keys to execute these custom commands in the CCSM.  

Any further help would be greatly appreciated.

-ZoraQ

---

### Post by haroonie on 2007-08-20
I too have the same problems.  After updating compiz fusion, my keybindings are gone ... i also see no "actions" tab.  compiz is running but i can't customize it, the changing i make in the settings manager don't take.

:confused:

---

### Post by praet on 2007-08-20
I apologize for not being clear about the steps in my previous post.

Open the compiz settings manager:
System > Preferences > **CompizConfig Settings Manager**
( /usr/bin/ccsm )

In the settings manager, in the general category should be "**General Options**". 
Here you can change things like having an audible bell, number of desktops, focus behaviour, and, custom keybound commands.

Here's how to to do it:
Select the "**Commands**" tab, here you have 12 slots for custom commands (0-11). Plus the ability to specify the screenshot and window only screenshot commands.

In "**Command line 0**" type in "gnome-terminal". (or whatever commandline you are seeking to run)

Now, we need to specify which action to bind to the command.  
In the same general options window, select the "**Actions**" tab.

 Here you can customize the default window actions in the General tree section (like close window = Alt-f4), as well as our own custom commands in the "Commands" tree branch.

For the command above, select "**Commands > Run command 0**", single left click the **Key** column, it will change to "New accelerator...", and type the key combination (I pressed Ctrl+Alt+t).

That should set the action to the command.  Typing your key binding should activate the command entered previously.
You can add more actions the same way.  I have added Ctrl+Alt+Del to bring up system monitor, as well as Ctrl+Space to bring up gnome-launch-box.  

Lastly, you can set an action to any compiz binding, like the bottom left screen edge for terminal.
Have fun.


See the screen shots attached for clarification.

---

### Post by vapore0n on 2007-08-20
that works for the old version of compiz-fusion

After updating, the Actions tab is missing.

What was the command to enter the "regristry" of ubuntu? The settings should show there too, so maybe we can manually enter them there.

---

### Post by praet on 2007-08-20
The configuration editor is what you are looking for: gconf-editor.

What version of compiz are you working with?
Mine says 0.5.2-0ubuntu2~ppa1 from Amaranth's repository.

---

### Post by forsberg on 2007-08-20
Yes I have the same problem - seems like the latest version of compiz fusion are missing a lot of action tabs.

what gives?   I can't use my old mapping to zoom anymore.

---

### Post by orangebase on 2007-08-20
Same problem here. Any workaround?

---

### Post by vapore0n on 2007-08-20
tried manually editing the gconfig for compiz, and it doesnt want to work. As if it wasnt reading the values from anywhere.

In metacity all my shortcuts work. None for compiz 0.53. 

Its an already reported bug. Many people are going back to 0.51 till this ccsm problem gets fixed.

---

### Post by ZoraQ on 2007-08-20
Here is the other really wacky thing.  When I switch back to metacity so that I can play some games, I find that alt+tab no longer works! It is really weird because it worked just fine in metacity prior to my installing compiz.

Thanks for the quick responses.

-ZoraQ

---

### Post by 00l0 on 2007-08-21
> **vapore0n said:**
> that works for the old version of compiz-fusion

After updating, the Actions tab is missing.
.

same problem, im rlly looking forward a solution  ;(

---

### Post by ZoraQ on 2007-08-25
Well, updating to the latest version of compiz in the repositories seems to fix all the problems. Thanks everyone.

-ZoraQ

---

### Post by 00l0 on 2007-08-26
yeah it's all fixed now, thanks to all developers! :]
the only thing missing now is how to set extra keyboard keys as keybindings to ccsm, Gnome's shortcut editor recognized me thos extra keys as adresses(0x81, 0x94...) but i dunno how to assign those to CCSM

thanks

---

