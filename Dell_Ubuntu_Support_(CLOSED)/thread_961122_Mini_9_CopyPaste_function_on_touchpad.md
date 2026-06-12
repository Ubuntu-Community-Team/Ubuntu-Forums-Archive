---
title: "Mini 9 Copy/Paste function on touchpad"
date: 2008-10-28
forum: Dell Ubuntu Support (CLOSED)
---

### Post by abeisgreat on 2008-10-28
this is weird, if i tap the lower part of the scrollwheel thing on the touchpad it copys and if i tap near the top is pastes. how can I disable this?

---

### Post by kumoshk on 2009-07-18
Um, I want to know about this, too. Mine doesn't do that particularly, though—it only pastes when the knuckle of my right thumb accidentally touches the touchpad in the upper-right corner while I'm typing (and it usually pastes into something in a rather destructive manner, which would be dreadful if I used programs that didn't have undo options).

Why can't I seem to replicate this behavior on purpose? How do I stop doing it on accident?

---

### Post by ruf4play on 2009-08-05
The touchpad has a ridiculous paste shortcut in the upper right corner. Since the touchpad blends right into the keyboard, it's easy to hit it inadvertently. You can try the fix here: [http://ubuntuforums.org/showthread.php?t=1119474](http://ubuntuforums.org/showthread.php?t=1119474)

It worked for me, but some have noticed the issue reverting.

---

### Post by ugm6hr on 2009-08-06
Or turn tapping off when using keyboard:

> LAPTOP TOUCHPAD

Using a laptop? If your cursor shoots off all over the place when you type and seemingly clicks on things without your consent, have no fear, you can disable it's click function while typing in a few simple steps. First of all, execute the following command in the terminal:

gksudo gedit /etc/hal/fdi/policy/shmconfig.fdi

Next, copy and paste the following text into the empty document:

```
<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
<device>
<match key="input.x11_driver" string="synaptics">
<merge key="input.x11_options.SHMConfig" type="string">True</merge>
</match>
</device>
</deviceinfo>
```

Ubuntu/Xubuntu Users: Navigate to "System > Preferences > Sessions" ("Applications > Settings > Autostart Applications" in Xubuntu) and click on "Add". Name it something like "Touchpad Syndaemon", the description can be "Disables touchpad while typing", and the all important command you need is "syndaemon -i 1 -d -t -K". For it to take effect, either logout or reboot.

Ref: [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by kumoshk on 2009-08-07
I wish I had a shortcut key for that.

---

### Post by ugm6hr on 2009-08-07
> **kumoshk said:**
> I wish I had a shortcut key for that.

For what?

---

### Post by anjilslaire on 2009-08-07
I simply disabled touchpad tapping by using the GUI:
System>Preferences>Mouse>Touchpad>
Uncheck "Enable mouse clicks with touchpad"

---

### Post by kumoshk on 2009-08-07
> **ugm6hr said:**
> For what?

For disabling the touchpad (or just mouse clicks, for that matter).

I'd rather keep using the pointer capture (never lock your screen while the pointer is locked, though&#8212;there's a nasty bug waiting for you if you do) than go the said GUI route.

A simple keyboard shortcut to toggle it on and off would be great (although I'd love to get the button on my laptop designed for the purpose working&#8212;but not if it involves more than three hundred steps j/k&#8212;if you've ever followed instructions that are supposed to do such and often do something else instead, you may get the joke).

It shouldn't be too hard for someone to make an executable script to turn the thing on and off (making the GUI option they have made should certainly be more difficult). Making a keyboard shortcut to a script is easy enough.

---

### Post by kumoshk on 2009-08-07
> **kumoshk said:**
> It shouldn't be too hard for someone to make an executable script to turn the thing on and off (making the GUI option they have made should certainly be more difficult). Making a keyboard shortcut to a script is easy enough.

After looking into this with a helpful hunch (I figured there had to be an option for this in the gconf-editor, and that there had to be a way to edit the options in the gconf-editor from the command-line), I've discovered that it's actually easy enough that I can do it myself, without too much effort.

Here's the command-line code to turn the touchpad off:

```
gconftool-2 --set "/desktop/gnome/peripherals/mouse/touchpad_enabled" --type boolean false
```

and on

```
gconftool-2 --set "/desktop/gnome/peripherals/mouse/touchpad_enabled" --type boolean true
```

The following code will return the value of this setting:
```
gconftool-2 --get "/desktop/gnome/peripherals/mouse/touchpad_enabled"
```

Now I guess I just need to learn how executable script syntax works and all.

---

### Post by ugm6hr on 2009-08-07
The syndaemon settings I suggested will do all this automatyically.  every time you use the keyboard, tapping will be turned off for a specified time (1 sec in the example given).

Having to manually enable and disable it would be too annoying for me.

---

### Post by kumoshk on 2009-08-07
> **ugm6hr said:**
> The syndaemon settings I suggested will do all this automatyically.  every time you use the keyboard, tapping will be turned off for a specified time (1 sec in the example given).

Having to manually enable and disable it would be too annoying for me.

It's not always while using the keyboard that it's needed, though (i.e. you're sitting there, someone surprises you, and your thumb-knuckle touches the touchpad on accident—or whatever; strange stuff can happen). I can see you're point, though, but a manual keyboard shortcut doesn't bother me, if it works (having to scroll somewhere and click something to disable it, however, is annoying for me, at times). It's a matter of preference, I suppose.

---

### Post by kumoshk on 2009-08-07
> **kumoshk said:**
> Now I guess I just need to learn how executable script syntax works and all.

If anyone's curious, I got a working script file. Now I'm happy. Here's the code to put in the script (on Ubuntu, Jaunty, using Gnome, at least):

```
#!/bin/bash

if [ $(gconftool-2 --get "/desktop/gnome/peripherals/mouse/touchpad_enabled") = true ]; then
	gconftool-2 --set "/desktop/gnome/peripherals/mouse/touchpad_enabled" --type boolean false
else
	gconftool-2 --set "/desktop/gnome/peripherals/mouse/touchpad_enabled" --type boolean true
fi
```

I'm about to explain the details on how to set it up&#8212;so if you already know, feel free to skip the rest.

Name the file whatever you want. Make it executable (right-click on it; go to properties; go to permissions and check 'Allow executing file as program'.

Put the file somewhere in your path (such as ~/bin). If you put it in your home directory's bin folder, if you had to make it because it wasn't there, then you might have to restart your computer afterward before it will be in your path.

Then make the shortcut. Go to System --> Preferences --> Keyboard Shortcuts. Click on add. Choose a name. Put the name of the file for the script under Command. Click Apply. Then click on it in the shortcuts window. Under the Shortcut tab it will say 'New shortcut...'; press the key combination you desire (e.g. ctrl alt k). Then pressing that should toggle the touchpad completely off and on.

Anyway, enjoy.

---

