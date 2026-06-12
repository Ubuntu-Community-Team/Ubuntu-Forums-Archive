---
title: "Emulate Yakuake with gnome-terminal"
date: 2005-12-09
forum: Desktop Environments
---

### Post by runlevel0 on 2005-12-09
There is an easy way to set up gnome-terminal to start in a yakuake-like fashion. 

I got used to yakuake using KDE 3.4.2 on my Gentoo box. It's a very useful app indeed, so I figured out how to get a similar behaviour in Gnome. It's quite simple but I have a final question for the gnome-savvy. But first the explanation.

What I find most useful of Yakuake is that I can start it with a keybinding (F12 indeed comes quite handy) and that it starts on a fixed position. OK, Yakuake does more, like animated scrolling... But I like yakuake because it's darn useful, not because of eyecandy.

So the get these two basic things what we need is to pass the [color=#009900]--geometry[/color] argument to the gnome-terminal and bind it to a key.

Open the [color=#009900]Ubuntu menu > System tools > Config editor > apps > metacity 
[/color]

There are two sections that we are going to use:
[color=#009900] keybindings_commands[/color] and [color=#009900]global_keybindings[/color].

First enter [color=#009900]keybindings_commands[/color] 
highlight the first command you like (i.e. *command_1*), double click and write this command into the *_Value_* field:

```

gnome-terminal --geometry=125x25+0+0

```

That's the custom invocation for gnome-terminals. Now we need to bind this command to a key. Enter [color=#009900]global_keybindings[/color] and select the entry which corresponds to your command, using *command_1* (i.e.) we will need to edit *run_command_1*. Double click and write *F12* into the *_Value*_ field. Once you close the editor you will be able to call gnome-terminal with F12. the terminal will be placed at the top of the screen, have a full screen lenght and is 30% high.

If you want to change this to any value of your choice, start 
the terminal and issue [color=#009900]xwininfo[/color], you will get a crosshair, just click on the terminal and take the last argument (-geometry) as a guide.

NOTE: I am a complete Gnome n00b coming from KDE. I gathered this info from the Ubuntu customization wiki:

[For the xwininfo part](http://doc.gwos.org/index.php/Transparent_Terminals) and
[for the keybindings part](http://doc.gwos.org/index.php/GnomeKeyboardShortcut)

**And now the million-dollar question:**

I have thought on emulating yakuake even further, so that I can close the terminal with the same keystroke (F12).
As I told you, I'm not very Gnome-savvy (bloody n00b indeed), but I think I might need to figure out what PID the terminal I opened has so that I can make a script to invoke when I press F12. The script shall open the terminal if there isn't any running and close it when it's open. 

Is there a way to accomplish this w/o having to write a daemon?

Who can I tell Gnome or Metacity to close or open a particular window from a command line?

Or even better: Where can I find stuff for the fine art of RTFMming ?  ;)

---

### Post by n8bounds on 2008-07-02
aptitude show tilda

works almost exactly like yakuake, and works great in Hardy!

I found your post when searching for it. Cheers!

---

