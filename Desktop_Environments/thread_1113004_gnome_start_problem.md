---
title: "gnome start problem"
date: 2009-04-01
forum: Desktop Environments
---

### Post by nmakry on 2009-04-01
I have ubuntu 8.10 on a sony vaio laptop. Yesterday, after an update, when the system restarted it didn't start gnome and remained at the character login screen on tty01. After some trials, I switch the runlevel to 5, using telinit 5 and managed to start gnome automatically on system start. But, the touchpad was not responding, making the gnome environment unusable.

I went to tty02 and login and then type startx. The gnome restarted and the touchpad was fine, but it was not possible to shutdown or restart the system from gnome. I had to go to tty02 terminal and shutdown or restart the system. Also, after system restart, the gnome started automatically, but the touchpad remained unusable, required the same procedure with startx from tty02.

Thank you in advance for any help to restore the system.

---

### Post by sukhhari on 2009-04-01
May be you need to fix some damage packages

While booting select with recovery mode and select damaged packages to fix the problems.

---

### Post by nmakry on 2009-04-01
> **sukhhari said:**
> May be you need to fix some damage packages

While booting select with recovery mode and select damaged packages to fix the problems.

I already did that. No change.

Thanks anyway.

---

### Post by Giblet5 on 2009-04-01
First, you need to determine what is failing.

Boot to the text console and log in.

Run:
sudo /etc/init.d/gdm restart

Does the session start as you expect it to?

If so, you need to figure out why gdm isn't starting during a boot. Perhaps you installed kdm, or some other display manager, and the startup scripts are looking for something that isn't there.

If not, then verify that the Xorg server can start. Run the "X" command to start an empty Xorg session. Ctrl-Alt-Backspace to quit.

You created this state of things by customizing your system w/o knowledge of what those customizations would do. That's fine, and we've all done it, but you'll fix it faster and learn more if you take some initiative and figure out what you did that broke the install.

Logs. Check them.

Get creative: add debugging statements to the startup scripts, or add a 'set -v' at the top...

Start with /etc/rc2.d/S30gdm (if the gdm restart command worked), or /var/logs/Xorg0.log otherwise.

---

### Post by nmakry on 2009-04-01
> **Giblet5 said:**
> First, you need to determine what is failing.

Boot to the text console and log in.

Run:
sudo /etc/init.d/gdm restart

Does the session start as you expect it to?

If so, you need to figure out why gdm isn't starting during a boot. Perhaps you installed kdm, or some other display manager, and the startup scripts are looking for something that isn't there.

Logs. Check them.

Get creative: add debugging statements to the startup scripts, or add a 'set -v' at the top...

Start with /etc/rc2.d/S30gdm (if the gdm restart command worked), or /var/logs/Xorg0.log otherwise.

gdm restart started the session as expected. But, it doesn't fix the problem, as after system restart mouse is freeze again.

The problem appeared when I updated the system from another account using the KDE. I didn't make any changes manually on the system. Just a couple of updates (not many), as I update the system often.

Can anyone help me to setup correctly the startup scripts for gnome?

Anyway thank you very much for your help so far.

---

### Post by Giblet5 on 2009-04-01
> **nmakry said:**
> gdm restart started the session as expected. But, it doesn't fix the problem, as after system restart mouse is freeze again.

The problem appeared when I updated the system from another account using the KDE. I didn't make any changes manually on the system. Just a couple of updates (not many), as I update the system often.

Can anyone help me to setup correctly the startup scripts for gnome?

Anyway thank you very much for your help so far.


You've already identified most of the problem...

Try:
sudo dpkg-reconfigure gdm

You may also need to do:
sudo dpkg-reconfigure kdm

and make sure you select the same manager for each.

The kdm manager installs whenever you install kde-desktop. The kdm install doesn't always work as well as one might think. The reconfigure will likely fix it.

---

### Post by nmakry on 2009-04-01
> **Giblet5 said:**
> You've already identified most of the problem...

Try:
sudo dpkg-reconfigure gdm

You may also need to do:
sudo dpkg-reconfigure kdm

and make sure you select the same manager for each.

The kdm manager installs whenever you install kde-desktop. The kdm install doesn't always work as well as one might think. The reconfigure will likely fix it.

I did both reconfigures, selecting gdm as default manager on both. But after restarting, again the touchpad pointer is freeze!

