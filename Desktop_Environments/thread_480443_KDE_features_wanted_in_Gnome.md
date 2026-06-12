---
title: "KDE features wanted in Gnome"
date: 2007-06-21
forum: Desktop Environments
---

### Post by jamesrl on 2007-06-21
Instead of the standard KDE vs. Gnome debate, I think I'll list some things that KDE has that would be nice if they could be done in gnome.  I ran Kubuntu for awhile and while I eventually switched back to gnome for a variety of reasons (mainly stability), there are some features I still long for.  

1). Easy switch of power options.  In kubuntu feisty by default on my laptop with two 2Ghz processors, you can easily switch from "Powersave mode" (processors run at 1 GHz), "Dynamic mode" (processors run at speed dependent on load) and "Performance mode" (processors run at 2GHz at all times).  You can also setup how it changes dependent on the power settings (can choose whether which mode to go to when plugged in, or unplugged) and also override those settings temporarily.  I don't see any options of this sort in gnome-power-manager-2.18, which would be nice.  Any suggestions would be nice.

2). Music Equalizer in one of the music applications.  Currently there are many fancy options for music in GNOME (Rhythmbox, Banshee, Exaile, Listen, Quod Libet, etc.) but none of them seem to have an equalizer (and Gnome with ALSA doesn't seem to have a system wide equalizer either).  I know both Amarok and XMMS can be installed with Gnome, but amarok is much better integrated into KDE and uses a lot more resources than the standard ones.  [That is I have a Dell E1505 that has stop/play/pause/next/prev buttons on the front that work well with Rhythmbox by default, but I can't get them to work easily with Amarok.]  

3). Calculator in the Alt-F2 "Run Application" window.  In KDE whenever you type in a math expression such as "(136/5)*3" it recognizes it as not being a command, and in the run application window does the calculation.  I think this is one of my favorite KDE features, as 
whenever I needed a quick calculation, I could quickly pull a calculator up (and not leave multiple windows open for later).  With gcalctool or other calculators, even if I make a keyboard 
shortcut to start them up; it will clutter my desktop/taskbar with too many windows open as I forget to close them.  Run application is nice as you can only have one open, and it always comes to the top.  I've come up with a solution below to do math calculations easily in the terminal.

4) Easier way to set keybindings that consistently work with the "Windows"/Super key.  


Any other KDE features people want in GNOME?



-----
Partial Solutions:

2) I'm using xmms with equalizer, and setup the multimedia keys with gconf-editor.  Type gconf-editor (may have to install) and go to /apps/metacity/keybinding-commands
Edit keys: 
	  command_1 to have "xmms"  to launch xmms
	  command_2 to have "xmms -t" for play/pause
          command_3 to have "xmms -s" for stop
	  command_4 to have "xmms -r" for previous track
	  command_5 to have "xmms -f" for next track
and then edit 
/apps/metacity/global_keybindings
	 run_command_1 to have "0xed"
	 run_command_2 to have "0xa2"
	 run_command_3 to have "0xa4"
	 run_command_4 to have "0x90"
	 run_command_5 to have "0x99"
[These are the bindings that work for Dell E1505.  On different computers, you can see what the keys output by going to the keyboard shortcuts option in the standard  gnome menu.  I also made sure to disable the shortcuts that were already set in Preferences > Keyboard Shortcuts that involved these keys.]

3) This isn't a solution to do calculations from the run applications; but allows you to do 
calculations easily and quickly from the bash terminal.  Edit .bash_aliases or .bashrc in your 
favorite text editor and add this line to the end: 
```

calc () { echo "scale=3; ${*}" | bc ; }

```
Then if you go to the command line and type 
```
calc '19/85' 
```
it sends a command to bc (which may need to be installed) and prints the output in the terminal.  You don't actually need the quotes on the calculation unless you use parentheses or * as bash will interpret these and not pass them correctly to bc.   You could also skip quotes but use \* , \( , and \) instead of *, (, and ).  

You can also shorten the command to change the name in .bashrc from 'calc' to 'c' or even '=' to save keystrokes if you want.   You can also change scale=3 to something different to have a different number of maximum decimal places (you may not want to make it too large as bc will go to the max decimal spaces after every division).  If you call it '=' you still have to be careful to put a space between it and a command like: 
```
= "3 / (5 * 3 + 2)"
```

4) The only way I can do it right now, is go to keyboard preferences: set "Hyper is mapped to the Win-keys" on layout options under Alt/Win behavior, and then go do the same gconf-editor and in the /apps/metacity/ and change the command_# and run_command_# settings as done above for xmms, though the shortcut for run_command isn't "<Super> M" but "<Mod4> M".  

Be careful if you think you can just do it with in Preferences -> Keyboard Shortcuts, as it sometimes works (for example launch terminal with "<Mod4> T" works if you set it there), but shortcuts for "Find Files" with "<Mod4> F" won't work though it would work if you tried "<Ctrl> F").  [And its not the key combination as that combination would work if it was for launch terminal.]

---

### Post by VanHammersly on 2007-06-21
Good observations.

"4) Easier way to set keybindings that consistently work with the "Windows"/Super key. "

I agree with your other points, but I am definitely on board for #4.  I like hot keys and am frustrated by bending the pinky all the way over to ctrl.  I'm so used to Apple Key + whatever.

---

