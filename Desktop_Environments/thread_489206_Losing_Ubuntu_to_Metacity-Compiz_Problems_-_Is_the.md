---
title: "Losing Ubuntu to Metacity-Compiz Problems - Is there ANY Salvation?"
date: 2007-07-01
forum: Desktop Environments
---

### Post by OzzyFrank on 2007-07-01
I have a Metacity/Compiz problem with many symptoms, so all the info I can gather is included. Sorry if this post is long! Currently the only way I can connect to post this is through this primitive Openbox DE I installed out of curiosity.
***************

In the past week or so (after a Compiz update that took a few goes to install), Metacity has been taking about 3 mins to load after the login screen, which is quite unusual. Now, when this first started I tried to change "compiz" in the window manager section of gconf to "metacity", and the desktop would load instantly and all seemed fine, except for an error message box that pops up (its output is listed further below):

*********************

Your session only lasted less than 10 seconds. If you have not logged out yourself, this could mean that there is some installation problem or that you may be out of diskspace. Try logging in with one of the failsafe sessions to see if you can fix this problem.

View details (~/.xsession-errors file)

********************

If I left it alone, I could continue using my computer, and so far the only thing I have seen that wouldn't load is the Sessions applet (says it's loading but never shows) and when I click the shutdown button all the panels disappear (so I ctrl+alt+backspace). If I click OK on the error message box it instantly sends me back to the login screen.

I originally ended up changing "metacity" back to "compiz" in gconf, and just putting up with the 2.5 - 3 mins it takes Metacity to load (since it was stable after the slow start), but things have gotten worse since updating fglrx and compiz on 30th June. It now takes longer, and when the desktop starts loading, I see a brief glimpse of error messages saying something about Nautilus and not being able to load a panel before the system logs itself out and I am back to the login screen. Half the time when this happens the screen is going haywire (at the login screen, like it's trying to load a display driver that won't work). Note that I've already gotten rid of any changes to xorg.conf as I copied over a safe backup, which usually fixes any screen issues (its trying to get fglrx to run that usually messes it up, and reverting to safe defaults is something I am used to doing).

When logging back in, it either just stays at the splash which says Metacity Window Manager is loading, or takes me to a desktop that logs itself out then back in again after a couple of errors that pass by too quicly for me to read... continually.

And now (after the update or whatever) changing "compiz" to "metacity" again, the desktop loads, but it logs out again, then when I log back in I get the error message I don't dare click.

