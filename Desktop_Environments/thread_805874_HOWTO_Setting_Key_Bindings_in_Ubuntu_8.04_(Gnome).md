---
title: "HOWTO: Setting Key Bindings in Ubuntu 8.04 (Gnome)"
date: 2008-05-24
forum: Desktop Environments
---

### Post by leetone on 2008-05-24
So I'm sure everyone has tried to key custom key bindings in GNOME only to find that - shock/horror - the GNOME key binding GUI is weak.

For more configurability look at this method I used for getting Amarok to start on Ctrl+Alt+a.

Firstly call up a terminal and enter:

**gconf-editor**

This will bring the central config tool for GNOME; here you can access all of your settings. We are interested in the following entries.

[b]/->apps->metacity->global_keybindings

/->apps->metacity->keybinding_commands[/b]

When you click on global_keybindings you should see entries along the line of

**run_command_x disabled**

Where x is a number between 1 and 12 (it can go upto 32 according the the manual but defaults to 12).

In keybinding_commands you should see entries like

**command_x**

Where x is the same number as for run_command.

In order to set a keybinding you simply enter the key combination in place of disabled in run_command-x, then enter the command to launch in the blank field for the respective command_x entry.


**run_command_x**

For this all meta keys are enclosed in <> as follows.

**<Control> <Alt> <Shift> <Super> (win key)**

Letters are simply lowercased entries. Direction arrows start with a capital letter such as

Up Down


We are interested in setting Ctrl+Alt+a for Amarok's shortcut keyc so we need to enter this after run_command_1 (or whichever one is free)

<Control><Alt>a


Ensure the value is entered by clicking a different entry (if you don't, the command may disappear as you change to keybinding_commands)


command_x

Here I had some problems. For whatever reason entering the same command as Amarok uses from a launcher (amarok %U) doesn't work properly. The program starts but doesn't load the last playlist opened like it normally does. No matter - we will force it to open it by saving the playlist, then directly calling the list in the command. This still doesn't call the last used list but it's better than having to mess around in a GUI every time you want to run your player. For the moment assume I saved the playlist as playlist.m3u and your user name is foo.

The command we enter into the blank field is

amarok /home/foo/.kde/share/apps/amarok/playlists/playlist.m3u


This will make the program run correctly.

I'm not sure if this problem is unique to Amarok or is a general GNOME problem. Anyway if you do have a problem with another program you can now try something along this line.


The Moment of Truth

Having done that, close the configuration editor (it will save all the altered values automatically). Then press your designated key combination (Ctrl+Alt+a in the example). If all is set up properly you should see Amarok (or whatever app you tried) starting. If not check again in gconf-editor to see if you have used the same value for x in both entries; also check that you haven't made any errors in either the key combination or the command itself.

---

### Post by K.Mandla on 2008-05-29
Moved to Desktop Environments.

---

### Post by JohanSwe on 2008-09-13
Thanks leetone,

this was just what I was looking for. Wanted a keybinding for starting Terminal and it works!

---

### Post by JohanSwe on 2008-09-13
I just found out that it's possible to set up keybindings in compizconfig manager under General options/Commands.. :)

---

