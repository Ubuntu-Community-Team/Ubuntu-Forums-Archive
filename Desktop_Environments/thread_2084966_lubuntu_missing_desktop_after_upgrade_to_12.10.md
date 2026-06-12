---
title: "lubuntu missing desktop after upgrade to 12.10"
date: 2012-11-17
forum: Desktop Environments
---

### Post by DuckHook on 2012-11-17
After upgrading Lubuntu from 12.04 to 12.10, lubuntu-desktop fails to load. In particular, lxession dies with the  following errors to run.log:

```
** Message: utils.vala:79: Config system location : /etc/xdg/xdg-LXDE/lxsession/LXDE
** Message: utils.vala:79: Config system location : /etc/xdg/lxsession/LXDE
** Message: utils.vala:85: System system path location : /etc/xdg/lxsession/LXDE/desktop.conf
** Message: utils.vala:89: Final file used : /etc/xdg/lxsession/LXDE/desktop.conf
** Message: utils.vala:79: Config system location : /etc/xdg/xdg-LXDE/lxsession/LXDE
** Message: utils.vala:79: Config system location : /etc/xdg/lxsession/LXDE
** Message: utils.vala:85: System system path location : /etc/xdg/lxsession/LXDE/desktop.conf
** Message: utils.vala:89: Final file used : /etc/xdg/lxsession/LXDE/desktop.conf
** Message: settings.vala:252: Key file does not have key 'window_manager/program'
** Message: settings.vala:261: Key file does not have key 'window_manager/session'
** Message: settings.vala:270: Key file does not have key 'window_manager/extras'
** Message: settings.vala:291: Key file does not have key 'panel/program'
** Message: settings.vala:301: Key file does not have key 'screensaver/program'
** Message: settings.vala:311: Key file does not have key 'power-manager/program'
** Message: settings.vala:341: Key file does not have key 'file-manager/program'
** Message: settings.vala:351: Key file does not have key 'polkit'
** Message: settings.vala:361: Key file does not have key 'network_gui'
** Message: settings.vala:371: Key file does not have key 'audio_manager'
** Message: settings.vala:381: Key file does not have key 'quit_manager'
** Message: settings.vala:391: Key file does not have key 'workspace_manager'
** Message: settings.vala:401: Key file does not have key 'launcher_manager'
** Message: settings.vala:411: Key file does not have key 'terminal_manager'
** Message: settings.vala:421: Key file does not have key 'clipboard'
** Message: settings.vala:431: Key file does not have key 'disable_autostart'
** Message: settings.vala:441: Key file does not have group 'State'
** Message: settings.vala:451: Key file does not have group 'Dbus'
** Message: settings.vala:460: Key file does not have group 'Dbus'
** Message: settings.vala:506: Key file does not have group 'Keymap'
** Message: settings.vala:527: Key file does not have group 'XRandr'

** (lxsession:2219): WARNING **: settings.vala:537: Key file does not have group 'Security'

** (lxsession:2219): WARNING **: settings.vala:611: Key file does not have key 'iXft/Hinting'

** (lxsession:2219): WARNING **: settings.vala:619: Key file does not have key 'sXft/HintStyle'

** (lxsession:2219): WARNING **: settings.vala:627: Key file does not have key 'sXft/RGBA'

** (lxsession:2219): WARNING **: settings.vala:635: Key file does not have key 'sGtk/ColorScheme'

** (lxsession:2219): WARNING **: settings.vala:643: Key file does not have key 'sGtk/CursorThemeName'

** (lxsession:2219): WARNING **: settings.vala:651: Key file does not have key 'iGtk/ToolbarIconSize'

** (lxsession:2219): WARNING **: settings.vala:659: Key file does not have key 'iNet/EnableEventSounds'

** (lxsession:2219): WARNING **: settings.vala:667: Key file does not have key 'iNet/EnableInputFeedbackSounds'

** (lxsession:2219): WARNING **: settings.vala:719: Key file does not have key 'Beep'
** Message: settings.vala:185: Monitoring: /etc/xdg/lxsession/LXDE/desktop.conf
** Message: settings.vala:193: Desktop file is not in config home, monitoring creation of it
** Message: settings.vala:208: Monitoring home path: /home/user/.config/lxsession/LXDE/desktop.conf
** Message: options.vala:154: Create build-in Clipboard
** Message: utils.vala:79: Config system location : /etc/xdg/xdg-LXDE/lxsession/LXDE
** Message: utils.vala:79: Config system location : /etc/xdg/lxsession/LXDE
** Message: utils.vala:85: System system path location : /etc/xdg/lxsession/LXDE/conffiles.conf
** Message: utils.vala:89: Final file used : /etc/xdg/lxsession/LXDE/conffiles.conf
** Message: utils.vala:79: Config system location : /etc/xdg/xdg-LXDE/lxsession/LXDE
** Message: utils.vala:79: Config system location : /etc/xdg/lxsession/LXDE
** Message: utils.vala:85: System system path location : /etc/xdg/lxsession/LXDE/desktop.conf
** Message: utils.vala:89: Final file used : /etc/xdg/lxsession/LXDE/desktop.conf
** Message: app.vala:59: Launching openbox-lxde (null) (null)
** Message: utils.vala:79: Config system location : /etc/xdg/xdg-LXDE/lxsession/LXDE
** Message: utils.vala:79: Config system location : /etc/xdg/lxsession/LXDE
** Message: utils.vala:85: System system path location : /etc/xdg/lxsession/LXDE/autostart
** Message: utils.vala:89: Final file used : /etc/xdg/lxsession/LXDE/autostart
** Message: autostart.vala:44: Autostart path : /etc/xdg/lxsession/LXDE/autostart
** Message: app.vala:59: Launching xscreensaver -no-splash (null)
** Message: app.vala:59: Launching lxpanel --profile LXDE
** Message: app.vala:59: Launching pcmanfm --desktop --profile
** Message: app.vala:59: Launching /usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1 (null) (null)
** Message: options.vala:37: Options - Launch command (null)

(lxsession:2219): GLib-CRITICAL **: g_spawn_command_line_async: assertion `command_line != NULL' failed
** Message: main.vala:263: Check keymap_mode (null)

