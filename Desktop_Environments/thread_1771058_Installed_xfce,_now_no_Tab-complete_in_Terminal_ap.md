---
title: "Installed xfce, now no Tab-complete in Terminal apps?"
date: 2011-05-30
forum: Desktop Environments
---

### Post by AppleTech on 2011-05-30
Good day!  Just finished setting up my 11.04 home server this week.  Installed GNOME initially and ended up not feeling it (a bit too slow for VNC on my Atom box).

Performed sudo apt-get remove ubuntu-desktop and then installed xfce.

Now, I can't use tab-complete in any Terminal app in xfce when using VNC to access the box.  It still works properly over SSH.  Have ensured that all lines referring to auto-complete are un-commented in the following:

/etc/profile
/etc/bash.bashrc
~/.bashrc

I have verified that bash_completion is installed (reinstalled using Synaptic just to be sure).

It seemed to work intermittently when I changed the above config files but has reverted back to not functioning anymore.  Help!

Thanks!

---

### Post by AppleTech on 2011-05-30
Anyone?  Somewhat at wits-end here!

---

### Post by Toz on 2011-05-30
OK, lets check some settings. When connected through vnc, open up a terminal window and post back the results of the following two commands:```
echo $SHELL
echo $BASH_COMPLETION
```
And can you also post back the contents of your .vnc/xstartup file.

---

### Post by AppleTech on 2011-05-31
> **Toz said:**
> OK, lets check some settings. When connected through vnc, open up a terminal window and post back the results of the following two commands:```
echo $SHELL
echo $BASH_COMPLETION
```And can you also post back the contents of your .vnc/xstartup file.

```
echo $SHELL
/bin/bash
``````
echo $BASH_COMPLETION
/etc/bash_completion
``````
nano .vnc/xstartup

#!/bin/sh

# Uncomment the following two lines for normal desktop:
# unset SESSION_MANAGER
# exec /etc/X11/xinit/xinitrc

[ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
#xsetroot -solid grey
#vncconfig -iconic &
#x-terminal-emulator -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
#x-window-manager &
#exec gnome-session &
startxfce4

```

---

### Post by Toz on 2011-05-31
Two things I would try:

1. In your xstartup file, change the first line to read```
#!/bin/bash
```Save the file, restart the vnc service and try again.

