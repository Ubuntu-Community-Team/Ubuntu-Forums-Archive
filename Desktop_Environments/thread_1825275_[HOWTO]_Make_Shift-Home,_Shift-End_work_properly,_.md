---
title: "[HOWTO] Make Shift-Home, Shift-End work properly, if these keys are on the num pad."
date: 2011-08-15
forum: Desktop Environments
---

### Post by skief on 2011-08-15
Keywords: shift num pad numpad number key home end pgdn pgup page down up highlight edit text


**This HOWTO applies to you if:**
**1.** Your Home, End, PgUp, PgDn keys are on your num pad.
**2.** When you press Shift-Home or Shift-End to try to highlight a line of text, you instead get numbers (like 1 or 7 say).
**3.** You're not happy with this.

There is plenty of information on these forums about xmodmap, and how
to use it to assign whatever symbols you want to the keys on your
keyboard, but I didn't find any existing HOWTOs that addressed this
particular problem.

Buyer beware: If you use my method, you will regain the editing
capability that you want on your numpad, but every time you actually
want to use the numbers on it, you will have to type a command in a
terminal first, to switch back to "numbers mode". Then you will type
another command to switch back to "editing mode".


**0. Primer (skip if you don't care how it works, and just want a fix)**

Each key on your keyboard generates a key scan code when it is
pressed. This number has nothing to do with the symbol that is
printed on top of that key; it only reflects the key's position on
the board.

It is up your software to correctly assign symbols to keys, and by
default it is configured to do this in the standard way.  When you 
are running a desktop environment such as Gnome which uses
X Windowing, the command xmodmap can be used to alter this
configuration. Besides the man page:
```

man xmodmap

```
there is plenty of information here:
[http://cs.gmu.edu/~sean/stuff/n800/keyboard/old.html](http://cs.gmu.edu/~sean/stuff/n800/keyboard/old.html)
and here
[http://tronche.com/gui/x/xlib/input/keyboard-encoding.html](http://tronche.com/gui/x/xlib/input/keyboard-encoding.html)
if you want to know more.


**1. First you have to determine the key scan codes for the keys on your numpad.**

Open a terminal, and issue the command
```

xev

```
This utility prints the contents of X events. A small white window
(whose title bar should say "Event Tester" or something like it)
opens up, and for everything that happens in that window, you will see
a text representation of the event in your terminal.

So with the Event Tester window active, simply type the keys on your
numpad. For each key press, two new paragraphs will appear in your
terminal, describing the KeyPress and KeyRelease events that just
took place. They'll look something like this:
```

KeyPress event, serial 36, synthetic NO, window 0x4400001,
    root 0x114, subw 0x0, time 10981346, (688,244), root:(1351,297),
    state 0x0, keycode 79 (keysym 0xff50, Home), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 36, synthetic NO, window 0x4400001,
    root 0x114, subw 0x0, time 10981479, (688,244), root:(1351,297),
    state 0x0, keycode 79 (keysym 0xff50, Home), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

```
The key scan code you are looking for is immediately after the word
'keycode'. In this example, the keycode is 79.

Write down the keycodes for all the keys on your numpad.


**2. Next we write a file that will be passed to xmodmap.**

Open your favorite text editor, and compose a file like the following
example:
```

keycode 79 = Home NoSymbol
keycode 87 = End NoSymbol
keycode 81 = Prior NoSymbol
keycode 89 = Next NoSymbol
keycode 80 = KP_Up NoSymbol
keycode 83 = KP_Left NoSymbol
keycode 85 = KP_Right NoSymbol
keycode 88 = KP_Down NoSymbol

```

Of course you must use your own keycodes, if they were different than
mine. For example, on my numpad, 'Home' is printed on the 7 key, and
the keycode for this key is 79. The up-arrow is printed on the 8 key,
which has keycode 80.

Save this file in your home directory. I recommend using the file name
```

.xmodmap_navpad

```

Technical point: The "KP_" prefix stands for "Key Pad," which is
another name for what I've been calling the "numpad." On my system,
if I used simply "Up, Left, Right, Down" without the "KP_" prefixes,
then these keys seemed to override the other arrow keys that I have
on my keyboard, making them unusable.

On the other hand, if I put the "KP_" prefix on Home and End, then
these keys became unusable in Emacs. Experiment for yourself, and see
what happens.


**3. Another text file.**

If you want to be able to switch from the "navigation" or
"editing" configuration we've just designed, back to the "number"
configuration, then you need to make another text file, this time
with contents like:
```

keycode 79 = KP_Home KP_7
keycode 87 = KP_End KP_1
keycode 81 = KP_Prior KP_9
keycode 89 = KP_Next KP_3
keycode 80 = KP_Up KP_8
keycode 83 = KP_Left KP_4
keycode 85 = KP_Right KP_6
keycode 88 = KP_Down KP_2

```
(again using your own keycodes) and save it as
```

.xmodmap_numpad

```
again, in your home directory.



**4. Add a line to your .profile in order to load the "navigation pad" configuration each time you login.**

Probably you should create a backup copy of .profile (in your home
directory) before you modify it. (Always a good idea.)

I recommend adding a comment as well, so that you would add the
following two lines to .profile:
```

# set custom keybindings
xmodmap ~/.xmodmap_navpad

```


[B]5. For convenience, add the following commands to your .bash_aliases.
[/B]

Again, this is in your home dirctory (or create the file if it does not already exist):
```

alias numpad='xmodmap ~/.xmodmap_numpad'
alias navpad='xmodmap ~/.xmodmap_navpad'

```
This way, at any time you can use the commands numpad and navpad to
switch you back and forth between the number and navigation
configurations.


[B]6. Save anything you're working on, log out of Gnome, and log back
in.[/B]

The first time you do this, a window may come up asking whether you
really want to load a certain file into xmodmap. Just tell it that
yes, you want to.


That's all folks. Hope it helps. If anyone knows ways to improve this
process, please add your advice to the thread! :)

---