As for Failsafe Gnome, I today noticed none of the windows have the title bars (which is I think weird for Failsafe session? Don't think it was like that when it first started and I used it to fix things). Another thing is that a couple days ago I thought I'd see what saving a session does in Sessions, and now previous apps keep loading even though I've told it NOT to automatically save new sessions. Not sure if that is related but I'm trying to include all symptoms.

And with the very last "metacity" login it did so with not only the session error, but now I also have the Nautilus error in front of me (before it was only when "compiz" was the wm in gconf, and showed briefly before the log out):

**********
Nautilus can't be used now, due to an unexpected error from Bonobo when attempting to locate the factory. Killing bonobo-activation-server and restarting Nautilus may help fix the problem.
**********

Now I have a desktop with no wallpaper or icons, but the panels are there in default mode (no metacity theme or transparency). So now using "metacity" instead of "compiz" in gconf is not really much better, though I wasn't planning to keep it that way. Still, I'm here and able to type, not like with the loop loading compiz, though can't connect online so will have to save this and post from Windows (eek!). Still, looks like this is getting progressively worse!

Anyway, below is the output from the original session error message, followed by its output earlier today when it all started going to hell, then the output from this weird session I'm in now (they differ quite a lot). I'm hoping someone here can make sense of it all and see what is causing the error (or at least know how to get around this).

PS: I'm not out of disk space (have 90Gb spare).

***********

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "ozzman"
/etc/gdm/Xsession: Beginning session setup...
No profile for user 'ozzman' found
SESSION_MANAGER=local/ozzman-desktop:/tmp/.ICE-unix/6126
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"
Window manager warning: Screen 0 on display ":0.0" already has a window manager; try using the --replace option to replace the current window manager.
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"
Window manager warning: Screen 0 on display ":0.0" already has a window manager; try using the --replace option to replace the current window manager.
Initializing nautilus-open-terminal extension
Initializing gnome-mount extension
** Message: failed to load session from /home/ozzman/.nautilus/saved-session-VB4PUT
*** glibc detected *** /usr/bin/gnome-session: free(): invalid next size (fast): 0x0828a2a0 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb76417cd]
/lib/tls/i686/cmov/libc.so.6(cfree+0x90)[0xb7644e30]
/usr/lib/libICE.so.6(_IcePaMagicCookie1Proc+0x18e)[0xb7ebdc3e]
/usr/lib/libICE.so.6[0xb7ec67c4]
/usr/lib/libICE.so.6(_IceProcessCoreMessage+0xfb)[0xb7ec7a3b]
/usr/lib/libICE.so.6(IceProcessMessages+0x15f)[0xb7ec8d3f]
/usr/lib/libgnomeui-2.so.0[0xb7f1b605]
/usr/lib/libglib-2.0.so.0[0xb777b40d]
/usr/lib/libglib-2.0.so.0(g_main_context_dispatch+0x182)[0xb7751df2]
/usr/lib/libglib-2.0.so.0[0xb7754dcf]
/usr/lib/libglib-2.0.so.0(g_main_context_iteration+0x65)[0xb7755335]
/usr/bin/gnome-session[0x8055789]
/usr/lib/libglib-2.0.so.0[0xb777b40d]
/usr/lib/libglib-2.0.so.0(g_main_context_dispatch+0x182)[0xb7751df2]
/usr/lib/libglib-2.0.so.0[0xb7754dcf]
/usr/lib/libglib-2.0.so.0(g_main_loop_run+0x1a9)[0xb7755179]
/usr/lib/libgtk-x11-2.0.so.0(gtk_main+0xb4)[0xb7c89044]
/usr/bin/gnome-session(main+0x5de)[0x805638e]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc)[0xb75efebc]
/usr/bin/gnome-session[0x8051d51]
======= Memory map: ========
08048000-08068000 r-xp 00000000 08:11 548        /usr/bin/gnome-session
08068000-08069000 rw-p 00020000 08:11 548        /usr/bin/gnome-session
08069000-082af000 rw-p 08069000 00:00 0          [heap]
b3500000-b3521000 rw-p b3500000 00:00 0 
b3521000-b3600000 ---p b3521000 00:00 0 
b3654000-b365f000 r-xp 00000000 08:11 93344      /lib/libgcc_s.so.1
b365f000-b3660000 rw-p 0000a000 08:11 93344      /lib/libgcc_s.so.1
b3676000-b3677000 ---p b3676000 00:00 0 
b3677000-b3e77000 rw-p b3677000 00:00 0 
b3e77000-b3ef4000 r--p 00000000 08:11 31440      /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
b3ef4000-b3ef6000 r-xp 00000000 08:11 8813       /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b3ef6000-b3ef7000 rw-p 00001000 08:11 8813       /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b3ef7000-b3efd000 r--s 00000000 08:11 86191      /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-x86.cache-2
b3efd000-b3efe000 r--s 00000000 08:11 86219      /var/cache/fontconfig/fd9505950c048a77dc4b710eb6a628ed-x86.cache-2
b3efe000-b3f01000 r--s 00000000 08:11 86207      /var/cache/fontconfig/ddc79d3ea06a7c6ffa86ede85f3bb5df-x86.cache-2
b3f01000-b3f02000 r--s 00000000 08:11 86213      /var/cache/fontconfig/e7071f4a29fa870f4323321c154eba04-x86.cache-2
b3f02000-b3f03000 r--s 00000000 08:11 86194      /var/cache/fontconfig/a2ab74764b07279e7c36ddb1d302cf26-x86.cache-2
b3f03000-b3f07000 r--s 00000000 08:11 86188      /var/cache/fontconfig/921a30a17f0be15c70ac14043cb7a739-x86.cache-2
b3f07000-b3f08000 r--s 00000000 08:11 86176      /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-x86.cache-2
b3f08000-b3f0a000 r--s 00000000 08:11 86181      /var/cache/fontconfig/646addb8444faa74ee138aa00ab0b6a0-x86.cache-2
b3f0a000-b3f0c000 r--s 00000000 08:11 86169      /var/cache/fontconfig/20bd79ad97094406f7d1b9654bfbd926-x86.cache-2
b3f0c000-b3f0d000 r--s 00000000 08:11 86184      /var/cache/fontconfig/75a2cd575a62c63e802c11411fb87c37-x86.cache-2
b3f0d000-b3f0f000 r--s 00000000 08:11 86192      /var/cache/fontconfig/9c0624108b9a2ae8552f664125be8356-x86.cache-2
b3f0f000-b3f15000 r--s 00000000 08:11 86182      /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-x86.cache-2
b3f15000-b3f17000 r--s 00000000 08:11 86208      /var/cache/fontconfig/de156ccd2eddbdc19d37a45b8b2aac9c-x86.cache-2
b3f17000-b3f19000 r--s 00000000 08:11 86205      /var/cache/fontconfig/da1bd5ca8443ffe22927a23ce431d198-x86.cache-2
b3f19000-b3f21000 r--s 00000000 08:11 86211      /var/cache/fontconfig/e3de0de479f42330eadf588a55fb5bf4-x86.cache-2
b3f21000-b3f27000 r--s 00000000 08:11 86165      /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-x86.cache-2
b3f27000-b3f28000 r--s 00000000 08:11 86174      /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-x86.cache-2
b3f28000-b3f3f000 r--s 00000000 08:11 86200      /var/cache/fontconfig/365b55f210c0a22e9a19e35191240f32-x86.cache-2
b3f3f000-b3f41000 r--s 00000000 08:11 86209      /var/cache/fontconfig/de9486f0b47a4d768a594cb4198cb1c6-x86.cache-2
b3f41000-b3f47000 r--s 00000000 08:11 86203      /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-x86.cache-2
b3f47000-b3f4a000 r--s 00000000 08:11 86180      /var/cache/fontconfig/6386b86020ecc1ef9690bb720a13964f-x86.cache-2
b3f4a000-b3f4e000 r--s 00000000 08:11 86163      /var/cache/fontconfig/089dead882dea3570ffc31a9898cfb69-x86.cache-2
b3f4e000-b3f50000 r--s 00000000 08:11 86502      /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-x86.cache-2
b3f50000-b3f51000 r--s 00000000 08:11 86217      /var/cache/fontconfig/fcff1cd55d48a2c86a175e9943c3506d-x86.cache-2
b3f51000-b3f52000 r--s 00000000 08:11 86214      /var/cache/fontconfig/e9e44584608a73233979f764b5f9dd81-x86.cache-2
b3f52000-b3f53000 r--s 00000000 08:11 86199      /var/cache/fontconfig/b5a4f3f568a71026ccdc6a3a51afa9b4-x86.cache-2
b3f53000-b3f54000 r--s 00000000 08:11 86170      /var/cache/fontconfig/2561679576a9c7fd2ce41d281d4e00d1-x86.cache-2
b3f54000-b3f55000 r--s 00000000 08:11 91664      /var/cache/fontconfig/b8613a33de00eecd32d5a94c3c617829-x86.cache-2
b3f55000-b3f58000 r--s 00000000 08:11 86196      /var/cache/fontconfig/b21a91cee725896328b8cee8091cf747-x86.cache-2
b3f58000-b3f5d000 r--s 00000000 08:11 91663      /var/cache/fontconfig/fd9416c4b92f07c6f59a3a8cf496e9dc-x86.cache-2
b3f5d000-b3f5f000 r--s 00000000 08:11 86162      /var/cache/fontconfig/059138ec877db160474b4d5de1248d14-x86.cache-2
b3f5f000-b3f60000 r--s 00000000 08:11 86215      /var/cache/fontconfig/f5a93ac943883aa0fd9a7bfe0f6ec3c1-x86.cache-2
b3f60000-b3f62000 r--s 00000000 08:11 86167      /var/cache/fontconfig/118d8d5311348bbdf5fe3b106d7c13d4-x86.cache-2
b3f62000-b3f63000 r--s 00000000 08:11 86193      /var/cache/fontconfig/a1131b7be650f9abae4907495aa5815d-x86.cache-2
b3f63000-b3f68000 r--s 00000000 08:11 86187      /var/cache/fontconfig/8ab5f685cd6d8ba67c37c908faf08172-x86.cache-2
b3f68000-b3f6c000 r--s 00000000 08:11 86164      /var/cache/fontconfig/0f32d3adc6a232110812e17374eaa446-x86.cache-2
b3f6c000-b3f6e000 r--s 00000000 08:11 86185      /var/cache/fontconfig/7b4a97c10f6c0166998ddfa1cf7392fb-x86.cache-2
b3f6e000-b3f71000 r--s 00000000 08:11 86177      /var/cache/fontconfig/61c830dfac3fd78a12654da5e9ba3f56-x86.cache-2
b3f71000-b3f72000 r--s 00000000 08:11 86210      /var/cache/fontconfig/e0f9e95429e756d56293ed4d63866094-x86.cache-2
b3f72000-b3f74000 r--s 00000000 08:11 86172      /var/cache/fontconfig/4123634e9c08547d899d0aaff05ebe69-x86.cache-2
b3f74000-b3f78000 r--s 00000000 08:11 91661      /var/cache/fontconfig/142ecfc435bad6f1fbc2648c1119d5eb-x86.cache-2
b3f78000-b3f7e000 r--s 00000000 08:11 86166      /var/cache/fontconfig/102e5142c2e9e50c5e8ece26694a2dad-x86.cache-2
b3f7e000-b3f7f000 r--s 00000000 08:11 86189      /var/cache/fontconfig/92a571655fb1c0ec1c4d6f496220600a-x86.cache-2
b3f7f000-b3f87000 r--s 00000000 08:11 86195      /var/cache/fontconfig/a960c40fc9306f090224a04585f8a963-x86.cache-2
b3f87000-b3f96000 r--s 00000000 08:11 15663108   /home/ozzman/.fontconfig/fbbf1c2719c6e053d34100c9b3da2605-x86.cache-2
b3f96000-b4763000 r--p 00000000 08:11 34343      /usr/share/icons/hicolor/icon-theme.cache
b4763000-b61d4000 r--p 00000000 08:11 412920     /usr/share/icons/crystalsvg/icon-theme.cache
b61d4000-b687d000 r--p 00000000 08:11 34401      /usr/share/icons/gnome/icon-theme.cache
b687d000-b6ad4000 r--p 00000000 08:11 44879      /usr/share/icons/Tango/icon-theme.cache
b6ad4000-b6b75000 r--p 00000000 08:11 44877      /usr/share/icons/Tangerine/icon-theme.cache
b6b75000-b6cdb000 r--p 00000000 08:11 44577      /usr/share/icons/Human/icon-theme.cache
b6cdb000-b6ced000 r-xp 00000000 08:11 3880       /usr/lib/gtk-2.0/2.10.0/engines/libubuntulooks.so
b6ced000-b6cee000 rw-p 00011000 08:11 3880       /usr/lib/gtk-2.0/2.10.0/engines/libubuntulooks.so
b6cee000-b6d4e000 rw-s 00000000 00:08 622596     /SYSV00000000 (deleted)
b6d4e000-b6da0000 rw-p b6d4e000 00:00 0 
b6da0000-b6da7000 r-xp 00000000 08:11 1570       /usr/lib/libfam.so.0.0.0
b6da7000-b6da8000 rw-p 00006000 08:11 1570       /usr/lib/libfam.so.0.0.0
b6da8000-b6dae000 r-xp 00000000 08:11 93307      /lib/libacl.so.1.1.0
b6dae000-b6daf000 rw-p 00005000 08:11 93307      /lib/libacl.so.1.1.0
b6daf000-b6db2000 r-xp 00000000 08:11 93311      /lib/libattr.so.1.1.0
b6db2000-b6db3000 rw-p 00002000 08:11 93311      /lib/libattr.so.1.1.0
b6db5000-b6db7000 r--s 00000000 08:11 91660      /var/cache/fontconfig/9404ff413c67fc2a1526fd14eb4163a8-x86.cache-2
b6db7000-b6dba000 r--s 00000000 08:11 86197      /var/cache/fontconfig/b3fedf7c409f006ca1a6fceffceb77cf-x86.cache-2
b6dba000-b6dbc000 r--s 00000000 08:11 91503      /var/cache/fontconfig/6330322105e0c4105d7c7a6ea2974107-x86.cache-2
b6dbc000-b6dbe000 r--s 00000000 08:11 86498      /var/cache/fontconfig/beeeeb3dfe132a8a0633a017c99ce0c0-x86.cache-2
b6dbe000-b6dc2000 r-xp 00000000 08:11 3900       /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
b6dc2000-b6dc3000 rw-p 00003000 08:11 3900       /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
b6dc3000-b6dc7000 r--p 00000000 08:11 59905      /usr/share/locale-langpack/en_AU/LC_MESSAGES/glib20.mo
b6dc7000-b6dc9000 r--p 00000000 08:11 59910      /usr/share/locale-langpack/en_AU/LC_MESSAGES/gnome-desktop-2.0.mo
b6dc9000-b6dd5000 r-xp 00000000 08:11 3823       /usr/lib/gnome-vfs-2.0/modules/libfile.so
b6dd5000-b6dd6000 rw-p 0000b000 08:11 3823       /usr/lib/gnome-vfs-2.0/modules/libfile.so
b6dd6000-b6ddd000 r--p 00000000 08:11 59946      /usr/share/locale-langpack/en_AU/LC_MESSAGES/libgnome-2.0.mo
b6ddd000-b6dde000 r-xp 00000000 08:11 5652662    /usr/lib/gconv/ISO8859-1.so
b6dde000-b6de0000 rw-p 00000000 08:11 5652662    /usr/lib/gconv/ISO8859-1.so
b6de0000-b6de5000 r--p 00000000 08:11 59935      /usr/share/locale-langpack/en_AU/LC_MESSAGES/gtk20-properties.mo
b6de5000-b6df4000 r--p 00000000 08:11 59936      /usr/share/locale-langpack/en_AU/LC_MESSAGES/gtk20.mo
b6df4000-b6e2f000 r--p 00000000 08:11 4435       /usr/lib/locale/en_AU.utf8/LC_CTYPE
b6e2f000-b6f06000 r--p 00000000 08:11 4434       /usr/lib/locale/en_AU.utf8/LC_COLLATE
b6f06000-b6f0f000 r-xp 00000000 08:11 96403      /lib/tls/i686/cmov/libnss_files-2.5.so
b6f0f000-b6f11000 rw-p 00008000 08:11 96403      /lib/tls/i686/cmov/libnss_files-2.5.so
b6f11000-b6f19000 r-xp 00000000 08:11 96407      /lib/tls/i686/cmov/libnss_nis-2.5.so
b6f19000-b6f1b000 rw-p 00007000 08:11 96407      /lib/tls/i686/cmov/libnss_nis-2.5.so
b6f1b000-b6f22000 r-xp 00000000 08:11 96399      /lib/tls/i686/cmov/libnss_compat-2.5.so
b6f22000-b6f24000 rw-p 00006000 08:11 96399      /lib/tls/i686/cmov/libnss_compat-2.5.so
b6f24000-b6f27000 rw-p b6f24000 00:00 0 
b6f27000-b6f5d000 r-xp 00000000 08:11 93398      /lib/libsepol.so.1
b6f5d000-b6f5e000 rw-p 00035000 08:11 93398      /lib/libsepol.so.1
b6f5e000-b6f68000 rw-p b6f5e000 00:00 0 
b6f68000-b6f6b000 r-xp 00000000 08:11 1723       /usr/lib/libgpg-error.so.0.3.0
b6f6b000-b6f6c000 rw-p 00002000 08:11 1723       /usr/lib/libgpg-error.so.0.3.0
b6f6c000-b6fbb000 r-xp 00000000 08:11 1611       /usr/lib/libgcrypt.so.11.2.2
b6fbb000-b6fbd000 rw-p 0004e000 08:11 1611       /usr/lib/libgcrypt.so.11.2.2
b6fbd000-b6fbe000 rw-p b6fbd000 00:00 0 
b6fbe000-b6fd2000 r-xp 00000000 08:11 2067       /usr/lib/libtasn1.so.3.0.6
b6fd2000-b6fd3000 rw-p 00013000 08:11 2067       /usr/lib/libtasn1.so.3.0.6
b6fd3000-b6fd5000 r-xp 00000000 08:11 96420      /lib/tls/i686/cmov/libutil-2.5.so
b6fd5000-b6fd7000 rw-p 00001000 08:11 96420      /lib/tls/i686/cmov/libutil-2.5.so
b6fd7000-b6feb000 r-xp 00000000 08:11 93397      /lib/libselinux.so.1
b6feb000-b6fed000 rw-p 00013000 08:11 93397      /lib/libselinux.so.1
b6fed000-b6ffc000 r-xp 00000000 08:11 96414      /lib/tls/i686/cmov/libresolv-2.5.so
b6ffc000-b6ffe000 rw-p 0000f000 08:11 96414      /lib/tls/i686/cmov/libresolv-2.5.so
b6ffe000-b7000000 rw-p b6ffe000 00:00 0 
b7000000-b700e000 r-xp 00000000 08:11 1449       /usr/lib/libavahi-client.so.3.2.2
b700e000-b700f000 rw-p 0000e000 08:11 1449       /usr/lib/libavahi-client.so.3.2.2
b700f000-b7010000 rw-p b700f000 00:00 0 
b7010000-b701a000 r-xp 00000000 08:11 1451       /usr/lib/libavahi-common.so.3.4.3
b701a000-b701b000 rw-p 00009000 08:11 1451       /usr/lib/libavahi-common.so.3.4.3
b701b000-b701d000 r-xp 00000000 08:11 1455       /usr/lib/libavahi-glib.so.1.0.1
b701d000-b701e000 rw-p 00001000 08:11 1455       /usr/lib/libavahi-glib.so.1.0.1
b701e000-b7088000 r-xp 00000000 08:11 1719       /usr/lib/libgnutls.so.13.0.9
b7088000-b708e000 rw-p 0006a000 08:11 1719       /usr/lib/libgnutls.so.13.0.9
b708e000-b70b0000 r-xp 00000000 08:11 1720391    /usr/lib/libpng12.so.0.15.0
b70b0000-b70b1000 rw-p 00021000 08:11 1720391    /usr/lib/libpng12.so.0.15.0
b70b1000-b70cf000 r-xp 00000000 08:11 1566       /usr/lib/libexpat.so.1.0.0
b70cf000-b70d1000 rw-p 0001d000 08:11 1566       /usr/lib/libexpat.so.1.0.0
b70d1000-b70d2000 rw-p b70d1000 00:00 0 
b70d2000-b713a000 r-xp 00000000 08:11 1688467    /usr/lib/libfreetype.so.6.3.10
b713a000-b713d000 rw-p 00068000 08:11 1688467    /usr/lib/libfreetype.so.6.3.10
b713d000-b7150000 r-xp 00000000 08:11 2125       /usr/lib/libz.so.1.2.3
b7150000-b7151000 rw-p 00012000 08:11 2125       /usr/lib/libz.so.1.2.3
b7151000-b7164000 r-xp 00000000 08:11 96397      /lib/tls/i686/cmov/libnsl-2.5.so
b7164000-b7166000 rw-p 00012000 08:11 96397      /lib/tls/i686/cmov/libnsl-2.5.so
b7166000-b7168000 rw-p b7166000 00:00 0 
b7168000-b716c000 r-xp 00000000 08:11 1356       /usr/lib/libORBitCosNaming-2.so.0.1.0
b716c000-b716d000 rw-p 00003000 08:11 1356       /usr/lib/libORBitCosNaming-2.so.0.1.0
b716d000-b716e000 rw-p b716d000 00:00 0 
b716e000-b7172000 r-xp 00000000 08:11 1381       /usr/lib/libXdmcp.so.6.0.0
b7172000-b7173000 rw-p 00003000 08:11 1381       /usr/lib/libXdmcp.so.6.0.0
b7173000-b7191000 r-xp 00000000 08:11 1848       /usr/lib/libjpeg.so.62.0.0
b7191000-b7192000 rw-p 0001d000 08:11 1848       /usr/lib/libjpeg.so.62.0.0
b7192000-b719a000 r-xp 00000000 08:11 2057       /usr/lib/libstartup-notification-1.so.0.0.0
b719a000-b719b000 rw-p 00007000 08:11 2057       /usr/lib/libstartup-notification-1.so.0.0.0
b719b000-b719c000 rw-p b719b000 00:00 0 
b719c000-b71a3000 r-xp 00000000 08:11 96416      /lib/tls/i686/cmov/librt-2.5.so
b71a3000-b71a5000 rw-p 00006000 08:11 96416      /lib/tls/i686/cmov/librt-2.5.so
b71a5000-b71a9000 r-xp 00000000 08:11 1775       /usr/lib/libgthread-2.0.so.0.1200.11
b71a9000-b71aa000 rw-p 00003000 08:11 1775       /usr/lib/libgthread-2.0.so.0.1200.11
b71aa000-b71ac000 r-xp 00000000 08:11 96392      /lib/tls/i686/cmov/libdl-2.5.so
b71ac000-b71ae000 rw-p 00001000 08:11 96392      /lib/tls/i686/cmov/libdl-2.5.so
b71ae000-b71b0000 r-xp 00000000 08:11 1677       /usr/lib/libgmodule-2.0.so.0.1200.11
b71b0000-b71b1000 rw-p 00002000 08:11 1677       /usr/lib/libgmodule-2.0.so.0.1200.11
b71b1000-b7207000 r-xp 00000000 08:11 1711       /usr/lib/libgnomevfs-2.so.0.1800.1
b7207000-b720a000 rw-p 00055000 08:11 1711       /usr/lib/libgnomevfs-2.so.0.1800.1
b720a000-b7278000 r-xp 00000000 08:11 1474       /usr/lib/libcairo.so.2.11.1
b7278000-b727a000 rw-p 0006d000 08:11 1474       /usr/lib/libcairo.so.2.11.1
b727a000-b727b000 rw-p b727a000 00:00 0 
b727b000-b727f000 r-xp 00000000 08:11 1387       /usr/lib/libXfixes.so.3.1.0
b727f000-b7280000 rw-p 00003000 08:11 1387       /usr/lib/libXfixes.so.3.1.0
b7280000-b7288000 r-xp 00000000 08:11 1377       /usr/lib/libXcursor.so.1.0.2
b7288000-b7289000 rw-p 00007000 08:11 1377       /usr/lib/libXcursor.so.1.0.2
b7289000-b7290000 r-xp 00000000 08:11 1393       /usr/lib/libXi.so.6.0.0
b7290000-b7291000 rw-p 00006000 08:11 1393       /usr/lib/libXi.so.6.0.0
b7291000-b7293000 r-xp 00000000 08:11 1395       /usr/lib/libXinerama.so.1.0.0
b7293000-b7294000 rw-p 00001000 08:11 1395       /usr/lib/libXinerama.so.1.0.0
b7294000-b729b000 r-xp 00000000 08:11 1407       /usr/lib/libXrender.so.1.3.0
b729b000-b729c000 rw-p 00006000 08:11 1407       /usr/lib/libXrender.so.1.3.0
b729c000-b72a9000 r-xp 00000000 08:11 1385       /usr/lib/libXext.so.6.4.0
b72a9000-b72aa000 rw-p 0000d000 08:11 1385       /usr/lib/libXext.so.6.4.0
b72aa000-b72ab000 rw-p b72aa000 00:00 0 
b72ab000-b72ce000 r-xp 00000000 08:11 1572       /usr/lib/libfontconfig.so.1.2.0
b72ce000-b72d6000 rw-p 00023000 08:11 1572       /usr/lib/libfontconfig.so.1.2.0
b72d6000-b72dd000 r-xp 00000000 08:11 1956       /usr/lib/libpangocairo-1.0.so.0.1600.2
b72dd000-b72de000 rw-p 00007000 08:11 1956       /usr/lib/libpangocairo-1.0.so.0.1600.2
b72de000-b7308000 r-xp 00000000 08:11 1958       /usr/lib/libpangoft2-1.0.so.0.1600.2
b7308000-b7309000 rw-p 0002a000 08:11 1958       /usr/lib/libpangoft2-1.0.so.0.1600.2
b7309000-b731d000 r-xp 00000000 08:11 1433       /usr/lib/libart_lgpl_2.so.2.3.17
b731d000-b731e000 rw-p 00013000 08:11 1433       /usr/lib/libart_lgpl_2.so.2.3.17
b731e000-b7325000 r-xp 00000000 08:11 93387      /lib/libpopt.so.0.0.0
b7325000-b7326000 rw-p 00006000 08:11 93387      /lib/libpopt.so.0.0.0
b7326000-b734f000 r-xp 00000000 08:11 1693       /usr/lib/libgnomecanvas-2.so.0.1400.0
b734f000-b7350000 rw-p 00029000 08:11 1693       /usr/lib/libgnomecanvas-2.so.0.1400.0
b7350000-b7351000 rw-p b7350000 00:00 0 
b7351000-b73ac000 r-xp 00000000 08:11 1470       /usr/lib/libbonoboui-2.so.0.0.0
b73ac000-b73af000 rw-p 0005a000 08:11 1470       /usr/lib/libbonoboui-2.so.0.0.0
b73af000-b74c6000 r-xp 00000000 08:11 2119       /usr/lib/libxml2.so.2.6.27
b74c6000-b74cc000 rw-p 00116000 08:11 2119       /usr/lib/libxml2.so.2.6.27
b74cc000-b758c000 r-xp 00000000 08:11 1435       /usr/lib/libasound.so.2.0.0
b758c000-b7591000 rw-p 000bf000 08:11 1435       /usr/lib/libasound.so.2.0.0
b7591000-b75b6000 r-xp 00000000 08:11 96394      /lib/tls/i686/cmov/libm-2.5.so
b75b6000-b75b8000 rw-p 00024000 08:11 96394      /lib/tls/i686/cmov/libm-2.5.so
b75b8000-b75d8000 r-xp 00000000 08:11 1447       /usr/lib/libaudiofile.so.0.0.2
b75d8000-b75da000 rw-p 00020000 08:11 1447       /usr/lib/libaudiofile.so.0.0.2
b75da000-b7715000 r-xp 00000000 08:11 96386      /lib/tls/i686/cmov/libc-2.5.so
b7715000-b7716000 r--p 0013b000 08:11 96386      /lib/tls/i686/cmov/libc-2.5.so
b7716000-b7718000 rw-p 0013c000 08:11 96386      /lib/tls/i686/cmov/libc-2.5.so
b7718000-b771c000 rw-p b7718000 00:00 0 
b771c000-b7723000 r-xp 00000000 08:11 93418      /lib/libwrap.so.0.7.6
b7723000-b7724000 rw-p 00007000 08:11 93418      /lib/libwrap.so.0.7.6
b7724000-b77b8000 r-xp 00000000 08:11 1667       /usr/lib/libglib-2.0.so.0.1200.11
b77b8000-b77b9000 rw-p 00093000 08:11 1667       /usr/lib/libglib-2.0.so.0.1200.11
b77b9000-b77c5000 r-xp 00000000 08:11 1683       /usr/lib/libgnome-keyring.so.0.0.1
b77c5000-b77c6000 rw-p 0000b000 08:11 1683       /usr/lib/libgnome-keyring.so.0.0.1
b77c6000-b77ff000 r-xp 00000000 08:11 1721       /usr/lib/libgobject-2.0.so.0.1200.11
b77ff000-b7800000 rw-p 00039000 08:11 1721       /usr/lib/libgobject-2.0.so.0.1200.11
b7800000-b7831000 r-xp 00000000 08:11 1508       /usr/lib/libdbus-1.so.3.2.0
b7831000-b7832000 rw-p 00031000 08:11 1508       /usr/lib/libdbus-1.so.3.2.0
b7832000-b784c000 r-xp 00000000 08:11 1510       /usr/lib/libdbus-glib-1.so.2.1.0
b784c000-b784d000 rw-p 0001a000 08:11 1510       /usr/lib/libdbus-glib-1.so.2.1.0
b784d000-b784e000 rw-p b784d000 00:00 0 
b784e000-b7861000 r-xp 00000000 08:11 96412      /lib/tls/i686/cmov/libpthread-2.5.so
b7861000-b7863000 rw-p 00013000 08:11 96412      /lib/tls/i686/cmov/libpthread-2.5.so
b7863000-b7865000 rw-p b7863000 00:00 0 
b7865000-b78ae000 r-xp 00000000 08:11 1352       /usr/lib/libORBit-2.so.0.1.0
b78ae000-b78b8000 rw-p 00048000 08:11 1352       /usr/lib/libORBit-2.so.0.1.0
b78b8000-b78e7000 r-xp 00000000 08:11 1609       /usr/lib/libgconf-2.so.4.1.2
b78e7000-b78ea000 rw-p 0002e000 08:11 1609       /usr/lib/libgconf-2.so.4.1.2
b78ea000-b78fd000 r-xp 00000000 08:11 1468       /usr/lib/libbonobo-activation.so.4.0.0
b78fd000-b78ff000 rw-p 00013000 08:11 1468       /usr/lib/libbonobo-activation.so.4.0.0
b78ff000-b7951000 r-xp 00000000 08:11 1466       /usr/lib/libbonobo-2.so.0.0.0
b7951000-b795b000 rw-p 00051000 08:11 1466       /usr/lib/libbonobo-2.so.0.0.0
b795b000-b795c000 rw-p b795b000 00:00 0 
b795c000-b7a49000 r-xp 00000000 08:11 1364       /usr/lib/libX11.so.6.2.0
b7a49000-b7a4d000 rw-p 000ed000 08:11 1364       /usr/lib/libX11.so.6.2.0
b7a4d000-b7a89000 r-xp 00000000 08:11 1954       /usr/lib/libpango-1.0.so.0.1600.2
b7a89000-b7a8b000 rw-p 0003b000 08:11 1954       /usr/lib/libpango-1.0.so.0.1600.2
b7a8b000-b7a90000 r-xp 00000000 08:11 1405       /usr/lib/libXrandr.so.2.1.0
b7a90000-b7a91000 rw-p 00005000 08:11 1405       /usr/lib/libXrandr.so.2.1.0
b7a91000-b7aa7000 r-xp 00000000 08:11 1631       /usr/lib/libgdk_pixbuf-2.0.so.0.1000.11
b7aa7000-b7aa8000 rw-p 00015000 08:11 1631       /usr/lib/libgdk_pixbuf-2.0.so.0.1000.11
b7aa8000-b7ac1000 r-xp 00000000 08:11 1441       /usr/lib/libatk-1.0.so.0.1809.1
b7ac1000-b7ac3000 rw-p 00018000 08:11 1441       /usr/lib/libatk-1.0.so.0.1809.1
b7ac3000-b7b46000 r-xp 00000000 08:11 1629       /usr/lib/libgdk-x11-2.0.so.0.1000.11
b7b46000-b7b49000 rw-p 00083000 08:11 1629       /usr/lib/libgdk-x11-2.0.so.0.1000.11
b7b49000-b7b4a000 rw-p b7b49000 00:00 0 
b7b4a000-b7e9b000 r-xp 00000000 08:11 1778       /usr/lib/libgtk-x11-2.0.so.0.1000.11
b7e9b000-b7ea1000 rw-p 00351000 08:11 1778       /usr/lib/libgtk-x11-2.0.so.0.1000.11
b7ea1000-b7ea2000 rw-p b7ea1000 00:00 0 
b7ea2000-b7eb6000 r-xp 00000000 08:11 1679       /usr/lib/libgnome-2.so.0.1800.0
b7eb6000-b7eb7000 rw-p 00014000 08:11 1679       /usr/lib/libgnome-2.so.0.1800.0
b7eb7000-b7ecc000 r-xp 00000000 08:11 1342       /usr/lib/libICE.so.6.3.0
b7ecc000-b7ece000 rw-p 00014000 08:11 1342       /usr/lib/libICE.so.6.3.0
b7ece000-b7ecf000 rw-p b7ece000 00:00 0 
b7ecf000-b7ed7000 r-xp 00000000 08:11 1360       /usr/lib/libSM.so.6.0.0
b7ed7000-b7ed8000 rw-p 00007000 08:11 1360       /usr/lib/libSM.so.6.0.0
b7ed8000-b7f62000 r-xp 00000000 08:11 1709       /usr/lib/libgnomeui-2.so.0.1788.4
b7f62000-b7f66000 rw-p 00089000 08:11 1709       /usr/lib/libgnomeui-2.so.0.1788.4
b7f66000-b7f7a000 r-xp 00000000 08:11 1681       /usr/lib/libgnome-desktop-2.so.2.3.5
b7f7a000-b7f7b000 rw-p 00014000 08:11 1681       /usr/lib/libgnome-desktop-2.so.2.3.5
b7f7b000-b7f7c000 rw-p b7f7b000 00:00 0 
b7f7c000-b7f85000 r-xp 00000000 08:11 1557       /usr/lib/libesd.so.0.2.36
b7f85000-b7f86000 rw-p 00009000 08:11 1557       /usr/lib/libesd.so.0.2.36
b7f86000-b7f88000 r-xp 00000000 08:11 1370       /usr/lib/libXau.so.6.0.0
b7f88000-b7f89000 rw-p 00001000 08:11 1370       /usr/lib/libXau.so.6.0.0
b7f8a000-b7f8e000 r--p 00000000 08:11 59921      /usr/share/locale-langpack/en_AU/LC_MESSAGES/gnome-session-2.0.mo
b7f8e000-b7f8f000 r--p 00000000 08:11 4440       /usr/lib/locale/en_AU.utf8/LC_NUMERIC
b7f8f000-b7f90000 r--p 00000000 08:11 4443       /usr/lib/locale/en_AU.utf8/LC_TIME
b7f90000-b7f91000 r--p 00000000 08:11 4438       /usr/lib/locale/en_AU.utf8/LC_MONETARY
b7f91000-b7f92000 r--p 00000000 08:11 4646       /usr/lib/locale/en_AU.utf8/LC_MESSAGES/SYS_LC_MESSAGES
b7f92000-b7f93000 r--p 00000000 08:11 4441       /usr/lib/locale/en_AU.utf8/LC_PAPER
b7f93000-b7f94000 r--p 00000000 08:11 4439       /usr/lib/locale/en_AU.utf8/LC_NAME
b7f94000-b7f95000 r--p 00000000 08:11 4433       /usr/lib/locale/en_AU.utf8/LC_ADDRESS
b7f95000-b7f96000 r--p 00000000 08:11 4442       /usr/lib/locale/en_AU.utf8/LC_TELEPHONE
b7f96000-b7f97000 r--p 00000000 08:11 4437       /usr/lib/locale/en_AU.utf8/LC_MEASUREMENT
b7f97000-b7f9e000 r--s 00000000 08:11 5652715    /usr/lib/gconv/gconv-modules.cache
b7f9e000-b7f9f000 r--p 00000000 08:11 4436       /usr/lib/locale/en_AU.utf8/LC_IDENTIFICATION
b7f9f000-b7fa1000 rw-p b7f9f000 00:00 0 
b7fa1000-b7fba000 r-xp 00000000 08:11 93301      /lib/ld-2.5.so
b7fba000-b7fbc000 rw-p 00019000 08:11 93301      /lib/ld-2.5.so
bff8f000-bffa4000 rw-p bff8f000 00:00 0          [stack]
ffffe000-fffff000 r-xp 00000000 00:00 0          [vdso]

