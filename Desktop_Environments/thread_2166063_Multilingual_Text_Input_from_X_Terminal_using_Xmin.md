---
title: "Multilingual Text Input from X Terminal using Xming"
date: 2013-08-07
forum: Desktop Environments
---

### Post by Richard Wordingham on 2013-08-07
I am trying to use a Windows XP system as a remote X server backup to my Ubuntu desktop machine.  (I sometimes lose physical access to the Ubuntu desktop machine.)  The connection is effected by Wi-Fi (802.11g).  I need to switch input keyboards quite frequently - in particular, I make much use of two Keyman for Linux (KMFL) keyboards via iBus.  I have added an XKB fallback for one of them.  I am using free Xming to make the Windows machine into an X server.  I prefer a rootless multiple window system so that I may readily use the browser natively.

Rebooting the Windows XP system to run Linux is a poor option, as (a) there is usually an inactive user logged into it and (b) its Wi-Fi dongle only works intermittently on Linux, at least for lucid lynx.

When my Ubuntu desktop rand lucid, I got a reasonable system on the X Server as follows:

1. Launch Xming running gnome-terminal with MS Windows providing window management.

2. Execute the following commands from the terminal window executing on Ubuntu and displaying on the remote X server:

gnome-panel&
ibus-daemon -r -d&

I could then choose most applications from the gnome panel, and other programmes could be started from the terminal window.  The gnome-panel was not 'expanded', so normally it did not block the corners of the screen.

The restarting of iBus by ibus-daemon seemed to interfere with any other sessions I was running, but I know of no other way to get the XKB and iBus keyboard controls on the panel (or anywhere else on the X server).  However, my KMFL physical keyboard mapping would not establish itself when selected - the iBus keyboard in use remained unchanged.  The physical keyboard usually works properly on the Ubuntu desk top.  I worked around this by converting it to a mnemonic keyboard for use with a British XKB keyboard mapping, but this solution cannot be shared widely and further complicates maintenance.  (I ought also to provide a US-based mapping.  I already have XKB, KMFL, emacs and MSKLC implementations to keep synchronised, with the MSKLC implementation being the fullest.)

With trepidation I upgraded to precise pangolin (12.04) and the scheme no longer works adequately.  (On precise pangolin, my desktop has always been based on Unity.)

Do I need to download more then gnome-panel via the software centre with recommended extras ticked to add applets to the panel?  The window created by gnome-panel no longer acquires indicators when I run ibus-daemon.

I have tried using 'unity-2d-panel&' instead of 'gnome-panel'.  I have not worked out how to get the XKB indicator into this panel, and I am having to switch XKB keyboards completely blind - switch and then type to see which XKB keyboard I now have.  With lucid I would be told the XKB keyboard if I hovered the mouse over the XKB keyboard indicator.  I cannot find a reliable way of switching iBus-keyboards.  The best I can do is to click on my application, then on the iBus keyboard indicator, select the first keyboard listed, and then click on my application.  I then get an iBus panel which I can usually move to a more visible location.  (The unity-2d panel is half off the top of the screen - I have to recognise the bottoms of the icons.)  Clicking on the name of the keyboard in this panel gives me a choice of keyboards and administrative actions, but I have not worked out how to select from the list.  Double clicking has worked, but rarely.  The only consolation is that this route once got my KMFL keyboard mapping to work, which is an advance on lucid.

How should I be switching keyboards from the remote X server provided by Windows XP?

---

### Post by Richard Wordingham on 2013-08-08
> **Richard Wordingham said:**
> Do I need to download more then gnome-panel via the software centre with recommended extras ticked to add applets to the panel?  The window created by gnome-panel no longer acquires indicators when I run ibus-daemon.
I'm not not sure if it is necessary, but once I'd downloaded gnome-shell I could use alt/right-click to add applets to the panels and move/delete them so they did not interfere with other panels.  (I only wanted a short panel, on the right or the left.)  I added 'indicator applet complete'.  This only shows the ibus-keyboard - it does not show the KBD applet.[/quote] 

> **Richard Wordingham said:**
> I cannot find a reliable way of switching iBus-keyboards.
Setting up a key to move between iBus  keyboards via iBus preferences is a work-around, though it is a poor way of switching when one has many keyboards to choose from.   Also, shift-alt is often not recognised.  To switch an input method off, I have to restart iBus via the command line.

---