(polkit-gnome-authentication-agent-1:2278): GLib-CRITICAL **: g_variant_new_string: assertion `string != NULL' failed

(polkit-gnome-authentication-agent-1:2278): polkit-gnome-1-WARNING **: Failed to register client: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files
Openbox-Message: Requested key "XF86Terminal" does not exist on the display
** Message: applet now removed from the notification area
** Message: using fallback from indicator to GtkStatusIcon
** Message: applet now embedded in the notification area
Failed to open VDPAU backend libvdpau_r200.so: cannot open shared object file: No such file or directory
Failed to open VDPAU backend libvdpau_r200.so: cannot open shared object file: No such file or directory
Failed to open VDPAU backend libvdpau_r200.so: cannot open shared object file: No such file or directory
[2417:2512:661332518:ERROR:download_updates_command.cc(130)] PostClientToServerMessage() failed during GetUpdates
Failed to open VDPAU backend libvdpau_r200.so: cannot open shared object file: No such file or directory
[2417:2417:802307357:ERROR:gtk_plugin_container_manager.cc(133)] Request for widget host for unknown window id 35651944
Failed to open VDPAU backend libvdpau_r200.so: cannot open shared object file: No such file or directory
Failed to open VDPAU backend libvdpau_r200.so: cannot open shared object file: No such file or directory
Failed to open VDPAU backend libvdpau_r200.so: cannot open shared object file: No such file or directory
Failed to open VDPAU backend libvdpau_r200.so: cannot open shared object file: No such file or directory
Failed to open VDPAU backend libvdpau_r200.so: cannot open shared object file: No such file or directory
Failed to open VDPAU backend libvdpau_r200.so: cannot open shared object file: No such file or directory
Failed to open VDPAU backend libvdpau_r200.so: cannot open shared object file: No such file or directory
Failed to open VDPAU backend libvdpau_r200.so: cannot open shared object file: No such file or directory
Failed to open VDPAU backend libvdpau_r200.so: cannot open shared object file: No such file or directory
** Message: init gpgme version 1.2.0
WARNING: gnome-keyring:: couldn't connect to: /run/user/user/keyring-xxxxxx/pkcs11: No such file or directory

** (seahorse:3086): WARNING **: Couldn't initialize registered PKCS#11 modules: An error occurred on the device
** Message: init gpgme version 1.2.0
WARNING: gnome-keyring:: couldn't connect to: /run/user/user/keyring-xxxxxx/pkcs11: No such file or directory

** (seahorse:3209): WARNING **: Couldn't initialize registered PKCS#11 modules: An error occurred on the device
** Message: PID 3324 (we are 2286) sent signal 15, shutting down...

(nm-applet:2286): libappindicator-WARNING **: Unable to send signal for NewStatus: The connection is closed
** Message: moving back from GtkStatusIcon to indicator

(nm-applet:2286): Gtk-CRITICAL **: gtk_status_icon_set_visible: assertion `GTK_IS_STATUS_ICON (status_icon)' failed
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0"
      after 210489 requests (210489 known processed) with 0 events remaining.
