---
title: "amarok: add new shortcut?"
date: 2006-09-05
forum: Desktop Environments
---

### Post by RikoW on 2006-09-05
Hi,

this is not really an Ubuntu specific question, but maybe someone knows the answer:

I would like to assign a shortcut to the function "Append to Playlist".
I'm running amarok 1.4.1 and "Append to Playlist" is not available in the "Configure Shortcuts" or "Configure global shortcuts" sections under tools.

I guess, the question is really generic. How to define shortcuts to commands not available in the short cut menu?

Thanks and cheers,

             Riko

---

### Post by alphahun on 2007-10-09
GNOME - HOWTO : Create Custom Keyboard Shortcuts

The goal of this small HOWTO is to create a custom keyboard shortcut to run a piece of software (like xmms, 3ddesk, etc..) or whatever command line you want (xkill, transset 0.5, ...).

For this example we want to start xkill (graphical kill) using the "Alt + a" shortcut.

1. Go to System Tools -> Configuration Editor.

2. Go to apps -> metacity -> keybinding_commands, and now choose a command, for this example we will choose command_1. Edit command_1 writing xkill in order to run xkill (or every command you want to launch like in a terminal).

3. In the same directory go to global_keybindings. Edit command_1 (or the command you choose in part 1) with the wanted shortcut like this : <Alt>a

enjoy....

---

### Post by RikoW on 2007-10-10
Hi,

thanks for the reply, but that was nt actually what I was asking about :(

I wanted to know, how to define a shortcut key inside the amarok application ...

Cheers,

                Riko

---

### Post by zeeple on 2008-04-16
> **alphahun said:**
> GNOME - HOWTO : Create Custom Keyboard Shortcuts
3. In the same directory go to global_keybindings. Edit command_1 (or the command you choose in part 1) with the wanted shortcut like this : <Alt>a

What is the syntax for adding Alt+ Super L?  

In my set up I am trying to configure Super L to launch a gnome terminal with profile1, and Alt + Super L to launch a gnome-terminal with profile2.

---

