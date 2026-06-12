---
title: "How to get original shortcut hotkey setting back?"
date: 2014-03-18
forum: Desktop Environments
---

### Post by A Traveller on 2014-03-18
Hi all.

(Ubuntu 10.04 LTS)

System - Preferences - Keyboard Shortcuts

I tried setting the 'Play (or play/pause)' shortcut from XF86AudioPlay to Ctrl + Alt + A. It didn't work, so how do I reset it to what it was (XF86AudioPlay)?

I'm trying to get the product in the link below to play and pause my VLC but do not want to mess anything up as the hotkeys buttons bring up the black login prompt screen which I don't know how to get out of and have to restart my pc.

[http://www.tianyou123.com/upload/20110215/20110215143252917.jpg](http://www.tianyou123.com/upload/20110215/20110215143252917.jpg)

Any help would be appreciated.

Thanks.

---

### Post by grumblebum2 on 2014-03-19
[s]Try this terminal command[/s].....
```
gsettings reset org.gnome.settings-daemon.plugins.media-keys play
```

[s]You could also use **d**conf-editor and drill down to the **org.gnome.settings-daemon.plugins.media-keys **location.[/s]

[SIZE=3][COLOR=#ff0000]EDIT[/COLOR][/SIZE]: Just noticed your still using 10.04.
Not sure but think you may have to use **g**conf-editor.
Can't remember where you'll find the key. 
Just do a search in gconf-editor for "XF86Audio".

---

### Post by A Traveller on 2014-03-19
Thanks grumblebum2. Your advice worked!

The setting now appears as it was before, but what does it mean though? What will I be now able to do again? Which Play/Pause is it referring to and which keys/buttons control it?

I have lots more questions about getting the remote control to work but will create another thread for that.

---

### Post by grumblebum2 on 2014-03-19
Have a look at this thread. [http://ubuntuforums.org/showthread.php?t=1542751](http://ubuntuforums.org/showthread.php?t=1542751)
I was able to disable the media keys and then set them as global shortcuts in vlc.
The shortcut keys will work even when vlc is not in focus.
May need to log out/in before change takes affect.
[ATTACH=CONFIG]251281[/ATTACH]

You might find a use for this command as well.
You will need to install wmctrl.
It will launch vlc or bring it in to focus if already running.
```
wmctrl -a vlc || vlc
```

I set my media key eject button to run the wmctrl command.
When adding to keyboard  shortcuts, use....
```
sh -c "wmctrl -a vlc || vlc"
```
[ATTACH=CONFIG]251282[/ATTACH]

---

### Post by A Traveller on 2014-03-21
Thanks again, grumblebum2.

I have tried assigning a function to one of the remote control keys by adding the key combination to the global hotkeys in VLC without disabling any media keys and it has worked but there is a problem. I think the problem could be solved without disabling any media keys.

I think I know what needs to be done but don't know how to do it. I'll try to explain.

The remote control has four buttons (A, B, C, and D) that can be used at hotkeys. The remote control is factory-programmed so that pressing button A on it does whatever pressing Ctrl+Alt+A or Ctrl+Alt+1 or Ctrl+Alt+F1 on the keyboard does. I have done some research and have learnt that the shortcut for bringing up the blank tty screen is Ctrl+Alt+F1 so this is why the tty screen comes up when I press button A on the keyboard. I have assigned the Ctrl+Alt+A keys to the global settings in VLC for 'mute'. Now when I press button A on the remote control, it does mute VLC, however, it also goes to the tty screen at the same time, so does anyone know how I can disable the Ctrl+Alt+F1 shortcut for bringing up the tty screen?

I need to know how to disable the following shortcuts currently assigned by Ubuntu as default.

Ctrl+Alt+A
Ctrl+Alt+1
Ctrl+Alt+F1
Ctrl+Alt+B
Ctrl+Alt+2
Ctrl+Alt+F2
Ctrl+Alt+C
Ctrl+Alt+3
Ctrl+Alt+F3
Ctrl+Alt+D
Ctrl+Alt+4
Ctrl+Alt+F4

Does anyone know what any of these shortcuts do, if they are safe to disable, how I could access the things they were used to access another way and how I could re-instate them if necessary? The only relevant item in Keyboard Shortcuts was Ctrl+Alt+D (Hide all normal windows and set focus to the desktop).

Thanks.

---

