---
title: "Another alternative to btnx"
date: 2008-12-02
forum: Desktop Environments
---

### Post by nicholas.alipaz on 2008-12-02
[SIZE="5"]Introduction[/SIZE]

I have read probably every thread on mouseclicking setup on these forums and elsewhere.  I have an mx revolution and getting all the buttons to do what I need is of course difficult in the latest ubuntu 8.10.

I tried out a number of different solutions, many of which would work but would be slow/unresponsive at times.  Or sometimes they would just be inaccurate.

In the end I used the following, which seems quick and smooth, as one would expect mouseclicks to be:

[SIZE="5"]Tutorial[/SIZE]

[SIZE="4"]Requirements[/SIZE]
[LIST]
[*]xbindkeys
[*]xautomation
[*]xev
[/LIST]
All of which may be obtained through synaptic

[SIZE="4"]Discovering your buttons[/SIZE]

First off you want to find what your mouseclicks actually do.  Open a terminal and type 
```
xev
```
now start clicking inside the box that popped up.  You will see statements like 
> ButtonRelease event, serial 31, synthetic NO, window 0x4000001,
    root 0x8b, subw 0x0, time 4542727, (45,140), root:(719,191),
    state 0x100, **button 1**, same_screen YES

Where "button 1" is the click you used on your mouse.

Record these somewhere for reference, like gedit.  Here are mine on my mx revolution connected via bluetooth.
```
# Mappings for keys for MX Revo
# b:1		left mouse button
# b:2		left and right mouse button together
# b:3 		right mouse button
# b:4		mouse wheel up
# b:5		mouse wheel down
# b:6		mouse wheel tilt left
# b:7		mouse wheel tilt right
# b:8		back button
# b:9		forward button
# b:10		-none-
# b:11		-none-
# b:12		-none-
# b:13		media wheel up
# b:14		-none-
# b:15		media wheel down
# b:16		media wheel press
# b:17		-none-
# c:0xE1	Search Button
```
*This is only for your reference, don't assume it will be the same on your mouse*

[SIZE="4"]Adding Commands[/SIZE]

Now using this information.  We are going to put all alterations to mouseclicking behaviour in our xbindkeysrc file:
```
gedit ~/.xbindkeysrc
```

All our commands are going to use xautomation to perform them.  Here is an example
```
# Change mouse wheel tilt right to do Ctrl+Alt+Shift+Down
"/usr/bin/xte 'keydown Alt_L' 'keydown Control_L' 'keydown Shift_L' 'key Down' 'keyup Shift_L' 'keyup Control_L' 'keyup Alt_L' &"
m:0x0 + b:7 
```

One more, more simple example:
```
# Change mouse wheel tilt right to do Alt+Down
"/usr/bin/xte 'keydown Alt_L' 'key Down' 'keyup Alt_L' &"
m:0x0 + b:7 
```

Add what you need then save and close.

Run these two commands to test your configuration:
```
killall xbindkeys
xbindkeys
```

Then start clicking and see if it works

[SIZE="4"]Persisting across restarts[/SIZE]

To keep this configuration after restarting, it is necessary to add xbindkeys to your startup applications.

Go to System -> Preferences -> Sessions, then click add (new application).  Type in 'xbindkeys' (without quotes) for the command and fill in the rest as you deem appropriate.

[SIZE="4"]xautomation Documentation[/SIZE]

Now here is what I was able to find for xautomation's documentation.  This took quite a bit of hunting:
```
Commands:
  key k          Press and release key k
  keydown k      Press key k down
  keyup k        Release key k
  str string     Do a bunch of key X events for each char in string
  mouseclick i   Click mouse button i
  mousemove x y  Move mouse to screen position x,y
  mousermove x y Move mouse relative from current location by x,y
  mousedown i    Press mouse button i down
  mouseup i      Release mouse button i
  sleep x        Sleep x seconds
  usleep x       uSleep x microseconds
Some useful keys (case sensitive)
  Home
  Left
  Up
  Right
  Down
  Page_Up
  Page_Down
  End
  Return
  Backspace
  Tab
  Escape
  Delete
  Shift_L
  Shift_R
  Control_L
  Control_R
  Meta_L
  Meta_R
  Alt_L
  Alt_R
```

Happy clicking!

[SIZE="4"]My xbindxrc file[/SIZE]

Here are the things I added to my file:
```
# I have the list of my mouseclick here (the one I posted above)

# Change search button to do button 2 left/right together (or middle click)
"/usr/bin/xte 'mouseclick 2' &"
c:0xE1

# Change tilt wheel right to do Ctrl+Alt+Shift+Down
"/usr/bin/xte 'keydown Alt_L' 'keydown Control_L' 'keydown Shift_L' 'key Down' 'keyup Shift_L' 'keyup Control_L' 'keyup Alt_L' &"
m:0x0 + b:7 

# Change tilt wheel left to do Ctrl+Alt+Shift+Up
"/usr/bin/xte 'keydown Alt_L' 'keydown Control_L' 'keydown Shift_L' 'key Up' 'keyup Shift_L' 'keyup Control_L' 'keyup Alt_L' &"
m:0x0 + b:6
```

I didn't specify anything else, since firefox already seems to pick up my back and forward buttons.

Additionally, I have configured a few of my buttons from within compiz configuration, by adding 'Button13' and so on.  If the button isn't in the drop down, just click edit then type in manually.

---

### Post by Tosho on 2012-06-02
# Change mouse wheel tilt right to do Alt+Down
"/usr/bin/xte 'keydown Alt_L' 'keydown Left' 'keyup Alt_L' 'keyup Left' &"
m:0x0 + b:6

# Change mouse wheel tilt right to do Alt+Down
"/usr/bin/xte 'keydown Alt_L' 'keydown Right' 'keyup Alt_L' 'keyup Right' &"
m:0x0 + b:7

it does work but so do the HUD, when I hit left/right I do go 
back/forward but it activates the  HUD. 

any solution for that ?

---

### Post by nicholas.alipaz on 2012-10-15
> **Tosho said:**
> # Change mouse wheel tilt right to do Alt+Down
"/usr/bin/xte 'keydown Alt_L' 'keydown Left' 'keyup Alt_L' 'keyup Left' &"
m:0x0 + b:6

# Change mouse wheel tilt right to do Alt+Down
"/usr/bin/xte 'keydown Alt_L' 'keydown Right' 'keyup Alt_L' 'keyup Right' &"
m:0x0 + b:7

it does work but so do the HUD, when I hit left/right I do go 
back/forward but it activates the  HUD. 

any solution for that ?

If the mouse key or that key combo is bound by something else on your system already then there will be an attempt to run both commands.  You will need to unbind the key from wherever that is defined would be my guess.

---

