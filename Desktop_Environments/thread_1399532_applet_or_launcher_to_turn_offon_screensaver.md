---
title: "applet or launcher to turn off/on screensaver"
date: 2010-02-05
forum: Desktop Environments
---

### Post by juanoleso on 2010-02-05
Hi All,

I am looking for an applet or a launcher or a script to turn the gnome screensaver off and on with a click.  The feature I would like, though, would be that the icon changes depending on whether the screensaver is on or off.  I was going to try and build it, but I couldn't figure out how to change the icon picture for a toolbar launcher with a *sh script and I don't really have enough experience programming in gnome with any language...

Thanks in advance for any suggestions

---

### Post by Barriehie on 2010-02-06
You can control the screensaver with **gnome-screensaver-command --[color="red"]*option*[/color]**, where **[color="red"]*option*[/color]** can be one of:
```

       --exit Causes the screensaver to exit gracefully

       -q, --query
              Query the state of the screensaver

       -t, --time
              Query the length of time the screensaver has been active

       -l, --lock
              Tells the running screensaver process to lock the screen immedi-
              ately

       -c, --cycle
              If  the  screensaver  is  active then switch to another graphics
              demo

       -a, --activate
              Turn the screensaver on (blank the screen)

       -d, --deactivate
              If the screensaver is active then deactivate  it  (un-blank  the
              screen)

       -p, --poke
              Poke the running screensaver to simulate user activity

       -i, --inhibit
              Inhibit  the  screensaver  from activating. Command blocks while
              inhibit is active.

       -n, --application-name
              The calling application that is inhibiting the screensaver

       -r, --reason
              The reason for inhibiting the screensaver

       -V, --version
              Version of this application

```

Can't help you with changing the icon regarding the status though.

Barrie

---

### Post by stinkeye on 2010-02-06
> **juanoleso said:**
> Hi All,

I am looking for an applet or a launcher or a script to turn the gnome screensaver off and on with a click.  The feature I would like, though, would be that the icon changes depending on whether the screensaver is on or off.  I was going to try and build it, but I couldn't figure out how to change the icon picture for a toolbar launcher with a *sh script and I don't really have enough experience programming in gnome with any language...

Thanks in advance for any suggestions
This script script will toggle gnome-screensaver on/off and display a message to the notification bubble.
Changing the icon is beyond my knowledge.
```
#!/bin/sh

# click to start, click to stop

if pidof gnome-screensaver | grep [0-9] > /dev/null
then
 exec killall gnome-screensaver &
 notify-send "Screen Saver" "Disabled"
else
 exec gnome-screensaver &
 notify-send "Screen Saver" "Enabled"
fi
```
Save as whatever you like and make executable.
Link to the script in your panel custom application launcher.

---

### Post by juanoleso on 2010-02-09
Thanks both, I think that will work perfectly!

For someone who sees this:

I had to install libnotify1 and libnotify-bin on my debian Lenny box:

```

sudo aptitude install libnotify1 libnotify-bin

```

---

### Post by hariks0 on 2010-02-09
I could not understand why you need the script to STOP the screensaver. I think moving your mouse will instantly stop the screensaver and if you use a password, you cannot disable screensaver without entering it in the first place. In my opinion a custom launcher with command ```
gnome-screensaver-command -a
``` is enough.

---

### Post by juanoleso on 2010-02-09
sometimes we watch movies on hulu and firefox doesn't disable the screensaver.  It isn't much work to go into prefs and change the screensaver, but I thought this little script would be fun to put together.

---

### Post by ChadMMc on 2010-06-04
Actually there is one already in the gnome panel applets (at least on my system).. 

The screensaver inhibit applet .. works fine for me.

---

### Post by jruberto on 2010-11-01
There is also this thing: "Caffeine".  Works!

[http://www.liberiangeek.net/2010/07/temporary-prevent-screensaver-powersaving-mode-ubuntu-10-04-lucid-lynx/](http://www.liberiangeek.net/2010/07/temporary-prevent-screensaver-powersaving-mode-ubuntu-10-04-lucid-lynx/)

---

### Post by henriquemaia on 2010-11-28
> **jruberto said:**
> There is also this thing: "Caffeine".  Works!

[http://www.liberiangeek.net/2010/07/temporary-prevent-screensaver-powersaving-mode-ubuntu-10-04-lucid-lynx/](http://www.liberiangeek.net/2010/07/temporary-prevent-screensaver-powersaving-mode-ubuntu-10-04-lucid-lynx/)

Thanks so much for this. I just looking for something that did this and you pointed me into the right direction.

---

### Post by slate on 2011-06-08
Does not work for me in  Natty Narwhal. Instead:
```

#!/bin/sh

# click to start, click to stop

if gconftool-2 -g /apps/gnome-screensaver/idle_activation_enabled | grep true
then
 gconftool-2 -s /apps/gnome-screensaver/idle_activation_enabled --type=bool false
 notify-send --expire-time=50 "Screen Saver" "Disabled"
else
 gconftool-2 -s /apps/gnome-screensaver/idle_activation_enabled --type=bool true
 notify-send  --expire-time=50 "Screen Saver" "Enabled"
fi

```

---

### Post by Thermostaten on 2012-08-13
Here is how it should be done - the right way *smile*

#!/bin/bash
# Toggle the gnome-screensaver on/off - Keld Norman, Aug 2012
ICON=/where/your/warning/icon/is/placed.png
SUSPENDED="`/usr/bin/pgrep -f 'xdg-screensaver suspend'|wc -l`"
if [ ${SUSPENDED:-0} -eq 0 ]; then
 /usr/bin/xdg-screensaver suspend `/usr/bin/xwininfo -root -children|grep Gnome-screensaver|awk '{print $1}'`
 /usr/bin/notify-send "Screen Saver" "Disabled"
 /usr/bin/zenity --notification --window-icon=${ICON} --text="Your ScreenSaver is disabled" &
else
 /usr/bin/xdg-screensaver resume `/usr/bin/xwininfo -root -children|grep Gnome-screensaver|awk '{print $1}'`
 /usr/bin/pkill -f "Your ScreenSaver is disable[d]"  # Kill the zenity taskbar info icon
 /usr/bin/notify-send "Screen Saver" "Enabled"       # Show a notice that the screensaver now is active
fi

---