(gnome-power-manager:6226): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.

(gnome-cups-icon:6234): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.

(gnome-terminal:6236): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.

(evolution-alarm-notify:6233): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.
evolution-alarm-notify-Message: Setting timeout for 41943 1183212000 1183170057
evolution-alarm-notify-Message:  Sun Jul  1 00:00:00 2007

evolution-alarm-notify-Message:  Sat Jun 30 12:20:57 2007


(update-notifier:6232): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.

(gconf-editor:6227): GnomeUI-WARNING **: While connecting to session manager:
IO error occured doing Protocol Setup on connection.

********************
then this one after yesterday's fglrx and compiz updates:
********************

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "ozzman"
/etc/gdm/Xsession: Beginning session setup...
No profile for user 'ozzman' found
SESSION_MANAGER=local/ozzman-desktop:/tmp/.ICE-unix/8135
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"
Window manager warning: Screen 0 on display ":0.0" already has a window manager; try using the --replace option to replace the current window manager.
Initializing nautilus-open-terminal extension
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"
Window manager warning: Screen 0 on display ":0.0" already has a window manager; try using the --replace option to replace the current window manager.
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Initializing gnome-mount extension
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

(gnome-panel:8222): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -3 and height 24
Unable to open desktop file file:///home/ozzman/Desktop/Edit%20Sources%20List%20(copy).desktop for panel launcher: No such file or directory
Unable to open desktop file file:///home/ozzman/Desktop/Edit%20Xserver.desktop for panel launcher: No such file or directory
Unable to open desktop file file:///home/ozzman/Desktop/Edit%20Defaults%20to%20Change%20Splash%20Image.desktop for panel launcher: No such file or directory

