---
title: "Switching between basic and international keymaps"
date: 2005-12-12
forum: General Help
---

### Post by WebDrake on 2005-12-12
Hello all,

Much to my delight, with the "regional settings" part of the KDE System Settings, it's relatively easy to select the keyboard map.  However, one thing I can't work out how to do...

... Is there a simple and easy way to set up the option to switch between basic and international variants of a keyboard layout?  Preferably a keyboard shortcut, but if not, by a quick right-click and select option from the system tray.  (As it is I can right-click on the little flag that indicates the keyboard layout, and quickly get into the configuration; but that takes a little more time than I'd like. ;-) )

Many thanks,

          -- Joe

---

### Post by WebDrake on 2005-12-12
Okie, I found out how to do it; though this solution is for GNOME not KDE.

Go to System -> Preferences -> Keyboard.  Click on the Layouts tab.  Add two keyboards, one basic, one international.  Then go to Layout Options and click on "Group Shift/Lock Behaviour", where you can set a key combination to switch between the two options.

It's probably a good idea to set up one of the options to use an LED to signify when you are using a particular keyboard layout. :-D

---

### Post by quasar on 2006-01-18
I've got a pretty nice solution for this problem! 

This is a KDE solution. It assumes a 104-key US Keyboard, and implements quick switching between the basic and intl variants.

It also assumes that setxkbmap works on your computer. If it doesn't, you're gonna have to look for the solution to that in another posting.

Basically, I associate hotkeys with little scripts that change the keyboard variant.

1) Go to System Settings -> Regional and Accessibility -> KHotKeys

2) You Might want to create a new group, click the "New Group" button at the bottom, name it "Joe's Hotkeys" or whatever.

3) Create a new hotkey with "New Action". Now select the newly created action.

4) go to the General Tab, name the Action "English Keyboard" or whatever.

5) Go to the Keyboard Shortcut tab, press the little button that says "None". A dialog will pop up, click the key combo you'd like for switching to the basic variant of your US keyboard.

6) go to the command settings tab, and in the textbox there type 

      setxkbmap -model pc104 -layout us -variant basic

7) repeat the process for switching to the intl variant, changing the names accordingly, finding a *different* key combination, and in the textbox at the end type

      setxkbmap -model pc104 -layout us -variant alt-intl


That's it! now when you click you hotkeys you should see the keyboard change variants silently and without fuss.

           QUASAR

---

### Post by WebDrake on 2006-01-28
Gosh!  That *is* a neat trick.  Thanks very much for that one!

Incidentally, you can first of all get the full command for whatever keyboard layout you want to select, via the keyboard layout tool, so there's no need to rely on -model pc104. :-)

---

### Post by grendel_khan on 2006-02-09
How do I get two variants of the same keyboard in KDE? I can only add one instance of the us keyboard in Keyboard Layout; it disappears from the list on the left side of the control panel once I add it. How can I add two so that I can make one basic and one intl? I currently have it kludged to use one us layout (intl) and one gb layout (basic), but this is ridiculous.

I can definitely add two us keyboards in Gnome; does this need to be bug-reported? To Ubuntu or to KDE?

---

