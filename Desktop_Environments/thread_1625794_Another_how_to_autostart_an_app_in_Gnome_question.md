---
title: "Another how to autostart an app in Gnome question"
date: 2010-11-19
forum: Desktop Environments
---

### Post by ubutu on 2010-11-19
Ok, so before I go off messing with sudo I'll ask.

I installed 'Alarm Clock' from the Software Center and would like to  have said app autostarts. There is an option in Alarm Clock to autostart  with Gnome but that doesn't work so I assume the reason being I'm not  root.

How to autostart Alarm Clock?

Also, in   **System > Preferences > Startup Applications,**  the 'Add' asks for a command. Is this like Windows whereas I simply  point it to the app I want started? I don't even know where apps are  installed. Who said ignorance is bliss?****

---

### Post by tom4everitt on 2010-11-19
The method I would use to autostart the alarm clock is to add it in 

System -> Preferences -> Startup Applications

as you mention. The command you want is the executable file that launches the program. These are generally located in /usr/bin (in some cases /bin or /usr/local/bin or /opt). So the command you want is probably 

```

/usr/bin/alarm-clock

```
but just
```

alarm-clock

```
usually work as well.

If you absolutely cannot find the file/command, you can look in System->Preferences->Main menu, find the program there, click on properties. There you will always find the command.

---

### Post by sisco311 on 2010-11-19
Actually the command is:
```
alarmclock
```

But anyway, go to alarmclock -> Edit -> Preferences and select *Start the program automatically with GNOME*.

Or copy its .desktop file to ~/.config/autostart; in a terminal run:
```

mkdir -p ~/.config/autostart
cp /usr/share/applications/alarm-clock.desktop ~/.config/autostart
```

---

### Post by ubutu on 2010-11-19
Thank you for the replies.

Browsing via System -> Preferences -> Startup Applications Add option, the command is 
/usr/bin/alarmclockLol, my core problem was I didn't know where installed apps were located, else I'd done this already.........

@sisco311
There wasn't a desktop icon and "go to alarmclock -> Edit -> Preferences and select *Start the program automatically with GNOME*." didn't work for me long before I made this post which then had me thinking I need sudo.:grin:

---

