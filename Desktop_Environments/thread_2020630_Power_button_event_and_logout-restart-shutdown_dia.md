---
title: "Power button event and logout-restart-shutdown dialog"
date: 2012-07-08
forum: Desktop Environments
---

### Post by billstei on 2012-07-08
In Ubuntu 12.04 I changed /etc/acpi/events/powerbtn, commenting out the "action" line as follows:

#action=/etc/acpi/powerbtn.sh

I also used dconf-editor to set apps/indicator-session/suppress-logout-restart-shutdown as checked (on).

Then I did:

sudo service acpid restart

And when I press the power button I still get the "Shutdown this system now?" dialog.  In theory this dialog was suppressed, and even if not suppressed, it is supposedly called by the script /etc/acpi/powerbtn.sh via the action line above that is now commented out.

So, from-where/why is this dialog being called?

Edit: Looking at /var/log/syslog I find that commenting out the action of /etc/acpi/events/powerbtn causes the following acpid start error:

acpid: skipping incomplete file /etc/acpi/events/powerbtn

So I changed this to:

action=logger "/etc/acpi/events/powerbtn script: Power button pressed."

And this message is indeed logged when I press the power button.

I also tried doing:

sudo service acpid stop

And leaving it stopped, and still the dialog appears when I press the power button.

---

### Post by billstei on 2012-07-08
In addition to the things disabled as noted in Post #1 above, I also discovered this in gconf-editor:

/apps/gnome-power-manager/buttons/power = suspend

and I changed that to

/apps/gnome-power-manager/buttons/power = nothing

And then to really be sure I uninstalled package gnome-power-manager (along with ubuntu-dekstop).

And still the dialog appears when I push the power button.

---

### Post by billstei on 2012-07-08
I think I found it:

Using dconf-editor:

Set org.gnome.settings-daemon.plugins.power.button-power = nothing

What I find odd is that it was set to "suspend", but what actually happens is not that, but rather the "Shut down this system now?, followed by a 60 second delay and then a shutdown.  If anything this is the "interactive" behavior, which is one of the pop-up menu selections for the button-power variable.

---

### Post by billstei on 2012-07-08
Final test results of gnome-settings-daemon (package ver 3.4.2-0ubuntu0.3) behavior in Ubuntu 12.04:

Note: This is with packages acpid, acpi-support, toshset, powermanagement-interface, and gnome-power-manager uninstalled, and pm-utils, powermgmt-base, and upower installed

org.gnome.settings-daemon.plugins.power.button-power =

1) blank - does nothing (correct?)
2) suspend - dialog, 60 second delay, then shutdown (wrong)
3) shutdown - dialog, 60 second delay, then shutdown (correct)
4) hibernate - does nothing (wrong)
5) interactive - dialog, 60 second delay, then shutdown (wrong? Cancel by default would make more sense)
6) nothing - does nothing (correct)

Regarding acpid, the file /etc/acpi/events/powerbtn sets the action to /etc/acpi/powerbtn.sh, a script which checks for a running gnome-settings-daemon and exits knowing that gnome-settings-daemon is handling the power button event.

There are various workarounds (on the forums, etc) attempting to fix acpi suspend-by-power-button behavior, when in fact the problem seems to be 2) and 4) above.

---

### Post by billstei on 2012-07-09
Continuing my efforts to "fix" this, this thread is worth noting as to how things got to where they are now: [https://bugzilla.gnome.org/show_bug.cgi?id=652183](https://bugzilla.gnome.org/show_bug.cgi?id=652183)

The code that determines what to do in each of the six cases above is in the gnome-settings-daemon source code tree in:

gnome-settings-daemon-3.4.2/plugins/media-keys/gsd-media-keys-manager.c

Line #1645 do_config_power_action()

and confirms that suspend and hibernate, 2) and 4) above both rely on calls to upower via dbus (correct?) as follows for suspend:

g_dbus_proxy_call (manager->priv->upower_proxy, "Suspend", NULL, G_DBUS_CALL_FLAGS_NONE, -1, NULL, upower_sleep_cb, NULL);

