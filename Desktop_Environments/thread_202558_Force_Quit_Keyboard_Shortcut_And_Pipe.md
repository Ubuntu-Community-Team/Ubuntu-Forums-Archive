---
title: "Force Quit Keyboard Shortcut?? And Pipe?"
date: 2006-06-23
forum: Desktop Environments
---

### Post by Kurt_Alan on 2006-06-23
****[SIZE="5"][/SIZE]

1. Re: freezes, is there a keyboard shortcut for Force Quit?

2. Re: the shell, isn't the vertical line called "a pipe"?  It is not on my keyboard. Is there any extended character for this, or do I have to buy a new keyboard?

---

### Post by trent dillman on 2006-06-23
1. CTRL+ALT+SYSRQ+B   <--- edit: this is for system freezes...but if that happens, try CTRL+ALT+BKSP to restart the graphical system. Otherwise, follow aysiu's advice
2. Um...the pipe on my keyboard is above the backslash. On some keyboards it looks like two vertical dashes, others have a single line.

---

### Post by aysiu on 2006-06-23
You can create a keyboard shortcut for the command ```
xkill
```

---

### Post by Kurt_Alan on 2006-06-26
[QUOTE=aysiu]You can create a keyboard shortcut for the command ```
xkill
```[/QUOTE]

1. Where is "Code" on my menu??

2. Is command xkill the same as Ctrl + Alt + Bcksp??

3. When I go to man xkill it refers to a switch for a button.  What is this? 
A workspace?  

4. Can you give me an example of how I use xkill from the terminal. I do not understand the button reference.

5. And, then, how do I make a keyboard shortcut for the same??

Thank you very much for your help.

---

### Post by Kurt_Alan on 2006-06-26
[QUOTE=trent dillman]1. CTRL+ALT+SYSRQ+B   <--- edit: this is for system freezes...but if that happens, try CTRL+ALT+BKSP to restart the graphical system. Otherwise, follow aysiu's advice

Re: 

CTRL+ALT+SYSRQ+B <--- edit


1. What is SYSRQ?

2. What is:         <--- edit  ??

---

### Post by aysiu on 2006-06-26
[QUOTE=Kurt_Alan]1. Where is "Code" on my menu??[/quote] Well, if you right-click your menu, you should have the option to create new launchers. You can also create keyboard shortcuts for commands. You can also just press Alt-F2 and type the command.

> 
2. Is command xkill the same as Ctrl + Alt + Bcksp?? No. *xkill* turns your mouse into a skull and crossbones. Whatever you click after that will be killed.

Control-Alt-Backspace resets the entire X server and logs you out.

> 
5. And, then, how do I make a keyboard shortcut for the same?? Well, if you're in KDE, the keyboard shortcut already exists. It's Control-Alt-Escape.

