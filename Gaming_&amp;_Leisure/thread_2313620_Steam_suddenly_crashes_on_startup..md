---
title: "Steam suddenly crashes on startup."
date: 2016-02-14
forum: Gaming &amp; Leisure
---

### Post by Reding on 2016-02-14
Hi all,

After months playing on steam without a problem, i just don't seem to be able to start it anymore. The upgrade box shows up and disappears instantly after a few seconds and does't get to the next " connection to account box " like it was the case previously. It just crashes and nothing seem to help (remove-re-installing...).

Here's what i get when i run steam from the terminal.

> steamrm: cannot remove ‘/home/red/.steam/steam’: Is a directory
rm: cannot remove ‘/home/red/.steam/bin’: Is a directory
Running Steam on linuxmint 17.3 64-bit
STEAM_RUNTIME is enabled automatically
[2016-02-14 15:11:50] Startup - updater built Feb  4 2016 12:22:08
Installing breakpad exception handler for appid(steam)/version(1454620878)
Looks like steam didn't shutdown cleanly, scheduling immediate update check
Installing breakpad exception handler for appid(steam)/version(1454620878)
[2016-02-14 15:11:50] Checking for update on startup
[2016-02-14 15:11:50] Checking for available updates...
Installing breakpad exception handler for appid(steam)/version(1454620878)
[2016-02-14 15:11:50] Download skipped: /client/steam_client_ubuntu12 version 1454620878, installed version 1454620878
[2016-02-14 15:11:50] Nothing to do
[2016-02-14 15:11:50] Verifying installation...
[2016-02-14 15:11:50] Performing checksum verification of executable files
[2016-02-14 15:11:51] Verification complete


(steam:5458): Gtk-WARNING **: Unable to locate theme engine in module_path: "adwaita",


(steam:5458): Gtk-WARNING **: Unable to locate theme engine in module_path: "adwaita",
/usr/share/themes/Adwaita/gtk-2.0/gtkrc:1137: error: unexpected identifier `direction', expected character `}'
Installing breakpad exception handler for appid(steam)/version(1454620878)
Fontconfig error: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 70: non-double matrix element
Fontconfig error: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 70: non-double matrix element
Fontconfig warning: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 78: saw unknown, expected number
Fontconfig warning: "~/.fonts.conf", line 627: saw number, expected matrix
[0214/151151:ERROR:main_delegate.cc(777)] Could not load cef_extensions.pak
[0214/151151:ERROR:browser_main_loop.cc(203)] Running without the SUID sandbox! See [https://code.google.com/p/chromium/wiki/LinuxSUIDSandboxDevelopment](https://code.google.com/p/chromium/wiki/LinuxSUIDSandboxDevelopment) for more information on developing with the sandbox on.
Installing breakpad exception handler for appid(steamwebhelper)/version(20160204122139)
Installing breakpad exception handler for appid(steamwebhelper)/version(1454588499)
[0214/151151:ERROR:main_delegate.cc(777)] Could not load cef_extensions.pak
Installing breakpad exception handler for appid(steamwebhelper)/version(20160204122139)
Installing breakpad exception handler for appid(steamwebhelper)/version(1454620878)
Installing breakpad exception handler for appid(steamwebhelper)/version(1454620878)
Installing breakpad exception handler for appid(steam)/version(1454620878)
Installing breakpad exception handler for appid(steam)/version(1454620878)
Installing breakpad exception handler for appid(steam)/version(1454620878)
Installing breakpad exception handler for appid(steam)/version(1454620878)
Installing breakpad exception handler for appid(steam)/version(1454620878)
Installing breakpad exception handler for appid(steam)/version(1454620878)
Created shared memory when not owner SteamController_Shared_mem
Installing breakpad exception handler for appid(steam)/version(1454620878)
Installing breakpad exception handler for appid(steam)/version(1454620878)
Fontconfig error: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 70: non-double matrix element
Fontconfig error: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 70: non-double matrix element
Fontconfig warning: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 78: saw unknown, expected number
Fontconfig warning: "~/.fonts.conf", line 627: saw number, expected matrix
Refresh rate: 1
Refresh rate: 1
Refresh rate: 1
Refresh rate: 1
Refresh rate: 1
Refresh rate: 1
Refresh rate: 1
Refresh rate: 1
Refresh rate: 1
Refresh rate: 1
assert_20160214151150_1.dmp[5513]: Uploading dump (out-of-process)
/tmp/dumps/assert_20160214151150_1.dmp
/home/red/.steam/steam.sh: line 756:  5458 Segmentation fault      $STEAM_DEBUGGER "$STEAMROOT/$STEAMEXEPATH" "$@"
red@ZaReason ~ $ [0214/151152:WARNING:content_browser_client.cc(622)] No browser info matching frame process id 2 and routing id 1
[0214/151152:WARNING:content_browser_client.cc(622)] No browser info matching frame process id 3 and routing id 1
assert_20160214151150_1.dmp[5513]: Finished uploading minidump (out-of-process): success = yes
assert_20160214151150_1.dmp[5513]: response: CrashID=bp-72c9627e-fea1-47f7-95df-0ceb52160214
assert_20160214151150_1.dmp[5513]: file ''/tmp/dumps/assert_20160214151150_1.dmp'', upload yes: ''CrashID=bp-72c9627e-fea1-47f7-95df-0ceb52160214''

There seems to be some errors in the lines indeed.

Help would be highly appreciated as i'm really desperate right now.

Cheers

Red

Ps: I'm on Linux Mint 17.3

---

### Post by james_riddick on 2016-02-14
Yes I have just recently installed a new distro and been tackling this for the past 6 hours to no avail. I'm starting to wonder if valve pushed out a bad update or something? I have tried pretty much everything right down to removing my video drivers and reinstalling it 100 different ways. I'm stumped :(

---

### Post by Reding on 2016-02-16
Did you find a solution ?

I'm still totally stucked with it. Hope someone can come up with an answer

---

### Post by MikeCyber on 2016-02-17
Maybe installed as sudo? Never, always use regular user if possible. There are two versions. One to install with synaptic and the other download from steam.
Try the other after having installed your graphics drivers with synaptic.

---

### Post by Reding on 2016-02-18
Well i installed it with this command "sudo apt-get install steam" if it is what you mean. I purged it it using the command line as well since it was crashing and tried to install it from steam's website. Didn't change anything. Same for the synaptic package.

---

### Post by MikeCyber on 2016-02-18
I would completely uninstall and delete manually in your home the hidden steam folder:
rm -rf .steam
maybe search for steam like:
whereis steam
or
find / -name "*team"
foremost delete the ~/.steam folder.

---

