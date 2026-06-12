---
title: "mc4man's 'spread' (window picker for window group) from all workspaces"
date: 2015-04-29
forum: Desktop Environments
---

### Post by rocky-oceans on 2015-04-29
Dear All,

I would like to restore the behavior that mc4man aimed for in this thread:
[http://ubuntuforums.org/showthread.php?t=1921996](http://ubuntuforums.org/showthread.php?t=1921996)

That is to say, I would like to have a command that implements the window picker for window group across all workspaces.

The command mentioned in that thread is the following:

```
[COLOR=#000000][FONT=Ubuntu Mono]dbus-send --print-reply --type=method_call --dest=org.freedesktop.compiz /org/freedesktop/compiz/scale/screen0/initiate_all_key org.freedesktop.compiz.activate string:'root' int32:`xwininfo -root | grep id: | awk '{ print $4 }'` string:"match" string:$(xprop -id `xprop -root | grep "_NET_ACTIVE_WINDOW(WINDOW)" | awk '{print $5}'` | grep "WM_CLASS" | cut -d\" -f4 | awk '{print "class=" $1 }')[/FONT][/COLOR]
```

However, I get the following error:
```
Error org.freedesktop.DBus.Error.ServiceUnknown: The name org.freedesktop.compiz was not provided by any .service files
```

Could someone explain which packages or set up files I need to install to get the above command to work from a fresh Ubuntu 15.04 installation?
Has there since been found a better work around?

---

### Post by mc4man on 2015-04-29
The command is still valid & works fine though it's not meant to be run via a terminal.
There are however 2 issues - 
1. If bound to some keyboard combo then that combo must be executed exactly, otherwise you'll get a spread that cannot be exited from in any manner, only a restart will solve.
2. User set commands in compiz (command plugin) tend to get 'lost' over a short period of time & then require re-setting, a minor pita.

To resolve #2,  since 13.04  I've been integrating the command into compiz with a default keyboard  binding. As it's built/stored in a personal ppa I first used ctrl+alt+p to account for some users possibly  installing the compiz packages. That combo required using 2 hands so less chance to do wrong, like ctrl+p+alt.
Since then I've decided to set as I prefer for single hand operation - ctrl+alt+z 

When a command such as this is   integrated into compiz it must be done via a script (binary), that also allows other means to execute. In other words if the binary is run the all instances of the window group in focus are pulled to a spread.  However again dbus can be wierd so I don't use anything other than the keyboard binding or it seems the binary works ok with an edge binding though technically the dbus command is for 'key'
(and i'm not inclined to integrate a 2nd command specific to edge.

So maybe describe how you are trying to use. The user side method is to use the command in the command plugin & set that command  to a binding. (also you must enable the dbus plugin
 One should note dconf & ccsm are one off, ccsm starts commands on 0, dconf on 1

I do have a 15.04 compiz build in a ppa with this  integrated  (generally for myself as it also includes unity modified for a 1x4 workspaces & some other stuff..)

---

### Post by CantankRus on 2015-04-29
Hi **mc4man**,
just a note for rocky-oceans.
The dbus plugin won't be available in ccsm until you install the unsupported plugins.
```
sudo apt-get install compiz-plugins
```
Lately when changing some settings in ccsm, if unity needs to reload it has been logging me out
so close any other applications when using ccsm.

---

### Post by rocky-oceans on 2015-05-02
Thank you very much for your response mc4man. I really appreciate it. I should say that I have learned so much from your posts over the years.

> **mc4man said:**
> The command is still valid & works fine though it's not meant to be run via a terminal.
There are however 2 issues - 
1. If bound to some keyboard combo then that combo must be executed exactly, otherwise you'll get a spread that cannot be exited from in any manner, only a restart will solve.


What does this mean? I must be misunderstanding something because it seems obvious to me that if I do not execute the shortcut exactly the command bound to the shortcut will not be run.

> **mc4man said:**
> 
2. User set commands in compiz (command plugin) tend to get 'lost' over a short period of time & then require re-setting, a minor pita.

To resolve #2,  since 13.04  I've been integrating the command into compiz with a default keyboard  binding. As it's built/stored in a personal ppa I first used ctrl+alt+p to account for some users possibly  installing the compiz packages. That combo required using 2 hands so less chance to do wrong, like ctrl+p+alt.
Since then I've decided to set as I prefer for single hand operation - ctrl+alt+z 

When a command such as this is   integrated into compiz it must be done via a script (binary), that also allows other means to execute. In other words if the binary is run the all instances of the window group in focus are pulled to a spread.  However again dbus can be wierd so I don't use anything other than the keyboard binding or it seems the binary works ok with an edge binding though technically the dbus command is for 'key'
(and i'm not inclined to integrate a 2nd command specific to edge.

So maybe describe how you are trying to use. The user side method is to use the command in the command plugin & set that command  to a binding. (also you must enable the dbus plugin
 One should note dconf & ccsm are one off, ccsm starts commands on 0, dconf on 1

I do have a 15.04 compiz build in a ppa with this  integrated  (generally for myself as it also includes unity modified for a 1x4 workspaces & some other stuff..)

I tried to implement the shortcut through xbindkeys. It works in the sense that the command is run, but the window spread does not show. I redirect output to a file and looked at it. It says

method return sender=:1.36 -> dest=:1.112 reply_serial=2

which I think means it ran correclty, because that is the same (simpilar based on dest number value) output I get as when I run in the terminal. And actually when I run in the terminal it works (it shows all of my terminal windows).

Any idea on how I can debug this issue further? I would really like to have this feature back.

---

### Post by rocky-oceans on 2015-05-02
> **CantankRus said:**
> Hi **mc4man**,
just a note for rocky-oceans.
The dbus plugin won't be available in ccsm until you install the unsupported plugins.
```
sudo apt-get install compiz-plugins
```
Lately when changing some settings in ccsm, if unity needs to reload it has been logging me out
so close any other applications when using ccsm.

Great, thank you for these instructions! Do you happen to know how I can enable the dbus plugin from the command line?

---

### Post by CantankRus on 2015-05-02
> **rocky-oceans said:**
> Great, thank you for these instructions! Do you happen to know how I can enable the dbus plugin from the command line?

Why?
Are you running Ubuntu/unity?
...and also don't understand why you're using xbindkeys to set the shortcut.

---

### Post by mc4man on 2015-05-02
> **rocky-oceans said:**
> 
What does this mean? I must be misunderstanding something because it seems obvious to me that if I do not execute the shortcut exactly the command bound to the shortcut will not be run.

I don't think that keyboard combos are that 'deterministic' in linux or ubuntu, ex. ctrl+alt+delete produces the same as ctrl+delete+alt, at least when physically done.


> **rocky-oceans said:**
> 
I tried to implement the shortcut through xbindkeys. It works in the sense that the command is run, but the window spread does not show. I redirect output to a file and looked at it. It says

method return sender=:1.36 -> dest=:1.112 reply_serial=2

which I think means it ran correclty, because that is the same (simpilar based on dest number value) output I get as when I run in the terminal. And actually when I run in the terminal it works (it shows all of my terminal windows).

Any idea on how I can debug this issue further? I would really like to have this feature back.

I don't believe it's a matter of debugging, more of just implementing correctly.
The screens should show - 
open ccsm > command plugin > use the dbus command on a command #, set a binding (key & or edge)
or alt - 
make the command a script, (scr.3), put the script in a bin folder in your $PATH & make executable. Then use the scriptname as the command, set a binding(s)

So in screens both examples work

As far as xbindkeys also don't get the use case. If executing it 'steals' focus then that defeats the deal here..
Edit - so for example this would work here but slower/more cumbersome, scr. 4
alt+f2 > xdotool key ctrl+alt+z
alt+f2 > set1

---

### Post by rocky-oceans on 2015-05-02
> **mc4man said:**
> I don't think that keyboard combos are that 'deterministic' in linux or ubuntu, ex. ctrl+alt+delete produces the same as ctrl+delete+alt, at least when physically done.
I don't believe it's a matter of debugging, more of just implementing correctly.
The screens should show - 
open ccsm > command plugin > use the dbus command on a command #, set a binding (key & or edge)
or alt - 
make the command a script, (scr.3), put the script in a bin folder in your $PATH & make executable. Then use the scriptname as the command, set a binding(s)

So in screens both examples work

As far as xbindkeys also don't get the use case. If executing it 'steals' focus then that defeats the deal here..
Edit - so for example this would work here but slower/more cumbersome, scr. 4
alt+f2 > xdotool key ctrl+alt+z
alt+f2 > set1

I got it working thanks to you! I did not know about commands. Actually I've never used CCSM and have only implemented shortcuts in xbindkeys.

I did see an issue where it correctly activated but I could not get out of it. You described this above. I'm not sure how I triggered it or how to fix that. I suppose I need to make sure I run ctrl + alt + p like you say above instead of alt + ctrl + p ? I will experiment.

Thank you so very much for your help on this!

---

### Post by rocky-oceans on 2015-05-02
> **CantankRus said:**
> Why?
Are you running Ubuntu/unity?
...and also don't understand why you're using xbindkeys to set the shortcut.

I do run Ubuntu/unity. I want to configure from command line because I have a script that configures everything for me on a new set up. So it does sudo apt-get install [a bunch of stuff]. It changes gsettings, etc. I would like it to configure this as well.

I used xbindkeys because of ignorance :) I did not realize it was bad to use.

---

### Post by mc4man on 2015-05-02
As mentioned if using a keyboard combo you should/must do exactly, so for ctrl+alt+p **DO make sure p is last.** 
(I believe you could hit alt before ctrl & be ok though better to get used to doing it exactly.

I've become very used to ctrl+alt+z so it's not an issue for me & the advantage is it can be done with 1 hand

If you were to use for instance the bottom right corner as an edge binding then it's somewhat out of the inadvertent way & doesn't suffer from the key binding issue with incorrect order.

The 2nd issue you may come across is the binding may stop working after a period of time if time means reboots. This is some flaw in compiz/unity where settings can be set back to the default which in this case means 'none'
If that happens you'll need to reset in ccsm.

No way around that unless you integrate the command & a binding which is easiest done in the source & a rebuild.
(The logic here is that in this case the command & binding are the default so they can't be 'unset'

---

### Post by rocky-oceans on 2015-05-02
OK thank you very much for all of this useful information.

And again, thank you in general for your presence on ubuntuforums.org. You help so many people (and also people you don't even realize like me who mainly just read your posts without replying).

---