(update-notifier:8241): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.

*************
and the final one from the current session:
*************

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "ozzman"
/etc/gdm/Xsession: Beginning session setup...
No profile for user 'ozzman' found
SESSION_MANAGER=local/ozzman-desktop:/tmp/.ICE-unix/6181
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"
Window manager warning: Screen 0 on display ":0.0" already has a window manager; try using the --replace option to replace the current window manager.
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"
Window manager warning: Screen 0 on display ":0.0" already has a window manager; try using the --replace option to replace the current window manager.
Initializing nautilus-open-terminal extension
Initializing gnome-mount extension
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Session management error: IO error occured opening connection

(update-notifier:6284): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.

(gnome-power-manager:6285): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.

(gnome-cups-icon:6289): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.

(gedit:6295): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.

(gnome-terminal:6294): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.

---

### Post by punkybouy on 2007-07-01
Not really a solution but you could create another user and login as that user.  At least it might give you a little more stability while you figured out what was wrong.

---

### Post by OzzyFrank on 2007-07-01
Forgive my ignorance, but wouldn't creating another user just let me log in as someone else to the same problems? I gather if I am logging into Gnome it will try load the same stuff (ie the horrid Compiz updates etc). Now, I mentioned I had to log into Openbox, which I had just installed for no other reason than to have a look. After running Nautilus it turned into a half-Gnome-half-Openbox thing with no panels, no Openbox right-click menu, and with Metacity running... not the best solution, but it allowed me to log online and post the message (wvdial just wasn't initiating in Gnome). Afterwards, I thought I'd try the Kubuntu desktop, and lo and behold, it seemed to work fine for the few minutes I was there. I'm currently online in Windows, so will test later if Kubuntu is fine in that respect too. Looks like I'll have some sort of access to my Ubuntu system at least. But this isn't a solution, so if anyone had ideas for getting Gnome back, they'll be appreciated!

