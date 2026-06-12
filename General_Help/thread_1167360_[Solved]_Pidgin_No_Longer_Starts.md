---
title: "[Solved] Pidgin No Longer Starts"
date: 2009-05-22
forum: General Help
---

### Post by Literati on 2009-05-22
For the record, I have posted this on the Pidgin Trac, but I was just wondering if I could get a response from someone who might've already had this problem and fixed it for themselves... Anyway, on we go:

```
(18:42:39) prefs: Reading /home/matt/.purple/prefs.xml
(18:42:39) prefs: Finished reading /home/matt/.purple/prefs.xml
(18:42:39) dbus: okkk
(18:42:39) plugins: probing /usr/local/lib/pidgin/timestamp_format.so
(18:42:39) plugins: probing /usr/local/lib/pidgin/sendbutton.so
(18:42:39) plugins: probing /usr/local/lib/pidgin/gtkbuddynote.so
(18:42:39) plugins: probing /usr/local/lib/pidgin/spellchk.so
(18:42:39) plugins: probing /usr/local/lib/pidgin/pidginrc.so
(18:42:39) plugins: probing /usr/local/lib/pidgin/timestamp.so
(18:42:39) plugins: probing /usr/local/lib/pidgin/gestures.so
(18:42:39) plugins: probing /usr/local/lib/pidgin/iconaway.so
(18:42:39) plugins: probing /usr/local/lib/pidgin/notify.so
(18:42:39) plugins: probing /usr/local/lib/pidgin/convcolors.so
(18:42:39) plugins: probing /usr/local/lib/pidgin/xmppconsole.so
(18:42:39) plugins: probing /usr/local/lib/pidgin/history.so
(18:42:39) plugins: probing /usr/local/lib/pidgin/markerline.so
(18:42:39) plugins: probing /usr/local/lib/pidgin/musicmessaging.so
(18:42:39) plugins: probing /usr/local/lib/pidgin/relnot.so
(18:42:39) plugins: probing /usr/local/lib/pidgin/extplacement.so
(18:42:39) plugins: probing /usr/local/lib/pidgin/ticker.so
(18:42:39) plugins: probing /usr/lib/purple-2/libsimple.so
(18:42:39) plugins: probing /usr/lib/purple-2/psychic.so
(18:42:39) plugins: probing /usr/lib/purple-2/newline.so
(18:42:39) plugins: probing /usr/lib/purple-2/idle.so
(18:42:39) plugins: probing /usr/lib/purple-2/autoaccept.so
(18:42:39) plugins: probing /usr/lib/purple-2/perl.so
(18:42:39) plugins: probing /usr/lib/purple-2/libsametime.so
(18:42:39) plugins: /usr/lib/purple-2/libsametime.so has a prefs_info, but is a prpl. This is no longer supported.
(18:42:39) plugins: probing /usr/lib/purple-2/libxmpp.so
(18:42:39) util: Reading file xmpp-caps.xml from directory /home/matt/.purple
(18:42:39) util: File /home/matt/.purple/xmpp-caps.xml does not exist (this is not necessarily an error)
(18:42:39) jabber: creating hash tables for data objects
(18:42:39) plugins: probing /usr/lib/purple-2/libfacebook64.so
(18:42:39) plugins: probing /usr/lib/purple-2/libzephyr.so
(18:42:39) plugins: probing /usr/lib/purple-2/offlinemsg.so
(18:42:39) plugins: probing /usr/lib/purple-2/ssl.so
(18:42:39) plugins: probing /usr/lib/purple-2/libicq.so
(18:42:39) plugins: probing /usr/lib/purple-2/libsilcpurple.so
(18:42:39) plugins: probing /usr/lib/purple-2/dbus-example.so
(18:42:39) plugins: probing /usr/lib/purple-2/statenotify.so
(18:42:39) plugins: probing /usr/lib/purple-2/libqq.so
(18:42:39) plugins: probing /usr/lib/purple-2/libyahoo.so
(18:42:39) plugins: probing /usr/lib/purple-2/ssl-nss.so
(18:42:39) plugins: probing /usr/lib/purple-2/libirc.so
(18:42:39) plugins: probing /usr/lib/purple-2/libnovell.so
(18:42:39) plugins: probing /usr/lib/purple-2/libaim.so
(18:42:39) plugins: probing /usr/lib/purple-2/liboscar.so
(18:42:39) plugins: /usr/lib/purple-2/liboscar.so is not usable because the 'purple_init_plugin' symbol could not be found.  Does the plugin call the PURPLE_INIT_PLUGIN() macro?
(18:42:39) plugins: probing /usr/lib/purple-2/libjabber.so
(18:42:39) plugins: /usr/lib/purple-2/libjabber.so is not usable because the 'purple_init_plugin' symbol could not be found.  Does the plugin call the PURPLE_INIT_PLUGIN() macro?
(18:42:39) plugins: probing /usr/lib/purple-2/joinpart.so
(18:42:39) plugins: probing /usr/lib/purple-2/libfacebook.so
(18:42:39) plugins: /usr/lib/purple-2/libfacebook.so is not loadable: wrong ELF class: ELFCLASS32
(18:42:39) plugins: probing /usr/lib/purple-2/libmyspace.so
(18:42:39) plugins: probing /usr/lib/purple-2/tcl.so
(18:42:39) plugins: probing /usr/lib/purple-2/log_reader.so
(18:42:39) plugins: probing /usr/lib/purple-2/libmsn.so
(18:42:39) plugins: probing /usr/lib/purple-2/libgg.so
(18:42:39) plugins: probing /usr/lib/purple-2/buddynote.so
(18:42:39) plugins: probing /usr/lib/purple-2/libbonjour.so
(18:42:39) plugins: probing /usr/lib/purple-2/libfacebookppc.so
(18:42:39) plugins: /usr/lib/purple-2/libfacebookppc.so is not loadable: wrong ELF class: ELFCLASS32
(18:42:39) prefs: /purple/status/scores/offline changed, scheduling save.
(18:42:39) prefs: /purple/status/scores/available changed, scheduling save.
(18:42:39) prefs: /purple/status/scores/invisible changed, scheduling save.
(18:42:39) prefs: /purple/status/scores/away changed, scheduling save.
(18:42:39) prefs: /purple/status/scores/extended_away changed, scheduling save.
(18:42:39) prefs: /purple/status/scores/idle changed, scheduling save.
(18:42:39) prefs: /purple/status/scores/offline_msg changed, scheduling save.
(18:42:39) util: Reading file accounts.xml from directory /home/matt/.purple
(18:42:39) util: Reading file status.xml from directory /home/matt/.purple
(18:42:39) certificate: CertificateVerifier x509, singleuse requested but not found.
(18:42:39) certificate: CertificateVerifier singleuse registered
(18:42:39) certificate: CertificatePool x509, ca requested but not found.
(18:42:39) certificate: CertificateScheme x509 requested but not found.
(18:42:39) certificate/x509/ca: Lazy init failed because an X.509 Scheme is not yet registered. Maybe it will be better later.
(18:42:39) certificate/x509/ca: Init failed, probably because a dependency is not yet registered. It has been deferred to later.
(18:42:39) certificate: CertificatePool ca registered
(18:42:39) certificate: CertificatePool x509, tls_peers requested but not found.
(18:42:39) certificate: CertificatePool tls_peers registered
(18:42:39) certificate: CertificateVerifier x509, tls_cached requested but not found.
(18:42:39) certificate: CertificateVerifier tls_cached registered
(18:42:39) prefs: /purple/logging/format changed, scheduling save.
(18:42:39) prefs: /purple/logging/format changed, scheduling save.
(18:42:39) prefs: /purple/proxy/type changed, scheduling save.
(18:42:39) prefs: /purple/proxy/host changed, scheduling save.
(18:42:39) prefs: /purple/proxy/port changed, scheduling save.
(18:42:39) prefs: /purple/proxy/username changed, scheduling save.
(18:42:39) prefs: /purple/proxy/password changed, scheduling save.
(18:42:39) certificate: CertificateScheme x509 requested but not found.
(18:42:39) certificate: CertificateScheme x509 registered
(18:42:39) util: Reading file smileys.xml from directory /home/matt/.purple
(18:42:39) util: File /home/matt/.purple/smileys.xml does not exist (this is not necessarily an error)
(18:42:39) stun: using server 
(18:42:39) sound: Initializing sound output drivers.
(18:42:39) prefs: /pidgin/conversations/placement changed, scheduling save.
(18:42:39) gtkblist: added visibility manager: 1
(18:42:39) docklet: created
(18:42:39) util: Reading file blist.xml from directory /home/matt/.purple
(18:42:39) plugins: Loading saved plugin /usr/local/lib/pidgin/notify.so
(18:42:39) plugins: probing /usr/lib/pidgin/musictracker.so
(18:42:39) plugins: Unable to find saved plugin /usr/lib/pidgin/musictracker.so
(18:42:39) plugins: Loading saved plugin /usr/lib/purple-2/ssl-nss.so
(18:42:39) plugins: probing /usr/lib/pidgin/nautilus.so
(18:42:39) plugins: Loading saved plugin /usr/lib/pidgin/nautilus.so
(18:42:39) nautilus: saved blist online
(18:42:39) plugins: Loading saved plugin /usr/lib/purple-2/ssl.so
(18:42:39) pounce: Error reading pounces: Failed to open file '/home/matt/.purple/pounces.xml': No such file or directory
(18:42:39) ui_main: Failed to load the default window icon (scalablepx version)!
(18:42:39) Session Management: ICE initialized.
(18:42:39) Session Management: Connecting with no previous ID
(18:42:39) Session Management: Handling new ICE connection... 
(18:42:39) done.
(18:42:39) Session Management: Connected to manager (gnome-session) with client ID 10f1315eac77fa0b92124303215989830900000036520046
(18:42:39) Session Management: Using pidgin as command
(18:42:39) dbus: Need to register an object with the dbus subsystem. (If you are not a developer, please ignore this message.)
(18:42:39) dbus: The signal "gtkblist-unhiding" caused some dbus error. (If you are not a developer, please ignore this message.)
(18:42:39) account: Connecting to account [redacted]
(18:42:40) prefs: /purple/savedstatus/isidleaway changed, scheduling save.
(18:42:40) account: Disconnecting account 0x1f1dc10
(18:42:40) connection: Disconnecting connection 0x27cfc60
(18:42:40) facebook: disconnecting account
(18:42:40) g_log: fb_close: assertion `pc->proto_data != NULL' failed
(18:42:40) connection: Destroying connection 0x27cfc60
(18:42:40) dbus: Need to register an object with the dbus subsystem. (If you are not a developer, please ignore this message.)
(18:42:40) dbus: The signal "signing-on" caused some dbus error. (If you are not a developer, please ignore this message.)
(18:42:40) connection: Connecting. gc = 0x27cfc60
Pidgin 2.5.6 has segfaulted and attempted to dump a core file.
This is a bug in the software and has happened through
no fault of your own.

