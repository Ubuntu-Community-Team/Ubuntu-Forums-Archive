---
title: "[Utility Announcement] XToggle : easily hide/restore your applications (using hotkey)"
date: 2009-04-10
forum: Desktop Environments
---

### Post by acquiesce1968 on 2009-04-10
Hello everyone,

I wrote a small utility to hide/restore any window using regular expression.
It might be useful to some of you!

Download Link:
[http://www.quotersoftware.com/xtoggle/xtoggle-0.1.2.tar.gz](http://www.quotersoftware.com/xtoggle/xtoggle-0.1.2.tar.gz)


XToggle v0.1.2
-----------------------------

XToggle is a simple command line tool for listing all the top level
windows you have within your X session, and allows you to hide/restore
or close windows by regular expression.


Motivation
-----------------------------

Wouldn't it be nice to be able to hide/restore all your emesene / Pidgin conversation windows with one hotkey ? 
Or to temporally hide AWN because it is covering the status bar of your web browser ?

I searched for some kind of "magical" utility to do this. Never found it.
So I wrote xtoggle ;-)

Please note that xtoggle is derived from another cool utility called xclose written by 'steve'. 
You can find the original xclose here: [www.steve.org.uk/Software](www.steve.org.uk/Software)
Thanks 'steve'!


Building
-----------------------------

This application only requires the xlib and glib header files and libraries. 
It should build under any environment under which X itself is supported.


Usage
-----------------------------

xtoggle [--list OR --close OR --restore-all OR NOTHING (to toggle visibility)] [exact OR NOTHING (for using regexp)] [--lookup_name AND/OR --lookup_class AND/OR --lookup_title OR NOTHING (for lookup_title only)] expression

--list ..................... List matching windows, don't do anything.
--close .................. Force to close matching windows.
--exact .................. Force xtoggle to perform exact matching.
--restore-all .......... Restore all windows previously hidden by xtoggle.
--lookup_name ..... Perform matching using the window name.
--lookup_class ...... Perform matching using the window class.
--lookup_title ........ Perform matching using the window title (default).
--help .................... Shows this usage information.
--debug ................ Shows debug info.
--version ............... Shows the version number of xtoggle.


Examples
-----------------------------

Toggle 'Avant Window Navigator' visibility:
patrick@acquiesce:~$ xtoggle --lookup_class Awn

Toggle 'emesene' visibility (including conversation windows):
patrick@acquiesce:~$ xtoggle --exact --lookup_class --lookup_title emesene

Toggle 'emesene' visibility (buddylist only):
patrick@acquiesce:~$ xtoggle --exact emesene

Toggle 'emesene' visibility (conversation windows only):
patrick@acquiesce:~$ xtoggle --lookup_class emesene

Toggle 'Pidgin' visibility (including conversation windows):
patrick@acquiesce:~$ xtoggle --lookup_class Pidgin

Toggle 'Audacious' visibility:
patrick@acquiesce:~$ xtoggle --lookup_class Audacious

For a trial run you may use the '--list' argument along with a regular
expression. This will display the windows which match, for example:

patrick@acquiesce:~$ xtoggle --list awn

Application Name - Application Class - Window Title
====================================
awn - Awn - awn
awn - Awn - awn
awn - Awn - awn_elements
-----------------------------------------------------------

Note: 'xtoggle --list' will list all top level windows.


Install
-----------------------------

Open a terminal window, go to the directory containing this file and type this command:

sudo make xtoggle install

Note: If you have this error: "xtoggle.c:23:29: error: X11/Xmu/WinUtil.h: No such file or directory", you will need to install "libxmu-dev" from Synaptic.


Desktop Integration
-----------------------------

You can easily integrate xtoggle with your desktop by mapping a hotkey with the appropriate xtoggle command.
For example, you can use Compiz 'command' module to map the 'ctrl+alt+H' hotkey with the 'xtoggle --lookup_class Awn' command.
Each time you press 'ctrl+alt+H' this will hide/restore your AWN dock.


Comments
-----------------------------

Comments or feedback and/or generous donation for my wedding may be sent to the author 
at the address listed at the bottom of this text, where they will be gratefully received.


Patrick DesRosiers
---
[email]acquiesce1968@gmail.com[/email]

---

### Post by jalvareze on 2009-05-20
Thanks for this little tool. I googled a while to find something similar, and at least I found it. Works great. Congratulations

---