If you're in Gnome, press Alt-F2 and type ```
gconf-editor
``` Then go to Apps > Metacity

In Global Keybindings Command_1, type the name of the keyboard shortcut you want.

In Keybinding Commands Command_1, type ```
xkill
```

---

### Post by Kurt_Alan on 2006-06-26
[QUOTE=Kurt_Alan][QUOTE=trent dillman]1. CTRL+ALT+SYSRQ+B   <--- edit: this is for system freezes...but if that happens, try CTRL+ALT+BKSP to restart the graphical system. Otherwise, follow aysiu's advice

Re: 

CTRL+ALT+SYSRQ+B <--- edit


1. What is SYSRQ?

2. What is:         <--- edit  ??[/QUOTE]

---

### Post by aysiu on 2006-06-26
[QUOTE=Kurt_Alan]1. What is SYSRQ?[/QUOTE] It's this.

---

### Post by Kurt_Alan on 2006-06-26
[QUOTE=aysiu]Well, if you right-click your menu, you should have the option to create new launchers. You can also create keyboard shortcuts for commands. You can also just press Alt-F2 and type the command.

 No. *xkill* turns your mouse into a skull and crossbones. Whatever you click after that will be killed.

Control-Alt-Backspace resets the entire X server and logs you out.

 Well, if you're in KDE, the keyboard shortcut already exists. It's Control-Alt-Escape.

If you're in Gnome, press Alt-F2 and type ```
gconf-editor
``` Then go to Apps > Metacity

In Global Keybindings Command_1, type the name of the keyboard shortcut you want.

In Keybinding Commands Command_1, type ```
xkill
```[/QUOTE]
**[SIZE="5"][/SIZE]**

I have tried all above, but I am ending up with problems, confusion, and no results.

1. What I meant by "finding code," was how do I designate "code" on the forum window, not my desktop.  Wherever I hover my mouse cursor I can't find "code."

2. I'm a little confused about what the keyboard shortcut is referencing.  Is it referencing the keyboard command to kill the xserver and log-in again or is it referencing xkill in a terminal that results in mouse's skull and crossbones to kill a frozen app??

3.  Whichever it references, I couldn't make it work.  I did find gconf-editor apps metacity global keybindings BUT I did NOT find Command_1.  

I only found Run_Command_1            I did enter a new value there: my shortcut was 187.   And then I went to Keybinding Commands and did find Command_1 and typed in xkill           My end result: When I hit 187 as my keyboard command, nothing happens.  I'm confused. What did I do wrong and what should I do?

---

### Post by aysiu on 2006-06-26
[QUOTE=Kurt_Alan]
1. What I meant by "finding code," was how do I designate "code" on the forum window, not my desktop.  Wherever I hover my mouse cursor I can't find "code."[/quote] I don't know if there's a button. I just type the tags. [c o d e]xkill[/ c o d e] without the spaces.

> 
2. I'm a little confused about what the keyboard shortcut is referencing.  Is it referencing the keyboard command to kill the xserver and log-in again or is it referencing xkill in a terminal that results in mouse's skull and crossbones to kill a frozen app?? Control-Alt-Backspace is a predefined keyboard shortcut that will reset the X server.

I tried to give you instructions for how to create a keyboard shortcut for *xkill*, though, which is the skull and crossbones.

> 
3.  Whichever it references, I couldn't make it work.  I did find gconf-editor apps metacity global keybindings BUT I did NOT find Command_1.  

I only found Run_Command_1            I did enter a new value there: my shortcut was 187.   And then I went to Keybinding Commands and did find Command_1 and typed in xkill           My end result: When I hit 187 as my keyboard command, nothing happens.  I'm confused. What did I do wrong and what should I do? What's 187? You need to actually type the key combination--something like ```
<Control><Alt>Escape
``` I don't believe it can be a combination of numbers.

---

### Post by Kurt_Alan on 2006-06-26
[QUOTE=Kurt_Alan][QUOTE=Kurt_Alan][/QUOTE]


Good. I found that key.  But what is <---edit?

And just to clarify, what does that keyboard command do?  

What's the difference between that command and:

1. xkill
2. Ctrl + Alt + Bcksp?

---

### Post by aysiu on 2006-06-26
I don't know about the earlier post, but this may help: [quote=from Mandriva's documentation]The Magic ~SysRq Key

This feature allows you to do some basic maintenance tasks even if the rest of the system isn't responding. It is enabled by default on Mandrake Linux. In particular, it allows you to shutdown your system properly, thus avoiding the risk of file system corruption when simply turning the machine off with media still being mounted.

The '~SysRq' sequence involves pressing three keys at once, the left ALT key, the '~SysRq' key (also labeled '~PrtSc' or 'F13') and a letter key:

    * ALT <~SysRq> r , puts the keyboard in 'raw' mode.
      This might be helpful in cases where the graphical interface does not respond to keyboard or mouse commands any more. Having pressed that sequence, press simultaneously. This will try to kill the X server and drops you onto the console (i.e. it's the emergency key combination to switch from runlevel 5 to runlevel 3).
    * ALT <~SysRq> s , attempts to write all unsaved data to disk ('sync' the disk) to prevent file corruption.
    * ALT <~SysRq> e , sends a termination signal to all processes , except for 'init'.
    * ALT <~SysRq> i , sends a kill signal to all processes, except for init, thus terminating all processes which ignored the termination signal.
    * ALT <~SysRq> u , remounts all mounted file systems read-only. This prevents file system corruption.
    * ALT <~SysRq> b , reboots the system. Alternatively, replace the 'b' with an 'o' to turn the machine off.

If you look at this sequence, you see that you are - apart from the first step - actually emulating the 'init' shutdown process. Therefore it is important that you press these sequences in the correct order (e.g. that you 'sync' the drives before remounting them): Raw - Sync - tErm - kIll - Umount - reBoot. A possible mnemonic phrase: 'Raising Skinny Elephants Is Utterly Boring'. Mandrake Linux user Louis suggested this phrase, which is a bit more on topic: 'Remembering the Sequence Entirely Is Useful Buddy'.[/quote] For the record, I've never used any of those keys. *xkill* and Control-Alt-Backspace have worked fine for me.

---

### Post by Kurt_Alan on 2006-06-27
[FONT="Fixedsys"]**[SIZE="5"]:KS [/SIZE]**[/FONT]

I have successfully made a keyboard shortcut for* xkill*
I have also learned about Alt + F2 for Run and also *gconf-editor*
I have also learned keyboard shortcuts for killing the GUI and forcing a re-boot. . .


THANK YOU TRENT AND AYSIU FOR YOUR HELP!



:KS

---