If you can reproduce the crash, please notify the developers
by reporting a bug at:
http://developer.pidgin.im/simpleticket/

Please make sure to specify what you were doing at the time
and post the backtrace from the core file.  If you do not know
how to get the backtrace, please read the instructions at
http://developer.pidgin.im/wiki/GetABacktrace
Aborted
```

[B]
BACKTRACE[/B]


```
matt@matt:~/Other/pidgin-2.5.6$ gdb pidgin
GNU gdb 6.8-debian
Copyright (C) 2008 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.  Type "show copying"
and "show warranty" for details.
This GDB was configured as "x86_64-linux-gnu"...
(gdb) handle SIGPIPE nostop noprint
Signal        Stop	Print	Pass to program	Description
SIGPIPE       No	No	Yes		Broken pipe
(gdb) run
Starting program: /usr/local/bin/pidgin 
[Thread debugging using libthread_db enabled]
[New Thread 0x7fc66acdb7d0 (LWP 29961)]
[New Thread 0x7fc6567cc950 (LWP 29964)]

Program received signal SIGSEGV, Segmentation fault.
[Switching to Thread 0x7fc66acdb7d0 (LWP 29961)]
0x00007fc65b0e1d37 in fb_login (account=0x2166200) at libfacebook.c:283
283	libfacebook.c: No such file or directory.
	in libfacebook.c