2. If that doesn't work, within the vnc session, at a terminal prompt, re-source the .bashrc file like this:```
. ~/.bashrc
```and try again.

If those don't work, maybe the vnc programs are somehow remapping or blocking the function of the tab key. What server program are you using on the server? And what front-end program are you using and from what type of system (another linux box, windows box, mac, etc)?

---

### Post by AppleTech on 2011-06-03
> **Toz said:**
> Two things I would try:

1. In your xstartup file, change the first line to read```
#!/bin/bash
```Save the file, restart the vnc service and try again.

2. If that doesn't work, within the vnc session, at a terminal prompt, re-source the .bashrc file like this:```
. ~/.bashrc
```and try again.

If those don't work, maybe the vnc programs are somehow remapping or blocking the function of the tab key. What server program are you using on the server? And what front-end program are you using and from what type of system (another linux box, windows box, mac, etc)?

Tried changing first line of .vnc/xstartup: No change.

Tried re-sourcing .bashrc from GUI terminal app: No change

Regarding versions - using vnc4server on 11.04 Server.  Client is Chicken of the VNC on Mac, but this hasn't change.  Issue started when booting xfce from vnc login rather than GNOME. :mad:

---

### Post by Toz on 2011-06-03
Interesting - then it must be xfce. This leads to me think that maybe the last line of your xstartup file might be the culprit - perhaps that is not the correct method for starting xfce in such a scenario. Did some googling and found the following:

```
xfwm4 --display :1.0 &
xfce4-panel --display :1.0 &
xfdesktop --display :1.0 &
```

in lieu of the startxfce4 command.

Note: also found reference to: **xfce4-session** as startup command. Perhaps you can give them a try.
Note2: also found this command: **exec ck-launch-session dbus-launch --exit-with-session startxfce4**

Perhaps you can test them?

---

### Post by Toz on 2011-06-03
Also, what is the contents of /etc/vnc/xstartup? If it exists, it is also being executed in your script.

---

### Post by AppleTech on 2011-06-03
Interestingly that file doesn't exist?

---

### Post by Toz on 2011-06-03
That's fine, its only executed if it exists. I was curious to see if it did exist, what was in there.

---

### Post by billd42 on 2011-07-24
Wow, nobody's come up with an answer to this one?  I'm experiencing this issue too and it's a real head-scratcher.  I've gone ahead and started using Fluxbox instead, I need a lightweight WM.

---

### Post by Toz on 2011-07-24
Try using Ctrl-I instead of tab.

---

### Post by edwinorc on 2011-08-01
I accidentally discovered a fix for this while trying to solve a different problem.

edit
~/.config/xfce4/xfconf/xfce-perchannel-xml/xfce4-keyboard-shortcuts.xml

find the line 

<property name="&lt;Super&gt;Tab" type="string" value="switch_window_key"/>

and change  it to 

<property name="&lt;Super&gt;Tab" type="empty"/>

reboot or whatever and then tab will work properly!

I have no idea why but when using vnc this file seems to override tab's normal behaviour and makes it into a switch window key.

---

### Post by m_gustafsson on 2011-08-12
> **edwinorc said:**
> I accidentally discovered a fix for this while trying to solve a different problem.

edit
~/.config/xfce4/xfconf/xfce-perchannel-xml/xfce4-keyboard-shortcuts.xml

find the line 

<property name="&lt;Super&gt;Tab" type="string" value="switch_window_key"/>

and change  it to 

<property name="&lt;Super&gt;Tab" type="empty"/>

reboot or whatever and then tab will work properly!

I have no idea why but when using vnc this file seems to override tab's normal behaviour and makes it into a switch window key.

Thanks! Saved my day :D

---

### Post by Cloudy Brain on 2011-09-07
Thanks so much edwinorc! That's been annoying me for ages!

---

### Post by martinitime1975 on 2011-11-10
This worked for me on the local desktop, as well as in ssh terminal windows, but when I VNC to the server, the tab key does nothing (no auto complete, or tabbing in a text document).  Alt+tab does switch windows, and ctrl+i will cause auto complete to work, but in VNC the "tab" key doesn't function properly at all.  Why does everything else work but not VNC?

---

### Post by perpetualv on 2012-03-09
Thanks Edwinorc - just tried your solution for my VNC server running on Oneric 64-bit and it worked like a champ.  Don't know how you figured this one out, but glad you did.

regards,
Russ

---

### Post by robmi on 2012-05-04
> **Toz said:**
> Two things I would try:

1. In your xstartup file, change the first line to read```
#!/bin/bash
```Save the file, restart the vnc service and try again.

2. If that doesn't work, within the vnc session, at a terminal prompt, re-source the .bashrc file like this:```
. ~/.bashrc
```and try again.

If those don't work, maybe the vnc programs are somehow remapping or blocking the function of the tab key. What server program are you using on the server? And what front-end program are you using and from what type of system (another linux box, windows box, mac, etc)?

@Toz: nr. 1. did the trick for me. Many thanks

---

### Post by goofrider on 2012-10-23
> **edwinorc said:**
> I accidentally discovered a fix for this while trying to solve a different problem.

edit
~/.config/xfce4/xfconf/xfce-perchannel-xml/xfce4-keyboard-shortcuts.xml

find the line 

<property name="&lt;Super&gt;Tab" type="string" value="switch_window_key"/>

and change  it to 

<property name="&lt;Super&gt;Tab" type="empty"/>

reboot or whatever and then tab will work properly!

I have no idea why but when using vnc this file seems to override tab's normal behaviour and makes it into a switch window key.

This fix works for me. Thanks tons!!!

---