pcmanfm: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.

```

I have anonymized user reference and x'ed out keyring reference for security reasons.

The resulting desktop still has base functionality. I can right click on the desktop, which brings up a pop-up with a subset of the programs that should be available on the start menu. <ctrl>+<alt>+<t> still brings up a terminal, so programs can be run by invoking from the command line. Most curiously, guest sessions still bring up the full desktop; only regular users are missing lubuntu-desktop. Moreover, choosing lubuntu netbook at login will bring up a functional desktop with desktop icons and panel. The only option that seems to be choking is the default lubuntu desktop for regular users. Has anyone else experienced this?

I have found two work-arounds:

1. invoke lxpanel from a terminal, which gives me most of the functionality but still missing Desktop icons, and

2. downloaded lxde metapackage from the repository, which gives me a fully functional alternative lxde desktop. Because this second workaround yields a fully functional desktop, this is no longer a critical problem, but I would still like to get to the bottom of things.

More info:

I upgraded a Dell Latitude D600 laptop with the notorious Pentium M processor which lacks PAE capability. Did not review the forum threads giving warning to this known problem until the upgrade process failed to install the 3.5.0-18-generic kernel and fell back to the 3.2.0-33-generic kernel. Upgrade did manage to complete with fallback older kernel, but could missing desktop be tied in to missing kernel? Since the lxde desktop is working properly, this would seem to be unlikely, but one never knows.

All comments/observations appreciated.

---

### Post by Clayhanger on 2012-11-17
I've just hit exactly the same problem after upgrading a Dell Inspiron  9400. I'm using 3.5.0-18-generic, so it's not a kernel issue. I used your workaround of installing the LXDE metapackage and now have a functional system, though it's not a real fix.

Moral: wait a couple of months before doing an upgrade :(

---

### Post by DuckHook on 2012-11-17
> **Clayhanger said:**
> I've just hit exactly the same problem after upgrading a Dell Inspiron  9400. I'm using 3.5.0-18-generic, so it's not a kernel issue. I used your workaround of installing the LXDE metapackage and now have a functional system, though it's not a real fix.

Moral: wait a couple of months before doing an upgrade :(

I normally wait--as you rightly note to be good practice--but I was in the awkward position of having to allow guest sessions use of chromium browser, and 12.04 does not allow guest users browser access due to a different bug that the developers have deemed to be low priority for a fix. The upgrade solves that issue only to introduce a bigger one. Actually, my bigger worry is that my processor is no longer supported in future updates/upgrades. I can live with LXDE. After all, its desktop is almost identical to the Lubuntu default. However, if I'm cut off from newer kernel updates, then I'm concerned about some important app no longer being supported under old kernels at some future time.

I'm a Linux enthusiast, but this sort of stuff really turns off new users. Isn't Lubuntu an attractive distro because it works on older hardware that has been orphaned by the proprietary vendors? It seems counter-productive to adopt a new kernel that in essence orphans that same hardware. But I'm off topic--I will leave a bug report in Launchpad re: the missing desktop, and mark this thread solved, though it isn't, really.

---

### Post by Clayhanger on 2012-11-17
Hopefully one of the Lubuntu gurus will be able to identify the problem. I suspect it's something to do with customising the interface (themes, colours etc) which breaks the 12.10 upgrade. If so we won't be the only people to encounter it :)

---

### Post by chconnor on 2012-11-20
> **Clayhanger said:**
> If so we won't be the only people to encounter it :)

Indeed you are not. :-)

I will try the lxde install -- what are the ramifications of that? Just an issue of losing some config values? Any implications for future upgrade path?

I'm on an Asus Eee PC 901SD. Using the 3.5.0-18 kernel as well.

How do you view the run.log file? I have nothing like that in /var/log/... special config needed to make lxsession log?

Did you make a launchpad bug yet?

Thanks!

---

### Post by DuckHook on 2012-11-21
> **chconnor said:**
> :-)
what are the ramifications of that? Just an issue of losing some config values? Any implications for future upgrade path?

My experiences so far is that the desktop is recreated intact, but I've lost some autostart apps likely due to the fact that LXDE looks elsewhere than ~/.cache/lxsession/lxde/autostart for startup files.

run.log can be found with find, locate or catfish if you prefer graphical utility.

lxsession is still generating a segfault. It just doesn't clobber the desktop when it dies.

Don't know about ramifications for future upgrades, but I intend to do a virgin install next time, so it's an academic question for me.

The system itself is generating an apport report, but since 12.10 has now been released, it has probably been going to ubuntu.errors instead of launchpad. Therefore, I won't be filing an independent launchpad report.

---

### Post by chconnor on 2012-11-21
> [quote]what are the ramifications of that? Just an issue of losing some config values? Any implications for future upgrade path?

My experiences so far is that the desktop is recreated intact, but I've lost some autostart apps likely due to the fact that LXDE looks elsewhere than ~/.cache/lxsession/lxde/autostart for startup files.[/quote]

Thanks... i'm going to hold off, though... wanna poke around a little more.

How do you know that lxsession is segfaulting?

> run.log can be found with find, locate or catfish if you prefer graphical utility.

Thanks... i had tried locate but had to use a brute-force find to find it for some reason.

> The system itself is generating an apport report, but since 12.10 has now been released, it has probably been going to ubuntu.errors instead of launchpad. Therefore, I won't be filing an independent launchpad report.

I see nothing in /var/log/apport.log -- is that the place to look?

```
** Message: utils.vala:68: User config used : /home/casey/.config/lxsession/Lubuntu/desktop.conf
** Message: utils.vala:89: Final file used : /home/casey/.config/lxsession/Lubuntu/desktop.conf
** Message: utils.vala:68: User config used : /home/casey/.config/lxsession/Lubuntu/desktop.conf
** Message: utils.vala:89: Final file used : /home/casey/.config/lxsession/Lubuntu/desktop.conf
** Message: settings.vala:252: Key file does not have key 'window_manager/program'
** Message: settings.vala:261: Key file does not have key 'window_manager/session'
** Message: settings.vala:270: Key file does not have key 'window_manager/extras'
** Message: settings.vala:291: Key file does not have key 'panel/program'
** Message: settings.vala:301: Key file does not have key 'screensaver/program'
** Message: settings.vala:311: Key file does not have key 'power-manager/program'
** Message: settings.vala:341: Key file does not have key 'file-manager/program'
** Message: settings.vala:351: Key file does not have key 'polkit'
** Message: settings.vala:361: Key file does not have key 'network_gui'
** Message: settings.vala:371: Key file does not have key 'audio_manager'
** Message: settings.vala:381: Key file does not have key 'quit_manager'
** Message: settings.vala:391: Key file does not have key 'workspace_manager'
** Message: settings.vala:401: Key file does not have key 'launcher_manager'
** Message: settings.vala:411: Key file does not have key 'terminal_manager'
** Message: settings.vala:421: Key file does not have key 'clipboard'
** Message: settings.vala:431: Key file does not have key 'disable_autostart'
** Message: settings.vala:441: Key file does not have group 'State'
** Message: settings.vala:451: Key file does not have group 'Dbus'
** Message: settings.vala:460: Key file does not have group 'Dbus'
** Message: settings.vala:506: Key file does not have group 'Keymap'
** Message: settings.vala:527: Key file does not have group 'XRandr'