(gdb) bt full
#0  0x00007fc65b0e1d37 in fb_login (account=0x2166200) at libfacebook.c:283
	fba = <value optimized out>
	postdata = <value optimized out>
	encoded_username = <value optimized out>
	encoded_password = <value optimized out>
#1  0x00007fc6663b10f7 in purple_accounts_restore_current_statuses ()
   from /usr/lib/libpurple.so.0
No symbol table info available.
#2  0x000000000047dba4 in main (argc=1, argv=0x7fff72d17188) at gtkmain.c:862
	opt_help = <value optimized out>
	opt_login = 0
	opt_nologin = 0
	opt_version = <value optimized out>
	opt_si = 1
	opt_config_dir_arg = 0x0
	opt_login_arg = 0x0
	opt_session_arg = 0x0
	accounts = <value optimized out>
	sigset = {__val = {82951, 0 <repeats 15 times>}}
	prev_sig_disp = (void (*)(int)) 0
	errmsg = "q&#65533;vh&#65533;\177\000\000+\034&#65533;j&#65533;\177\000\000\000\000\000\000&#65533;\177\000\000&#65533;n&#65533;r&#65533;\177\000\000@o&#65533;r&#65533;\177\000\000\000\000\000\000\000\000\000\000\210\215%h&#65533;\177\000\000\b\000\000\000\000\000\000\000&#65533;&#65533;&#65533;j&#65533;\177\000\000&#65533;W&#65533;j&#65533;\177\000\000\00---Type <return> to continue, or q <return> to quit---q
Quit
(gdb) quit
The program is running.  Exit anyway? (y or n) y

```

This problem started in 2.5.5 so I upgraded (just now) to 2.5.6, and it's still occuring. Any ideas? Thanks!

---

### Post by LesterPalooza on 2009-05-22
Have you considered reinstalling Pidgin? And then see if you are still getting errors in the new 2.5.5. If no errors occur, then try upgrading to 2.5.6

---

### Post by Literati on 2009-05-22
No, that didn't work. But a dev responded to me, and apparently it was the Facebook Chat plugin that was causing the problem, so I removed it, and it started fine. :)

So then I installed the Facebook Protocol from source, and it's all working great again (And I'm up to 2.5.6 as a bonus :P)

---

