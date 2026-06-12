---
title: "Scale for menu and title bars setting resets when TV is turned off and on"
date: 2017-04-13
forum: Desktop Environments
---

### Post by ytyLa9z2ru on 2017-04-13
I'm running Ubuntu 17.04 on an Intel NUC i3 7100U Kaby Lake connected to a Samsung 55" UHD TV. I've changed the resolution to 3840 x 2160 and set the "Scale for menu and title bars" to 1.75. Apart for some minor scaling issues with some applications everything worked just fine for some time. But since about a week ago the scaling factor resets to 1 if I turn the TV off and on again. 

The following can be seen in the syslog if I turn the TV off and on:

```
Apr 13 19:29:20 nuc console-kit-daemon[3891]: console-kit-daemon[3891]: GLib-CRITICAL: Source ID 20 was not found when attempting to remove it
Apr 13 19:29:20 nuc console-kit-daemon[3891]: GLib-CRITICAL: Source ID 20 was not found when attempting to remove it
Apr 13 19:29:20 nuc systemd[1]: Stopping User Manager for UID 0...
Apr 13 19:29:20 nuc systemd[7005]: Stopped target Default.
Apr 13 19:29:20 nuc systemd[7005]: Stopped Run Click user-level hooks.
Apr 13 19:29:20 nuc systemd[7005]: Stopping D-Bus User Message Bus...
Apr 13 19:29:20 nuc systemd[7005]: Stopped D-Bus User Message Bus.
Apr 13 19:29:20 nuc systemd[7005]: Stopped target Basic System.
Apr 13 19:29:20 nuc systemd[7005]: Stopped target Timers.
Apr 13 19:29:20 nuc systemd[7005]: Stopped target Paths.
Apr 13 19:29:20 nuc systemd[7005]: Stopped target Sockets.
Apr 13 19:29:20 nuc systemd[7005]: Closed D-Bus User Message Bus Socket.
Apr 13 19:29:20 nuc systemd[7005]: Reached target Shutdown.
Apr 13 19:29:20 nuc systemd[7005]: Starting Exit the Session...
Apr 13 19:29:20 nuc systemd[7005]: Received SIGRTMIN+24 from PID 7103 (kill).
Apr 13 19:29:20 nuc systemd[1]: Stopped User Manager for UID 0.
Apr 13 19:29:20 nuc systemd[1]: Removed slice User Slice of root.
Apr 13 19:29:30 nuc compiz[2405]: WARN  2017-04-13 19:29:30 unity.screen UScreen.cpp:131 UScreen::GetMonitorName: Failed to get monitor name for monitor0
Apr 13 19:29:30 nuc compiz[2405]: WARN  2017-04-13 19:29:30 unity.screen UScreen.cpp:131 UScreen::GetMonitorName: Failed to get monitor name for monitor0
Apr 13 19:29:30 nuc gnome-terminal-[6740]: Allocating size to GtkBox 0x555b92376880 without calling gtk_widget_get_preferred_width/height(). How does the code know the size to allocate?
Apr 13 19:29:30 nuc gnome-terminal-[6740]: message repeated 2 times: [ Allocating size to GtkBox 0x555b92376880 without calling gtk_widget_get_preferred_width/height(). How does the code know the size to allocate?]
Apr 13 19:29:30 nuc unity-settings-[2219]: Failed to load PNP ids: Failed to open file &#8220;/usr/share/hwdata/pnp.ids&#8221;: No such file or directory
Apr 13 19:29:30 nuc unity-settings-[2219]: message repeated 2 times: [ Failed to load PNP ids: Failed to open file &#8220;/usr/share/hwdata/pnp.ids&#8221;: No such file or directory]
Apr 13 19:29:31 nuc colord[1780]: failed to get session [pid 2219]: No such device or address
Apr 13 19:29:31 nuc unity-settings-[2219]: Failed to load PNP ids: Failed to open file &#8220;/usr/share/hwdata/pnp.ids&#8221;: No such file or directory
Apr 13 19:29:31 nuc unity-settings-[2219]: Failed to load PNP ids: Failed to open file &#8220;/usr/share/hwdata/pnp.ids&#8221;: No such file or directory
Apr 13 19:29:36 nuc compiz[2405]: WARN  2017-04-13 19:29:36 unity.screen UScreen.cpp:131 UScreen::GetMonitorName: Failed to get monitor name for monitor0
Apr 13 19:29:36 nuc compiz[2405]: WARN  2017-04-13 19:29:36 unity.screen UScreen.cpp:131 UScreen::GetMonitorName: Failed to get monitor name for monitor0
Apr 13 19:29:37 nuc unity-settings-[2219]: Failed to load PNP ids: Failed to open file &#8220;/usr/share/hwdata/pnp.ids&#8221;: No such file or directory
Apr 13 19:29:37 nuc unity-settings-[2219]: message repeated 2 times: [ Failed to load PNP ids: Failed to open file &#8220;/usr/share/hwdata/pnp.ids&#8221;: No such file or directory]
Apr 13 19:29:37 nuc colord[1780]: failed to get session [pid 2219]: No such device or address
Apr 13 19:29:37 nuc unity-settings-[2219]: Failed to load PNP ids: Failed to open file &#8220;/usr/share/hwdata/pnp.ids&#8221;: No such file or directory
Apr 13 19:29:37 nuc unity-settings-[2219]: Failed to load PNP ids: Failed to open file &#8220;/usr/share/hwdata/pnp.ids&#8221;: No such file or directory
Apr 13 19:29:51 nuc unity-control-c[7130]: Failed to load PNP ids: Failed to open file &#8220;/usr/share/hwdata/pnp.ids&#8221;: No such file or directory
Apr 13 19:29:51 nuc hud-service[2636]: #033[31mvoid DBusMenuImporter::slotGetLayoutFinished(QDBusPendingCallWatcher*)#033[0m: "No such interface 'com.canonical.dbusmenu' on object at path /org/ayatana/bamf/window/52428821"
Apr 13 19:29:51 nuc unity-control-c[7130]: State 0 for FooScrollArea 0x56095d9fa6d0 doesn't match state 128 set via gtk_style_context_set_state ()

```