---

### Post by OzzyFrank on 2007-07-02
OK, an update on more weird symptoms, some work arounds, and a "fix" of sorts.

So, Gnome would log out and in again with the message about the xsession error, but I could use more things, Metacity themes were there, but for the life of me couldn't connect online. Just in case it was wvdial for some reason, I went to the effort of configuring pppd but it couldn't seem to find the modem.

Using Openbox... well, that was weird as running Nautilus would suddenly give me my Gnome desktop without the panels (and Openbox would disappear)... but I could use the terminal to run commands I didn't have desktop shortcuts for... and I could connect to the internet no problems.

Running Failsafe Gnome started taking me straight back into that weird half-Gnome-half-Openbox, which wasn't what I expected... but then running the KDE desktop seemed fine, no problems I could see (from a brief look... I'm assuming I could connect from there). So, I suppose you could say that if you've also got the Kubuntu desktop, logging into that instead of Gnome is a workaround that will at least let you get online and get updates, etc.

Anyway, back in a working Gnome with no error messages through the use of some boot options:

noapictimer irqpoll

For newbies who want to try to use this to fix a similar error with Compiz or whatever, when you get to the GRUB menu you'll see at the bottom it says you can hit the "e" key to edit the boot process. Hit "e" and then select the 2nd line, then hit "e" to edit that. It will take you to the end of that line, which is where you type the options (should be after something like "ro quiet vga=771 splash" or "ro single"). Hit Enter when finished then "b" to boot.

Still wouldn't mind all this fixed up, but for now I'll just add a new line to my GRUB menu with this option to save editing it each time.

(Edit: I must be a glutton for punishment as I just let Compiz get updated again, hehe. Actually, I'm just overly trusting and somewhat hopeful, hehe... and too optimistic for my own good.)

---

### Post by OzzyFrank on 2007-07-06
Just confirming that after starting up with those boot options and updating Compiz, all seems fine. I doubt it was from booting once with "irqpoll" etc so gather they did some quick fixing up of things. Cheers

---

