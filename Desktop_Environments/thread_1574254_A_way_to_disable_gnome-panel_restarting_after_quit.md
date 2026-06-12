---
title: "A way to disable gnome-panel restarting after quitting?"
date: 2010-09-14
forum: Desktop Environments
---

### Post by Gaygerbil on 2010-09-14
I have seen a couple of threads about this, for me I want to close my gnome-panel while voice chatting on Skype and watching streams off Youtube/Hulu or w/e. The videos and voice chat run a lot smoother when I close out of all the applets and gnome-panel running. However the only way I was able to do that was by just deleting the panel, which of course adds the problem of adding it back and then reconfiguring it the way I want.

I noticed if I just kill the panel using killall gnome-panel it'll die and then come back. :| 

I can uncheck it off startup applications and removed it from required components but that doesn't really solve my problem, it won't start that way but if I want it running I have to open a terminal to run it. And if I quit out of that terminal the panel goes with it too. :|

Is there either a way to open the panel without having to leave the terminal open which would be required of me if I'm doing that, or two disable the restart of gnome-panel when I kill it. Either way is perfectly acceptable for me as long as it functions the way I intended it's ok. Thanks! :]

---

### Post by hhh on 2010-09-14
> **Gaygerbil said:**
> open the panel without having to leave the terminal open
Open the Run dialog (Alt+F2) and run gnome-panel

HTH

---

### Post by asmoore82 on 2010-09-14
> **Gaygerbil said:**
> I have seen a couple of threads about this, for me I want to close my gnome-panel while voice chatting on Skype and watching streams off Youtube/Hulu or w/e. The videos and voice chat run a lot smoother when I close out of all the applets and gnome-panel running.
...
Interesting, I've not heard of that before.

Will setting the Panels to "Auto-Hide" have the same effect?

I have this old shell script to toggle this setting from a launcher...

```
[COLOR="Blue"]#!/bin/bash
#HidePanels
#  This file is in the Public Domain.[/COLOR]

count=0

while read line
do
   keys[$((++count))]=[COLOR="Purple"]"${line}/auto_hide"[/COLOR]
done <<EOF
$( gconftool-2 --all-dirs [COLOR="Purple"]"/apps/panel/toplevels"[/COLOR] )
EOF

old=$( gconftool-2 --get ${keys[1]} )

case [COLOR="Purple"]"$old"[/COLOR] in
   [COLOR="Purple"]"0"[/COLOR] | [COLOR="Purple"]"false"[/COLOR] | [COLOR="Purple"]"False"[/COLOR] )
      new=[COLOR="Purple"]"true"[/COLOR]
      ;;
   * )
      new=[COLOR="Purple"]"false"[/COLOR]
      ;;
esac

for key in [COLOR="Purple"]"${keys[@]}"[/COLOR]
do
   gconftool-2 --set [COLOR="Purple"]"$key"[/COLOR] --type bool [COLOR="Purple"]"$new"[/COLOR]
done

[COLOR="Blue"]#End of File[/COLOR]
```

---

### Post by Gaygerbil on 2010-09-15
> **hhh said:**
> Open the Run dialog (Alt+F2) and run gnome-panel

HTH
Yeah should have mentioned this but you can't use the menu (Alt+F1) or the run dialog (Alt+F2) without gnome-panel on.

I really don't think setting the panel as autohide has any effect as the processes are still running and taking up resources. I know this cuz I actually use two panels the bottom one autohides and has Dockbarx on it. If I open up my terminal right now it's still an active process it's not until I quit out of gnome-panel or delete Dockbarx that it goes away as a process.

---

### Post by Gaygerbil on 2010-09-16
Shameless Bump.

---

### Post by nick_goodfate on 2010-09-16
> **Gaygerbil said:**
> Yeah should have mentioned this but you can't use the menu (Alt+F1) or the run dialog (Alt+F2) without gnome-panel on.

You can install Gnome-do or something similar and use it instead of ALT+F2 while your panels are disabled.

---

### Post by hhh on 2010-09-16
> **Gaygerbil said:**
> Yeah should have mentioned this but you can't use the menu (Alt+F1) or the run dialog (Alt+F2) without gnome-panel on.
Sorry, I forgot about that. Have you looked into gmrun?
[http://packages.ubuntu.com/lucid/gmrun](http://packages.ubuntu.com/lucid/gmrun)
[http://wiki.archlinux.org/index.php/Gmrun](http://wiki.archlinux.org/index.php/Gmrun)

---

### Post by Gaygerbil on 2010-09-17
I'm using Kupfer and it works for this pretty well. :]

I decided to go with Kupfer instead of GnomeDo after reading that GnomeDo takes too many resources. This will do just fine. Thannks! Although if anyone actually knows how to prevent gnome-panel from relaunching everytime I kill it that would be appreciated.

---

### Post by Gaygerbil on 2011-01-26
I know this is late, but I figured out a way to do what I intended with a script. 

I assigned the script to launch with a keyboard shortcut, Win + Z and to close with Win + X

It opens up, wallpaper-tray, gnome-panel, and conky and the closes all those when I close it. 

Works well and saves lots of resources (around 40 - 50 mb of RAM and tasks your processor less.)

---

### Post by Copper Bezel on 2011-01-26
Actually, you shouldn't have to have the script edit gconf every time. Just remove the panel as a required session in gconf-editor, then add the panel to your startup applications. Then you can kill and re-run it normally.

Since I don't (ever) use gnome-panel, I installed xfce-utils and bound the Alt+F2 shortcut to xfrun4, the XFCE run dialog, instead. Not having a run dialog, even temporarily, would just kind of suck. = )

---

### Post by Boondoklife on 2011-01-26
if you run it from the terminal
```
gnome-panel &
```then instead of Closing the terminal, type exit. This should leave the panel running.

Synapse is another good launcher app or you could try guake which keeps a hide able terminal available with the press of F12.

---

### Post by Gaygerbil on 2011-01-27
That requires you to leave a terminal open though which is something I didn't want.

---

### Post by Boondoklife on 2011-01-27
The method I gave you does not need the terminal open, which is why you can type exit and the panel will still be running. I just did this on my box, I don't use the panel so perfect situation, and it started the panel and stayed running after I exited the terminal.

---

### Post by Copper Bezel on 2011-01-27
This is a very messy proposition, the way you're handling it. What if the system locks up while you're running without a panel and you have to restart?

---

### Post by Boondoklife on 2011-01-27
Well if the system hard locks, the panel won't make a lick of difference. If X hangs, then you can change to a terminal with ALT+CTRL+F2 and login/reboot.

---

### Post by Copper Bezel on 2011-01-27
I didn't mean *your* method, just the initial idea. But yeah, you're right, it's not really an issue so long as the keybindings for running a terminal or running the panel are there.

---

### Post by Boondoklife on 2011-01-27
No worries! I don't care for the panel myself, I prefer docky. The ALT+F2 for the run box do not work, but the key bindings to switch to a terminal do work.

---

### Post by Gaygerbil on 2011-01-28
Well hitting the power button on my computer just shuts down my computer normally as it would so it's not a big deal. And if it hangs that much where it won't respond to the power button having a panel won't make much of a difference.

Besides it's less likely to hang without the panel being loaded you know?  

But yeah I got Alt + ~ for my terminal as well.

---

