---
title: "Error opening terminal: xterm."
date: 2015-04-09
forum: Desktop Environments
---

### Post by philip10 on 2015-04-09
Using Ubuntu 14.04

When i type "nano" into the terminal I receive the following message:
Error opening terminal: xterm.

Typing "top" will give this message:
'xterm': unknown terminal type.

Word wrap is not working when I push backspace on a multi-line command.

Ctrl+Alt+F6 -> commands work fine.
xterm works fine.
Have tried creating a new user but it has the same problem.
Tried what was suggested [here]("http://ubuntuforums.org/showthread.php?t=2197486") but it doesn't help.

Any other suggestions out there?

---

### Post by egeezer on 2015-04-11
Not all that familiar with the Unity system, but in Systems > Settings > Preferences, which terminal is set as preferred?

---

### Post by philip10 on 2015-04-11
Just adding to the list of symptoms. When typing "man <something>" The following message will be shown "WARNING: terminal is not fully functional"

I found this command to find out which terminal is preferred:
-ubuntu:~$ gsettings get org.gnome.desktop.default-applications.terminal exec                                                                                                                    
'x-terminal-emulator'

Edit: I just changed it to xterm and was about to say I'm happy with that. but It's hard to copy and paste things to xterm :(

---

### Post by egeezer on 2015-04-12
Try my favorite: the Xfce terminal.  Copy-paste is easy, lot of customizing options.

---

### Post by philip10 on 2015-04-13
I installed and opened xfce terminal
sudo apt-get install xfce4-terminal

xfce4-terminal
Failed to connect to session manager: Failed to connect to the session manager: SESSION_MANAGER environment variable not defined

echo $SESSION_MANAGER
<blankline>

xfce4-terminal still opens up but it suffers from the same problems as x-terminal-emulator

---

### Post by papibe on 2015-04-13
Hi philip10.

Could you open a terminal run these commands, and post back the results (you can copy/paste the text)?
```
ls ~/.bash_logout ~/.bashrc ~/.profile

diff /etc/skel/.bashrc ~/.bashrc

diff /etc/skel/.profile ~/.profile
```
Regards.

---

### Post by philip10 on 2015-04-13
ls ~/.bash_logout ~/.bashrc ~/.profile
```
/home/philip/.bash_logout  /home/philip/.bashrc  /home/philip/.profile
```

diff /etc/skel/.bashrc ~/.bashrc
```
<Nothing>
```

diff /etc/skel/.profile ~/.profile
```
<nothing>
```

---

### Post by philip10 on 2015-04-29
Ok I have almost figured this out.

```
sudo apt-get install rxvt-unicode
export TERM=rxvt-unicode
```

From there on everything works perfectly. My only problem now is that i have to set TERM all the time. How can i set it permanently to rxvt-unicode using either gnome-terminal or xfce4-terminal? ... or any other terminal that supports copy n paste

---

### Post by philip10 on 2015-05-22
Ok completely figured it out now.  
```

sudo apt-get install rxvt-unicode
nano ~/.bashrc
export TERM=rxvt-unicode

```

Now you should be able to run x-terminal-emulator or gnome-terminal-emulator and everything should work fine.

I'm not sure if this is just me but if you press ctrl+alt+T and are confronted with the wrong terminal, just open system settings -> keyboard -> shortcuts -> create a custom shortcut with your preferred terminal on ctrl+alt+t. This will override the system shortcut.

---