** (lxsession:1369): WARNING **: settings.vala:537: Key file does not have group 'Security'
** Message: settings.vala:185: Monitoring: /home/casey/.config/lxsession/Lubuntu/desktop.conf
** Message: settings.vala:189: Desktop file is already in config home, do nothing
** Message: options.vala:154: Create build-in Clipboard
** Message: utils.vala:79: Config system location : /etc/xdg/lubuntu/lxsession/Lubuntu
** Message: utils.vala:79: Config system location : /etc/xdg/xdg-Lubuntu/lxsession/Lubuntu
** Message: utils.vala:79: Config system location : /etc/xdg/lxsession/Lubuntu
** Message: utils.vala:85: System system path location : /etc/xdg/lxsession/Lubuntu/conffiles.conf
** Message: utils.vala:89: Final file used : /etc/xdg/lxsession/Lubuntu/conffiles.conf
** Message: utils.vala:68: User config used : /home/casey/.config/lxsession/Lubuntu/desktop.conf
** Message: utils.vala:89: Final file used : /home/casey/.config/lxsession/Lubuntu/desktop.conf
** Message: app.vala:59: Launching openbox-lubuntu (null) (null)
** Message: utils.vala:68: User config used : /home/casey/.config/lxsession/Lubuntu/autostart
** Message: utils.vala:89: Final file used : /home/casey/.config/lxsession/Lubuntu/autostart
** Message: autostart.vala:44: Autostart path : /home/casey/.config/lxsession/Lubuntu/autostart