Any other thoughts?

---

### Post by Giblet5 on 2009-04-01
> **nmakry said:**
> I did both reconfigures, selecting gdm as default manager on both. But after restarting, again the touchpad pointer is freeze!

Any other thoughts?

Well, we're close...

Try JUST the one for gdm. (since kdm probably broke the install in the first place)

Make sure that /etc/X11/default-display-manager contains only one line:
/usr/sbin/gdm

You'll notice that the display manager start/stop scripts both reference this file to determine which manager is default.

---

### Post by Giblet5 on 2009-04-01
ALSO: Did you tweak your xorg.conf?

---

### Post by nmakry on 2009-04-02
I will check /etc/X11/default-display-manager and I will do only the gdm.

Also, I didn't change manually xorg.conf

The strange thing is that the mouse (touchpad) pointer is freeze only after system start. When I type startx from a tty, the desktop starts fine and the mouse pointer is fine.

Something at system start is not starting correctly, while startx operates fine.

Is it something at synaptics driver / settings to check?

---

### Post by Giblet5 on 2009-04-02
> **nmakry said:**
> I will check /etc/X11/default-display-manager and I will do only the gdm.

Also, I didn't change manually xorg.conf

The strange thing is that the mouse (touchpad) pointer is freeze only after system start. When I type startx from a tty, the desktop starts fine and the mouse pointer is fine.

Something at system start is not starting correctly, while startx operates fine.

Is it something at synaptics driver / settings to check?


I think the touchpad controller drivers are all wrapped in the Xorg EV input driver now (someone correct me if this is not so).

I'm running intrepid on a Gateway p-7811fx that's modded all to heck and back. It has the Synaptic touchpad controller with the scroll area on one side. It's quite new (April '08?), yet I've had no trouble at all.

Do you have any USB hubs hanging off your system? Hubs that are underpowered can often drag the +5VDC below TTL logic levels and cause all kinds of trouble: missing keyboard, missing mouse/touchpad/trackpoint, intermittent failure to post, fires, plagues, stale pastries, etc.

Are you patched to-date? EV-input was updated a month back, I think, even on Dapper.

Since it works when gdm correctly starts a session (/etc/init.d/gdm restart), I'm inclined to think we're looking at either a gdm startup problem, or a gdm startup *timing* problem.

If you get a gdm login screen at boot, but the touchpad is unresponsive, it might be interesting to add a "sleep 5" as the second line of the /etc/init.d/gdm script...just to alter the timing and see if changes anything.

---

### Post by nmakry on 2009-04-02
Well, more information, but no fix yet.

I had my system to login automatically to a user. I change that to display the login screen (gdmgreeter). The interesting thing is that on that screen, not only the mouse pointer, BUT ALSO the keyboard is inactive! I can only use ctrl-alt-f2 to go to another tty.

I also changed the default display manager to kdm. The same: Keyboard and mouse not responding without restarting dm manually!

If I try to put manually the command "/etc/init.d/gdm restart" to a startup script, in order to try a temporary solution, what would be the best position?

---

### Post by Giblet5 on 2009-04-02
> **nmakry said:**
> If I try to put manually the command "/etc/init.d/gdm restart" to a startup script, in order to try a temporary solution, what would be the best position?


I'd add the following to /etc/rc.local just before the exit 0 at the bottom.

```
nohup (sleep 10 ; /etc/init.d/gdm restart)&
```

Maybe play with that 10 second delay to suit what works and your caffeine level...

You MAY want to see what happens if you just force the X server to restart...

When you're at the boot login greeter and the keyboard is unresponsive, try Ctrl-Alt-Backspace and see if it all works when the greeter comes back.

I'll bet you're logging interesting errors in /var/log/Xorg0.log when these devices fail to initialize...

---

### Post by nmakry on 2009-04-03
Finally solved by altering the priority of gdm to 30.

I did that by linking /etc/init.d/gdm with /etc/rc2.d/S30gdm and removing /etc/rc2.d/S20gdm

Is this the right way?

The altering of gdm priority, will have other side effects on the system?

Giblet5 proposed to use S30gdm from the start, but I didn't know how.

I believe that was a timing problem,. between HAL and gdm start.

Now, the problem I face is that on firefox, the back / forward buttons are always grayed and the address bar does not change while I am visiting various pages. I tried to reinstall firefox but it didn't fix it.

---

