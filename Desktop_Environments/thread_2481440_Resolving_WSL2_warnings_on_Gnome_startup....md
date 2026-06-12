---
title: "Resolving WSL2 warnings on Gnome startup..."
date: 2022-11-29
forum: Desktop Environments
---

### Post by prusso555 on 2022-11-29
I have the following warnings showing up in my terminal when I start a gnome desktop environment which does start up and show a functional desktop with the jelly fish on the orange background for Ubuntu 22.04.1 LTS which was installed via x410's installation documentation (I am using x410 in floating desktop mode):

[HTML]
prusso@tablet:~$ ~/bin/start-desktop.shlibmutter-Message: 15:37:06.730: Running GNOME Shell (using mutter 42.5) as a X11 window and compositing managerXlib:  extension "DPMS" missing on display "192.168.16.1:0.0".Xlib:  extension "DPMS" missing on display "192.168.16.1:0.0".
** (gnome-shell:179): WARNING **: 15:37:06.850: ATK Bridge is disabled but a11y has already been enabled.GNOME Shell-Message: 15:37:07.460: Failed to register AuthenticationAgentGNOME Shell-Message: 15:37:07.461: Telepathy is not available, chat integration will be disabled.GNOME Shell-Message: 15:37:07.800: Error calling StartServiceByName for net.hadess.PowerProfiles: Launch helper exited with unknown return code 1GNOME Shell-Message: 15:37:07.881: Error looking up permission: GDBus.Error:org.freedesktop.portal.Error.NotFound: No entry for geolocationWindow manager warning: Overwriting existing binding of keysym 32 with keysym 32 (keycode b).Window manager warning: Overwriting existing binding of keysym 34 with keysym 34 (keycode d).Window manager warning: Overwriting existing binding of keysym 35 with keysym 35 (keycode e).Window manager warning: Overwriting existing binding of keysym 36 with keysym 36 (keycode f).Window manager warning: Overwriting existing binding of keysym 38 with keysym 38 (keycode 11).Window manager warning: Overwriting existing binding of keysym 39 with keysym 39 (keycode 12).Window manager warning: Overwriting existing binding of keysym 37 with keysym 37 (keycode 10).Window manager warning: Overwriting existing binding of keysym 31 with keysym 31 (keycode a).Window manager warning: Overwriting existing binding of keysym 33 with keysym 33 (keycode c).GNOME Shell-Message: 15:37:08.553: GNOME Shell started at Tue Nov 29 2022 15:37:07 GMT-0800 (PST)Ubuntu Dock-Message: 15:37:08.553: Registering session with GDMUbuntu Dock-Message: 15:37:08.674: Error registering session with GDM: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.DisplayManager was not provided by any .service filesDING: Detected async api for thumbnailsDING: GNOME nautilus 42.2[/HTML]

So what I am looking to resolve are these notifications:

    - A DPMS that is missing.
    - ATK Bridge is disabled but a11y has already been enabled *(Is this a problem or what does it mean in terms of Windows Subsystem for Linux 2?)*
    -  Error looking up permission: GDBus.Error:org.freedesktop.portal.Error.NotFound: No entry for geolocation *(Is there a way to add the entry for geolocation?)*
    - Error registering session with GDM: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.DisplayManager was not provided by any .service files [I](Is this resolvable and or is it or will it be problematic in terms of running GUI application?)


Thanks....[/I]

---