** (lxsession:1369): WARNING **: app.vala:62: Failed to execute child process "~/bin/casey_ctrl_key" (No such file or directory)
** Message: app.vala:59: Launching lxterminal --geometry=70x4 -e
** Message: options.vala:37: Options - Launch command (null)

(lxsession:1369): GLib-CRITICAL **: g_spawn_command_line_async: assertion `command_line != NULL' failed
** Message: main.vala:263: Check keymap_mode (null)
Openbox-Message: Requested key "XF86Terminal" does not exist on the display

** (lxterminal:1433): WARNING **: Invalid borders specified for theme pixmap:
        /usr/share/themes/Lubuntu-default/gtk-2.0/images/null.png,
borders don't fit within the image

** (lxterminal:1433): WARNING **: Invalid borders specified for theme pixmap:
        /usr/share/themes/Lubuntu-default/gtk-2.0/images/scrollbar_vertical.png,
borders don't fit within the image
** Message: applet now removed from the notification area
** Message: using fallback from indicator to GtkStatusIcon
** Message: app.vala:73: lxterminal exit with this type of exit: 0
Openbox-Message: Requested key "XF86Terminal" does not exist on the display

** (x-terminal-emulator:1594): WARNING **: Invalid borders specified for theme pixmap:
        /usr/share/themes/Lubuntu-default/gtk-2.0/images/null.png,
borders don't fit within the image

** (x-terminal-emulator:1594): WARNING **: Invalid borders specified for theme pixmap:
        /usr/share/themes/Lubuntu-default/gtk-2.0/images/scrollbar_vertical.png,
borders don't fit within the image
** Message: applet now embedded in the notification area

** (x-terminal-emulator:1704): WARNING **: Invalid borders specified for theme pixmap:
        /usr/share/themes/Lubuntu-default/gtk-2.0/images/null.png,
borders don't fit within the image

** (x-terminal-emulator:1704): WARNING **: Invalid borders specified for theme pixmap:
        /usr/share/themes/Lubuntu-default/gtk-2.0/images/scrollbar_vertical.png,
borders don't fit within the image
```

