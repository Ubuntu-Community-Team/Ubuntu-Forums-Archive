---
title: "[SOLVED] copmiz-fusion widget layer launcher"
date: 2008-04-03
forum: Desktop Effects &amp; Customization
---

### Post by nuclearpidgeon on 2008-04-03
Hi

I'm using Compiz-fusion, avant window navigator and Screenlets, and I was wondering if there was any way for me to make a Launcher that virtually pushed F9 (to launch the widget layer), so that I could have a leopard-like dashboard icon?

Thanks in advance

---

### Post by kawaji on 2008-04-04
1. enable  ' Dbus '  plugin on CompizConfig Settings Manager.

2. create a new file and paste the following code to it, and then save as e.g. widget.sh 
```
#!/bin/bash
dbus-send --type=method_call --dest=org.freedesktop.compiz /org/freedesktop/compiz/widget/allscreens/toggle_key org.freedesktop.compiz.activate string:'root' int32:`xwininfo -root | grep id: | awk '{ print $4 }'`
```

3. right-clicking on the file. go to Properties -> Permmisions , check ' Execute ' option.  

4. create a new launcher ( command : /path/to/widget.sh ).

5. click the launcher.

---

### Post by nuclearpidgeon on 2008-04-04
uhh, avant-window-navigator is refusing to accept my .sh file as a launch target.
and also, the script ain't working. I even manually ran the command - the terminal just goes straight back to the prompt.

Could you also make one for a Ctrl+alt+enter command? (that's my expo shortcut)

Thanks

---

### Post by nuclearpidgeon on 2008-04-04
Also, to anyone, surely there's an easier way to do this. I mean, a massively long dbus command is rather inconveniant. perhaps it could be intergrated into a newer ubuntu release... there might even be a script to do it or something...

---

### Post by kawaji on 2008-04-04
Are you sure the backquote character, which is at the end of command line , was not be omitted from the one you copied & pasted ?
Is there dbus-daemon process name on your system-monitor ?

A script file cataining the command line works from a launcher on my AWN.
I just now copied the above code displayed on my Firefox. and ran it on terminal. It also worked like charm.

Anyway, here is a command line for Expo.
```
dbus-send --type=method_call --dest=org.freedesktop.compiz /org/freedesktop/compiz/expo/allscreens/expo_key org.freedesktop.compiz.activate string:'root' int32:`xwininfo -root | grep id: | awk '{ print $4 }'`
```

and it would be better to check for details of Compiz Dbus plugin.
[http://wiki.compiz-fusion.org/Plugins/Dbus](http://wiki.compiz-fusion.org/Plugins/Dbus)

Cheers,

---

### Post by nuclearpidgeon on 2008-04-04
Aha!
Found the problem.
I ran your command with the '--print-reply' command and this showed up:
```

~$ dbus-send --print-reply --type=method_call --dest=org.freedesktop.compiz /org/freedesktop/compiz/expo/allscreens/expo_key org.freedesktop.compiz.activate string:'root' int32:`xwininfo -root | grep id: | awk '{ print $4 }'`
Error org.freedesktop.DBus.Error.UnknownMethod: Method "activate" with signature "si" on interface "org.freedesktop.compiz" doesn't exist


```

---

### Post by kawaji on 2008-04-05
Hi, 
Thanks for your feedback.

Try these commands
for Widget Layer:
```
dbus-send --type=method_call --dest=org.freedesktop.compiz /org/freedesktop/compiz/widget/allscreens/toggle org.freedesktop.compiz.activate string:'root' int32:`xwininfo -root | grep id: | awk '{ print $4 }'`

```

for Expo :
```
dbus-send --type=method_call --dest=org.freedesktop.compiz /org/freedesktop/compiz/expo/allscreens/expo org.freedesktop.compiz.activate string:'root' int32:`xwininfo -root | grep id: | awk '{ print $4 }'`
```

I checked older version sources of those plugins, 

Option names on my compiz are ' toggle_key ' (Widget Layer) & 'expo_key' (Expo).
But I found those were ' toggle' & ' expo ' on the older version of compiz fusion.

---

### Post by nuclearpidgeon on 2008-04-05
HOORAY!!!
It works. Thankyou!
But does this mean that i'm using an old version of compiz-fusion?
I have the latest in the standard ubuntu sources iI believe.
EDIT:
Found out that the latest beta version is on hardy, not gutsy (default)

---

### Post by nuclearpidgeon on 2008-04-06
also, avant window navigator refuses to let me link to the .sh file. Is there any way I can turn it into a.bin file or something like that?

EDIT:
Fixed, but it only lets me put one at a time... very buggy

---

