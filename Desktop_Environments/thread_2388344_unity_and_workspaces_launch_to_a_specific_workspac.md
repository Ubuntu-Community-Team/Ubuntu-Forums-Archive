---
title: "unity and workspaces: launch to a specific workspace"
date: 2018-03-31
forum: Desktop Environments
---

### Post by Skaperen on 2018-03-31
i have enabled workspaces in unity.  i have even found the commands:

dconf write /org/compiz/profiles/unity/plugins/core/hsize 3
dconf write /org/compiz/profiles/unity/plugins/core/vsize 3

can be used to give me 9 workspaces in a 3x3 arrangement.

i would like to find out how to launch a program or open a window in a specific workspce.

i am running Ubuntu Desktop Xenial 16.04.3 LTS as upgraded a few days ago on a System 76 laptop.

---

### Post by mc4man on 2018-04-01
for this the compiz plugin "Place windows" will work.
Open ccsm > Place windows > Fixed Window Placement
Have the window you want to define open.

In Windows with fixed viewport click on New 
In the pop up click on green + , this will give you another pop up
Click on the Grab button, a + cursor will appear, move over window of app to be defined & left click
Click Add

Back at Edit window change the X position to horizontal, the Y position to vertical
(- probably for you those would be - 
1 1 or 1 2 or 1 3 or 2 1 or 2 2 or 2 3

In screenshot ex. I defined this for ccsm, setting to workspace 4 in a 1x4 setup (cube/rotate

(- note that the top option "Windows with fixed Placement will not work with your terminal profile placement deal as all terminal's are same window class & the window id option doesn't seem to  work..

---

### Post by Skaperen on 2018-04-01
there is already a process running named "compiz".  is that the plugin in need, or is there more i need to add in?  if the latter, can you tell me how to install it and plug it in?

i have more than one launcher buttons set up to launch terminals.  i will add a new one for the same size (82x46).  i assume this means to launch one from this button to have the window open.  i want a launch from this new button to launch in the new position.  i do not want terminals from other buttons to be affected.

this "fixed window" thing only applies to the one launch button?  how does it know which?

---

### Post by Skaperen on 2018-04-01
oops, my bad.  i mixed up the 2 questions i asked.  THIS ONE is about how to make a new window being opened by a program i am starting be started in a specific workspace.  if the only way to do it is relative, that should be OK since i am doing this always from the first workspace.

---

### Post by mc4man on 2018-04-02
> **Skaperen said:**
> there is already a process running named "compiz".  is that the plugin in need, or is there more i need to add in?  if the latter, can you tell me how to install it and plug it in?

i have more than one launcher buttons set up to launch terminals.  i will add a new one for the same size (82x46).  i assume this means to launch one from this button to have the window open.  i want a launch from this new button to launch in the new position.  i do not want terminals from other buttons to be affected.

this "fixed window" thing only applies to the one launch button?  how does it know which?This question was not about the gnome-terminal/ fixed window placement deal, only mentioned because you may see that other option in Place Windows plugin... and as said it will Not work with terminal profiles.

Not sure what you're asking about otherwise.., a guess would be to install compizconfig-settings-manager, then open with command of ccsm, insructions/screens in prior post to set a workspace for an app to open to.

---

### Post by again? on 2018-04-02
You used to be able to do this with gnome-terminal by setting a title.
You can do it with xfce4-terminal as the --title flag is still available.
Set a unique title and geometry if desired.
```
xfce4-terminal --title=termD4 --geometry 79x25+431+315
```

Then use ccsm as shown by mc4man to place windows of that title on a certain desktop.
[ATTACH=CONFIG]279160[/ATTACH]

This is an example unity launcher with a quicklist menu.
_~/.local/share/applications/xfce4-terminal.desktop_
```
[Desktop Entry]
Name=Xfce Terminal
Comment=Terminal Emulator
GenericName=Terminal Emulator
Exec=xfce4-terminal
Icon=utilities-terminal
Terminal=false
Type=Application
Categories=GTK;System;TerminalEmulator;
StartupNotify=true

Actions=termD4;termD7

[Desktop Action termD4]
Name=Term Desk 4
Exec=xfce4-terminal --title=termD4 --geometry 79x25+431+315

[Desktop Action termD7]
Name=Term Desk 7
Exec=xfce4-terminal --title=termD7 --geometry 79x25+431+315
```
In action vid----> [https://streamable.com/neoqz](https://streamable.com/neoqz)
This probably relates to your other thread as well.

---

### Post by vanadium on 2018-04-03
> **guber2 said:**
> You used to be able to do this with gnome-terminal by setting a title.
You can do it with xfce4-terminal as the --title flag is still available.

You can still set window class and window name of a gnome-terminal you launch. So also with gnome-terminal, tricks like this are still possible. See "gnome-terminal --help-all for all command line options.

---

### Post by again? on 2018-04-03
> **vanadium said:**
> You can still set window class and window name of a gnome-terminal you launch. So also with gnome-terminal, tricks like this are still possible. See "gnome-terminal --help-all for all command line options.
The ccsm "Place windows" plugin recognizes all gnome-terminals as **name=gnome-terminal-server**  even when you use the --name flag.

---

### Post by vanadium on 2018-04-03
You are right. It has become quite ugly to change the title of your gnome terminal. See here: [https://askubuntu.com/questions/22413/how-to-change-gnome-terminal-title](https://askubuntu.com/questions/22413/how-to-change-gnome-terminal-title)

After commenting out a section (case $TERM in ... esac) in your .bashrc, you can set a title with the --title option, or with a command such as
```

PROMPT_COMMAND='echo -ne "\033]0;SOME TITLE HERE\007"' gnome-terminal

```
[/code]
[/code]

---

### Post by monkeybrain20122 on 2018-04-03
> **vanadium said:**
> You can still set window class and window name of a gnome-terminal you launch. So also with gnome-terminal, tricks like this are still possible. See "gnome-terminal --help-all for all command line options.

I don't think this work anymore, it seems to be related to this old thread [https://ubuntuforums.org/showthread.php?t=2311359](https://ubuntuforums.org/showthread.php?t=2311359)

---