and hibernate:

g_dbus_proxy_call (manager->priv->upower_proxy, "Hibernate", NULL, G_DBUS_CALL_FLAGS_NONE, -1, NULL, upower_sleep_cb, NULL);

which would suggest that the bug is somewhere in upower, but note that identical suspend behavior (i.e. the dialog with 60 second timeout and shutdown by default) is also invoked via Line #765 and #776 as follows:

variant = g_dbus_connection_call_sync (manager->priv->connection,
GNOME_SESSION_DBUS_NAME, GNOME_SESSION_DBUS_PATH
GNOME_SESSION_DBUS_INTERFACE, "Shutdown", NULL, NULL,
G_DBUS_CALL_FLAGS_NONE, -1, NULL, &error);

My objective is to (primarily) make the power button do a suspend, and (secondarily) get rid of the 60 second timeout.  Why?  This is for a headless server that uses VNC to view/control the desktop sometimes, and a demanding and impatient non-specific human with a itchy power button finger most of the time.

---

### Post by billstei on 2012-07-09
It occurred to me that if I simply reverse this policy:

acpid - don't handle the power button if gnome-settings-daemon is running
gnome-settings-daemon - handle the power button

to this:

acpid - handle the power button
gnome-settings-daemon - don't handle the power button

I won't get all the quirky conflicts and bugs.  So here is what I now have:

In /etc/acpi/events/powerbtn change action line to:

action=/usr/sbin/pm-suspend

In gconf-editor:

/apps/gnome-power-manager/buttons/power = nothing

In dconf-editor:

apps.indicator-session.suppress-logout-restart-shutdown = unchecked
org.gnome.settings-daemon.plugins.power.button-power = nothing

And then verify:

acpid is installed and running.

Testing:

1) Press power button - immediate suspend, no dialog.  Resume appears normal.
2) Select "Suspend" in Unity Session Indicator/Menu - immediate suspend, no dialog.  Resume appears normal.
3) Select "Shutdown" in Unity Session Indicator/Menu - Shutdown confirmation dialog (without Suspend or Hibernate buttons).
4) Select "Logout..." in Unity Session Indicator/Menu - Logout confirmation dialog.
5) Press power button while suspended - computer resumes

Additional Notes:

In dconf-editor, org.gnome.gnome-session.logout-prompt, whether checked or unchecked has no effect on 4) above, and as such would appear to be another bug.

Don't leave any extra files in /etc/acpi/events (like powerbtn~ for example) as they will get parsed (as I recall) and probably mess things up.

After making changes to /etc/acpi/events files do: sudo service acpid restart
in order for the changes to take effect.

On a headless system this thread may be useful to solve the password on resume issue: [http://ubuntuforums.org/showthread.php?t=1466504](http://ubuntuforums.org/showthread.php?t=1466504)

---

### Post by dvo on 2012-09-01
Thanks a lot billstei for your excellent analysis and for providing solutions!
The logout-restart-shutdown dialog ("Shut down this system now?") was driving me nuts.

Testing this further, I found that for preventing the dialog it suffices to execute
> gsettings set org.gnome.settings-daemon.plugins.power button-power nothing
(that is, apps > indicator-session > suppress-logout-restart-shutdown can be ignored, 
and gconf-editor /apps/gnome-power-manager/buttons/power is not needed).

One should just be reminded after changing /etc/acpi/events/powerbtn to execute
> sudo service acpid restart

---

### Post by ezzy25 on 2012-10-07
I searched for quite a while (with no luck) trying to figure out how to immediately shut down the computer using the power button without bringing up the shutdown dialog box with the 60 second timer.  

The fix was to edit this file:

/etc/apci/powerbtnt.sh

I deleted everything in it (after making a copy of course) except the very last line of code, leaving this: 

/sbin/shutdown -h now "Power button pressed"

Problem solved.  Thanks for all the work billstei and for posting all of the info!

---

### Post by arskipaski on 2012-11-27
Why on earth is this not easily configurable through the system settings in 12.04? It's not like it's some out of this world feature.. Is there a bug report or feature request or something somewhere?

---