---

### Post by Clayhanger on 2012-11-21
If you install the LXDE metapackage after a failed 12.04-12.10 upgrade you will be offered an additional 'LXDE' option at the login screen. Choosing this will start an lxde session which will inherit most but not all of your lubuntu configuration. It's easy enough to tweak the bits that are wrong.

Interestingly, the effects of installing the meta on a clean 12.10 installation appear to be different - no 'LXDE' option is offered when logging in. I haven't investigated this at this stage.

---

### Post by DuckHook on 2012-11-21
> How do you know that lxsession is segfaulting?

My syslog shows:

```
Nov 17 19:27:23 Computer kernel: [ 2388.541144] lxsession[3873]: segfault at 0 ip 00f0d718 sp bf93b28c error 4 in libc-2.15.so[e90000+1a3000]
```

> I see nothing in /var/log/apport.log -- is that the place to look?

Never bothered to look at the apport.log to tell the truth. My system behaviour just automatically invokes the usual apport dialogue box informing me of an app failure and asking if I want to report it. It's my understanding that apport sends bugs from beta OSes to launchpad, but directs them to [www.ubuntu.errors](www.ubuntu.errors) (or some such site) after formal release.

---

### Post by DuckHook on 2012-11-21
> **Clayhanger said:**
> the effects of installing the meta on a clean 12.10 installation appear to be different - no 'LXDE' option is offered when logging in.

Odd behaviour. Have you done a clean virgin install and, if so, does it yield the same missing desktop? My problem came about through an upgrade, but if it also happens on a virgin install, then this might point to a cause unrelated to upgrading.

---

### Post by Clayhanger on 2012-11-22
Clean install, but on completely different hardware. The installation completed normally and everything seemed well, but there were a few minor video glitches (old nVidia card) which hadn't been there before. I installed the LXDE meta to try to resolve the glitches, which did indeed disappear. There were no other obvious changes and the login session options remained the same (Lubuntu, Lubuntu Netbook and Openbox).

---

### Post by DuckHook on 2012-11-22
> **Clayhanger said:**
> Clean install, but on completely different hardware.

Hmmm... The different hardware means that we don't really know. I upgraded while away from home. Will do a clean virgin install on the problem machine when I get back just to see if it's hardware based or upgrade based. This thread doesn't seem to have generated many hits, so hopefully, it doesn't affect too many users.

---

### Post by TopQuark_net on 2012-12-18
> **DuckHook said:**
> My syslog shows:

```
Nov 17 19:27:23 Computer kernel: [ 2388.541144] lxsession[3873]: segfault at 0 ip 00f0d718 sp bf93b28c error 4 in libc-2.15.so[e90000+1a3000]
```


This looks like it might be related to:
[https://bugs.launchpad.net/ubuntu/+source/lxsession/+bug/1091819](https://bugs.launchpad.net/ubuntu/+source/lxsession/+bug/1091819)

---

### Post by maxpro4u on 2012-12-30
I also had the issue. I deleted the autostart file in .config/lxsession/Lubuntu and logged out and into lubuntu and everything was back.

---

### Post by DuckHook on 2013-03-08
> **maxpro4u said:**
> I also had the issue. I deleted the autostart file in .config/lxsession/Lubuntu and logged out and into lubuntu and everything was back.

Awfully close to necro-threading, but not quite. Confirming that this fixes the problem. I had defined an autostart file before updating to 12.10 in ~/.config/lxsession/Lubuntu in order to autostart Conky. It seems that 12.10 changed things so that autostart apps are now invoked through .desktop entries in ~/.config/autostart

The presence of an autostart file in ~/.config/lxsession/Lubuntu will cause segfault and bork load of desktop. After deleting rogue autostart file, my desktop is also back to normal. Thanks to @maxpro4u for simple and elegant solution. Will try to mark thread "solved". Can't seem to find this option in new thread tools.

---

### Post by spontex on 2013-08-18
Thank you
Deleting this autostart file also solved this "no desktop after upgrade to Lubuntu 12.10" bug.

---

