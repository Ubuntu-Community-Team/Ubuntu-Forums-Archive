---
title: "HOWTO: assigning cool stuff to the windows key"
date: 2006-01-19
forum: Desktop Environments
---

### Post by jezjones on 2006-01-19
Hi everyone.

I am running Breezy on my laptop and i figured out how to do something cool from putting together different info in different threads on this forum, so i thought i would share it.


First I got 3Ddesktop via aptitude.

3Ddesktop is a tool that switches to your other desktops in a really cool looking 3d way. 

Then in order to assign the desktop switching action to my windows key ;-
(i was never one to use it to launch the menu back in the days when i did use windows).
--------------------------------------

First we have to ensure that when you hit the windows key it acts in the way we expect.

From System -> Preferences -> Keyboard
Select "Layout Options"
Expand "Alt/Win key behaviour"
Check "Super is mapped to the Win-Keys (default)"
It may be default behaviour but its what we want so no harm in being sure.

Then from the gnome menu ;-
Applications -> Systems tools -> Configuration Editor

The Configuration Editor is where you can control Gnome. 
I'm not religious about it but i prefer Gnome to KDE, many KDE fans say it is more configurable, which it may be, but that is not to say that you can't configure Gnome to do an awful lot!

It may seem a bit daunting but so long as you dont change things you dont understand, you wont have a problem (google.com/linux is your friend to check stuff !!).

In the configuration editor expand the tree on the left;-

Apps -> Metacity -> global_keybindings

"Metacity is a window manager for GNOME" - from the sourceforge project page for Metacity.
This basically means that it is a part of the whole windowing system that makes your computer point and click instead of a command line only interface.
We're interested in it because it is where we can assign an arbitrary command to a key or key sequence.

In the area on the right there is a list of Name / Value pairs.
The 7th (or similar) one down should be "run_command_1" and be disabled.
There are several other "run_command_n" (n being a number) listed, also disabled.

Highlight "run_command_1" and right click.
Select "Edit Key"
In the value field type "Super_L" which is the windows key.

Now in the tree on the left, select "keybind_commands" which is where we can set what "command_1" is.

Sure enough the first item is "command_1"
Right click on it and choose Edit.
In the value field type "3ddesk" which is the command to run the desktop switcher.
So now Super_L will run command 1, which is 3ddesk, and your desktop switcher will be executed.

Close the configuration editor and hit your windows key.

Use right and left arrows to move through desktops and enter to select.

First time through it may not have an image of the desktop but this is a cache thing that is solved after you have gone into each desktop.
I am sure there is a way to configure that in 3ddesk, that is my next task.

Even if you dont want to use 3ddesk hopefully this has given some people a peek at what you can do with Gnome, you can assign any command to your windows key or even to a key combination.
Be careful not to do anything that may conflict with your normal use unless you mean to! e.g ctrl alt delete


I hope this has helped some other people, comments/corrections welcome!

---

