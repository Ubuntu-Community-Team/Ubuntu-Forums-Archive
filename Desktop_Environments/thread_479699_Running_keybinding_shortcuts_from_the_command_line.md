---
title: "Running keybinding shortcuts from the command line in gnome"
date: 2007-06-20
forum: Desktop Environments
---

### Post by paradoxxical on 2007-06-20
I am trying to utilize the Super_L  (left windows key) in my keybinding shortcuts in Feisty - Gnome.

Currently I'm using this method:

<http://ubuntu.wordpress.com/2006/01/30/defining-keyboard-shortcuts-for-commands/>
"
1) Run gconf-editor
2) Find Apps -> Metacity -> Keybinding Commands
3) Click on command_1 -or any empty one upto- command_12
4) In “value” type the command you want to run
5) Move upto “global_keybindings”
6) Click on “run_command_x (x corresponds to the value at 3)
7) Type in a key or combination, eg:
Super_L = Left Win key
Super_R = Right Win key
"

In my case Super_L = <mod4>.
This method has worked great for the commands:
gnome-screensaver-command --lock                   locking the screen
gnome-terminal                                                         opening a knew terminal

My QUESTION is, what are the command lines for:

1) Show Desktop
2) Open a new /home window

I've searched a lot and have not been able to find how to run these from the terminal anywhere... any help would be GREAT

---

