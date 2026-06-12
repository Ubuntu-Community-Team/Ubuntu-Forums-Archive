---
title: "Keyboard shortcuts (keybindings) don't work in Jaunty"
date: 2009-04-24
forum: Desktop Environments
---

### Post by ftmichael on 2009-04-24
I've just upgraded my Ubuntu from 8.10 to 9.04, and now my keyboard shortcuts don't work.  **gconf-editor** says my keybinding settings are still as they were, but since upgrading to Jaunty they just plain don't work. Pressing the correct key combo yields no output.

I've seen a lot of posts from people who had this issue in Intrepid, but no actual fixes.  Plus my keybindings actually worked fine in Intrepid, and have only broken when I upgraded to Jaunty.

---

### Post by vetetix on 2009-04-24
Same problem for me, except that I reinstalled completely my system. In the default gconf tree in jaunty, the entries for the key bindings don't exist, maybe it means that the support have been dropped?

I'm still searching for some way to have my personal key bindings.

Edit: after all, it seems to be working, i don't know what i did to make it work.

---

### Post by jtprince on 2009-04-24
the gconf-editor approach appears to be futile.  You can set custom keyboard shortcuts in "System->Preferences->Keyboard Shortcuts" now (add a custom command and then enter a key combination in the next step).  That's a massive improvement for most users, but I had a script that wrote a bunch of shortcuts using gconftool-2.  How can we script these new-fangled shortcuts?  I have no idea where to look, but I'll fish around in gconf-editor and see what I come up with.

---

### Post by fizikz on 2009-04-25
I have a couple of similar problems since upgrading from 8.10 to 9.04; I found a solution for one, but not the other.

1. I have <Alt>+T as a shortcut to open a terminal (one of the preconfigured shortcuts) but for some reason this doesn't work. So I made a custom shortcut with the same key mapping, and it works. I found a workaround, but didn't really solve it. In the end it works out to the same thing in this case.

2. I use keyboard shortcuts to control amarok (play, pause, skip track, etc), however now the shortcuts only work if amarok's window is open, and it won't if the application is minimized to the system tray. Any ideas?

EDIT: I fixed the second problem too. It turns out the keyboard shortcuts assigned in amarok have changed during the upgrade (amarok was upgraded to amarok 2). I reset my old shortcuts and they work. In fact I find the new amarok more responsive, even if the layout takes some getting used to. So far this upgrade seems to have been almost flawless. Overall I'm liking Jaunty. :)

---

### Post by ftmichael on 2009-04-25
Thanks!  I didn't realise that the Keyboard Shortcuts UI allowed custom shortcuts to be added now.  It's still really annoying that my pre-existing settings in **gconf-editor** suddenly don't work, though.

---

### Post by octopuskevin on 2009-04-25
before this thread gets marked as solved, I'm wondering if anyone else is finding that their keybinding settings done through the "keyboard shortcuts" gui are not saved after a reboot?

For me, the issue is to do with the media keys on my Acer laptop... hmm

---

### Post by vivinc on 2009-04-26
Hi,
i had the same problem and then I just installed ccsm (sudo apt-get install compizconfig-settings-manager) and then enabled the first plugin (than it should be named "Commands" or something like that).

Hope this will help you.

Bye!

---

### Post by daucourt on 2009-04-26
Hi,

With Intrepid (and below) the scripting of keybindings was implemented with something like:

```
gconftool-2 -t str --set /apps/metacity/global_keybindings/run_command_1 "<Control><Alt>b"
gconftool-2 -t str --set /apps/metacity/keybinding_commands/command_1 "gedit --new-document"
```

In Jaunty, I had to change to something like: 

```
gconftool-2 -t str  --set /desktop/gnome/keybindings/custom1/binding "<Control><Alt>b"
gconftool-2 -t str  --set /desktop/gnome/keybindings/custom1/name "GEdit"
gconftool-2 -t str  --set /desktop/gnome/keybindings/custom1/action "gedit --new-document"
```

Take care to increment number of custom1 when creating new keybinding.
This still works after reboot.
You can check that your script work well by launching "gnome-keybinding-properties".

---

### Post by nbtrap on 2009-04-29
> **vivinc said:**
> Hi,
i had the same problem and then I just installed ccsm (sudo apt-get install compizconfig-settings-manager) and then enabled the first plugin (than it should be named "Commands" or something like that).

Hope this will help you.

Bye!

YES! Thank you. Everyone should manage his key-bindings via the "Commands" option in the compizconfig-settings-manager.

---

### Post by fxguenea on 2009-05-03
HI

I'm having the same kind of problem, but in my case, the "screenshot" shortcut (the typical "print screen" keyboard entry) is not working, the default alt+F2 isn't working either (and i suppose they're plenty more...) and if I try to configure them on the System > Preferences > Keyboard Shortcuts app. I get no positive response.

Any ideas?

---