Any ideas on what's wrong or what I should look at to investigate further?

---

### Post by zasran on 2017-04-22
I have the same problem since I updated to 17.04, also see the same message in logs when I turn of monitor and turn it back on:

```
Apr 21 22:57:42 jojda indicator-session-service[2928]: **
Apr 21 22:57:42 jojda indicator-session-service[2928]: display-cc-panel:ERROR:cc-rr-labeler.c:199:make_palette: assertion failed: (labeler->priv->num_outputs > 0)
Apr 21 22:57:42 jojda compiz[3094]: WARN  2017-04-21 22:57:42 unity.screen UScreen.cpp:131 UScreen::GetMonitorName: Failed to get monitor name for monitor0
Apr 21 22:57:42 jojda compiz[3094]: WARN  2017-04-21 22:57:42 unity.screen UScreen.cpp:131 UScreen::GetMonitorName: Failed to get monitor name for monitor0
Apr 21 22:57:43 jojda gnome-terminal-[4432]: Allocating size to GtkBox 0x5623cfccb8a0 without calling gtk_widget_get_preferred_width/height(). How does the code know the size to allocate?
Apr 21 22:57:43 jojda systemd[2595]: Starting Notification regarding a crash report...
Apr 21 22:57:43 jojda systemd[2595]: Started Notification regarding a crash report.
```

Did you figure out anything? Anybody else has any ideas how to troubleshoot? (this post was the only relevant search result I've found so far)


TIA,
        erik

---

### Post by ytyLa9z2ru on 2017-04-23
> **zasran said:**
> [...]
Did you figure out anything? Anybody else has any ideas how to troubleshoot? (this post was the only relevant search result I've found so far)

TIA,
        erik

Unfortunately I haven't been able to solve the problem or figure out what's going on. So it would be great if someone could give input on how to proceed to try to solve this issue or find a workaround. 

Or if this is something that should be reported as a bug, and if so, where.

---

### Post by tubaguy50035 on 2017-06-10
Also running in to the same problem.  I don't think it being a TV has anything to do with it, I think scaling on any display is being reset when the displays are turned off.  Super annoying.

---

### Post by ersin-the-ertan on 2017-07-05
I can confirm, the monitor need not be a Tv, this is also happening when my 4k computer monitor via display port, goes to sleep for energy saver and re-wakes(the computer is not sleeping, just the monitor). Any previously set scale will revert to the default of one, however when the system restarts, the scale will be what the last applied setting was.

See the bug here [https://bugs.launchpad.net/ubuntu/+source/unity-settings-daemon/+bug/1689356](https://bugs.launchpad.net/ubuntu/+source/unity-settings-daemon/+bug/1689356)

Login, and click on the "Does this bug affect you?" text to up vote.

---

### Post by witti-v on 2017-09-01
For me it was solved by installing a missing package - see below.

After freshly installing Ubuntu a week ago I had a similar problem: My 27' screen only worked ~1 out of 5 times.
I had a look into the syslog and saw the same error as OP: 
Failed to load PNP ids: Failed to open file “/usr/share/hwdata/pnp.ids”: No such file or directory

Not even this file but the whole hwdata directory was missing.
When googling to download the file I found out that it's part of a package called hwdata.

So what helped in my case was simple:
```
sudo apt-get install hwdata
``` and the a reboot.

Hopefully this will save someone some time...

---

### Post by ytyLa9z2ru on 2017-12-05
The problem is solved in Ubuntu 17.10.

---

### Post by amk1543 on 2018-01-03
I am still running into a similar issue on 17.10 (using Unity). Scaling for the only attached monitor resets to 1 every time I turn it off and on.
I am seeing the following error as well:
```
Jan  3 15:59:51 amakhlin-pc compiz[3004]: WARN  2018-01-03 15:59:51 unity.screen UScreen.cpp:131 UScreen::GetMonitorName: Failed to get monitor name for monitor0
```
Curiously, I did not have the problem on 17.04.

---

