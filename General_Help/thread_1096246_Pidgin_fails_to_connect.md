---
title: "Pidgin fails to connect"
date: 2009-03-14
forum: General Help
---

### Post by hwttdz on 2009-03-14
Pidgin seems to be unable to connect for the past couple (few?) days.  I don't even know where to start.  Can anyone give some advice.  

The output of pidgin -d:
```
(17:49:06) prefs: Reading /home/username/.purple/prefs.xml
(17:49:06) prefs: Finished reading /home/username/.purple/prefs.xml
(17:49:06) prefs: purple_prefs_get_string: /pidgin/browsers/command not a string pref
(17:49:06) dbus: okkk
(17:49:06) plugins: probing /usr/lib/pidgin/xmppconsole.so
<whole bunch of "plugins: probing X">
(17:49:06) plugins: /usr/lib/purple-2/libsametime.so has a prefs_info, but is a prpl. This is no longer supported.
(17:49:06) plugins: probing /usr/lib/purple-2/tcl.so
(17:49:07) plugins: probing /usr/lib/purple-2/libbonjour.so
(17:49:07) plugins: probing /usr/lib/purple-2/statenotify.so
(17:49:07) plugins: probing /usr/lib/purple-2/psychic.so
(17:49:07) plugins: probing /usr/lib/purple-2/liboscar.so
(17:49:07) plugins: /usr/lib/purple-2/liboscar.so is not usable because the 'purple_init_plugin' symbol could not be found.  Does the plugin call the PURPLE_INIT_PLUGIN() macro?
(17:49:07) plugins: probing /usr/lib/purple-2/libmyspace.so
(17:49:07) plugins: probing /usr/lib/purple-2/libyahoo.so
(17:49:07) plugins: probing /usr/lib/purple-2/ssl-nss.so
(17:49:07) plugins: probing /usr/lib/purple-2/log_reader.so
(17:49:07) plugins: probing /usr/lib/purple-2/libxmpp.so
(17:49:07) util: Reading file xmpp-caps.xml from directory /home/username/.purple
(17:49:07) util: File /home/username/.purple/xmpp-caps.xml does not exist (this is not necessarily an error)
(17:49:07) jabber: creating hash tables for data objects
(17:49:07) plugins: probing /usr/lib/purple-2/ssl.so
(17:49:07) plugins: probing /usr/lib/purple-2/dbus-example.so
(17:49:07) plugins: probing /usr/lib/purple-2/libgg.so
(17:49:07) plugins: probing /usr/lib/purple-2/buddynote.so
(17:49:07) plugins: probing /usr/lib/purple-2/libicq.so
(17:49:07) plugins: probing /usr/lib/purple-2/autoaccept.so
(17:49:07) plugins: probing /usr/lib/purple-2/newline.so
(17:49:07) plugins: probing /usr/lib/purple-2/libsilcpurple.so
(17:49:07) plugins: probing /usr/lib/purple-2/libjabber.so
(17:49:07) plugins: /usr/lib/purple-2/libjabber.so is not usable because the 'purple_init_plugin' symbol could not be found.  Does the plugin call the PURPLE_INIT_PLUGIN() macro?
(17:49:07) plugins: probing /usr/lib/purple-2/libaim.so
(17:49:07) plugins: probing /usr/lib/purple-2/libzephyr.so
(17:49:07) prefs: /purple/status/scores/offline changed, scheduling save.
(17:49:07) prefs: /purple/status/scores/available changed, scheduling save.
(17:49:07) prefs: /purple/status/scores/invisible changed, scheduling save.
(17:49:07) prefs: /purple/status/scores/away changed, scheduling save.
(17:49:07) prefs: /purple/status/scores/extended_away changed, scheduling save.
(17:49:07) prefs: /purple/status/scores/idle changed, scheduling save.
(17:49:07) prefs: /purple/status/scores/offline_msg changed, scheduling save.
(17:49:07) util: Reading file accounts.xml from directory /home/username/.purple
(17:49:07) util: Reading file status.xml from directory /home/username/.purple
(17:49:07) certificate: CertificateVerifier x509, singleuse requested but not found.
(17:49:07) certificate: CertificateVerifier singleuse registered
(17:49:07) certificate: CertificatePool x509, ca requested but not found.
(17:49:07) certificate: CertificateScheme x509 requested but not found.
(17:49:07) certificate/x509/ca: Lazy init failed because an X.509 Scheme is not yet registered. Maybe it will be better later.
(17:49:07) certificate/x509/ca: Init failed, probably because a dependency is not yet registered. It has been deferred to later.
(17:49:07) certificate: CertificatePool ca registered
(17:49:07) certificate: CertificatePool x509, tls_peers requested but not found.
(17:49:07) certificate: CertificatePool tls_peers registered
(17:49:07) certificate: CertificateVerifier x509, tls_cached requested but not found.
(17:49:07) certificate: CertificateVerifier tls_cached registered
(17:49:07) prefs: /purple/logging/format changed, scheduling save.
(17:49:07) prefs: /purple/logging/format changed, scheduling save.
(17:49:07) prefs: /purple/proxy/type changed, scheduling save.
(17:49:07) prefs: /purple/proxy/host changed, scheduling save.
(17:49:07) prefs: /purple/proxy/port changed, scheduling save.
(17:49:07) prefs: /purple/proxy/username changed, scheduling save.
(17:49:07) prefs: /purple/proxy/password changed, scheduling save.
(17:49:07) certificate: CertificateScheme x509 requested but not found.
(17:49:07) certificate: CertificateScheme x509 registered
(17:49:07) util: Reading file smileys.xml from directory /home/username/.purple
(17:49:07) util: File /home/username/.purple/smileys.xml does not exist (this is not necessarily an error)
(17:49:07) stun: using server 
(17:49:07) sound: Initializing sound output drivers.
(17:49:07) prefs: /pidgin/conversations/placement changed, scheduling save.
(17:49:07) gtkblist: added visibility manager: 1
(17:49:07) docklet: created
(17:49:07) util: Reading file blist.xml from directory /home/username/.purple
(17:49:07) plugins: Loading saved plugin /usr/lib/pidgin/history.so
(17:49:07) plugins: Loading saved plugin /usr/lib/pidgin/notify.so
(17:49:07) plugins: Loading saved plugin /usr/lib/purple-2/ssl-nss.so
(17:49:07) plugins: Loading saved plugin /usr/lib/pidgin/nautilus.so
(17:49:07) nautilus: saved blist online
(17:49:07) plugins: Loading saved plugin /usr/lib/purple-2/ssl.so
(17:49:07) pounce: Creating pounce: gtk-gaim, username
(17:49:07) ui_main: Failed to load the default window icon (scalablepx version)!
(17:49:07) Session Management: ICE initialized.
(17:49:07) Session Management: Connecting with no previous ID
(17:49:07) Session Management: Handling new ICE connection... 
(17:49:07) done.
(17:49:07) Session Management: Connected to manager (gnome-session) with client ID 10800510d82619eb85123706734783807600000131020278
(17:49:07) Session Management: Using pidgin as command
(17:49:08) dbus: Need to register an object with the dbus subsystem. (If you are not a developer, please ignore this message.)
(17:49:08) dbus: The signal "gtkblist-hiding" caused some dbus error. (If you are not a developer, please ignore this message.)
(17:49:08) account: Connecting to account phoenics29
(17:49:08) connection: Connecting. gc = 0x2583050
(17:49:08) oscar: registered module misc (family 0xffff, version = 0x0000, tool 0x0000, tool version 0x0000)
(17:49:08) oscar: registered module oservice (family 0x0001, version = 0x0003, tool 0x0110, tool version 0x0629)
(17:49:08) oscar: registered module locate (family 0x0002, version = 0x0001, tool 0x0110, tool version 0x0629)
(17:49:08) oscar: registered module buddy (family 0x0003, version = 0x0001, tool 0x0110, tool version 0x0629)
(17:49:08) oscar: registered module messaging (family 0x0004, version = 0x0001, tool 0x0110, tool version 0x0629)
(17:49:08) oscar: registered module admin (family 0x0007, version = 0x0001, tool 0x0010, tool version 0x0629)
(17:49:08) oscar: registered module popup (family 0x0008, version = 0x0001, tool 0x0104, tool version 0x0001)
(17:49:08) oscar: registered module bos (family 0x0009, version = 0x0001, tool 0x0110, tool version 0x0629)
(17:49:08) oscar: registered module userlookup (family 0x000a, version = 0x0001, tool 0x0110, tool version 0x0629)
(17:49:08) oscar: registered module stats (family 0x000b, version = 0x0001, tool 0x0104, tool version 0x0001)
(17:49:08) oscar: registered module chatnav (family 0x000d, version = 0x0001, tool 0x0010, tool version 0x0629)
(17:49:08) oscar: registered module chat (family 0x000e, version = 0x0001, tool 0x0010, tool version 0x0629)
(17:49:08) oscar: registered module odir (family 0x000f, version = 0x0001, tool 0x0010, tool version 0x0629)
(17:49:08) oscar: registered module bart (family 0x0010, version = 0x0001, tool 0x0010, tool version 0x0629)
(17:49:08) oscar: registered module feedbag (family 0x0013, version = 0x0004, tool 0x0110, tool version 0x0629)
(17:49:08) oscar: registered module icq (family 0x0015, version = 0x0001, tool 0x0110, tool version 0x047c)
(17:49:08) oscar: registered module auth (family 0x0017, version = 0x0000, tool 0x0000, tool version 0x0000)
(17:49:08) oscar: registered module alert (family 0x0018, version = 0x0001, tool 0x0010, tool version 0x0629)
(17:49:08) oscar: Adding handler for ffff/0003
<whole bunch of adding handler messages>
(17:49:08) oscar: oscar_login: gc = 0x2583050
(17:49:08) dns: DNS query for 'login.messaging.aol.com' queued
(17:49:08) Session Management: Received first save_yourself
(17:49:08) dns: Created new DNS child 7628, there are now 1 children.
(17:49:08) dns: Successfully sent DNS request to child 7628
(17:49:08) Session Management: Received save_complete
(17:49:08) docklet: embedded
(17:49:08) dns: Got response for 'login.messaging.aol.com'
(17:49:08) dnsquery: IP resolved for login.messaging.aol.com
(17:49:08) proxy: Attempting connection to 205.188.251.43
(17:49:08) proxy: Connecting to login.messaging.aol.com:5190 with no proxy
(17:49:08) proxy: Connection in progress
(17:49:13) util: Writing file prefs.xml to directory /home/username/.purple
(17:49:13) util: Writing file /home/username/.purple/prefs.xml
(17:49:13) util: Writing file accounts.xml to directory /home/username/.purple
(17:49:13) util: Writing file /home/username/.purple/accounts.xml
(17:49:13) util: Writing file blist.xml to directory /home/username/.purple
(17:49:13) util: Writing file /home/username/.purple/blist.xml
(17:49:13) util: Writing file pounces.xml to directory /home/username/.purple
(17:49:13) util: Writing file /home/username/.purple/pounces.xml
dns[7628]: nobody needs me... =(
```

---

### Post by Tibuda on 2009-03-14
What network are you trying to connect?

---

### Post by hwttdz on 2009-03-14
Trying to connect to the AIM network through login.messaging.aol.com, also tried login.oscar.aol.com or somesuch. It seems to be resolving the name correctly though.

---

### Post by hwttdz on 2009-03-17
Connection is intermittent.  Any suggestions?

---

### Post by hwttdz on 2009-03-20
Still looking for help?

---

### Post by hwttdz on 2009-03-23
Still looking for help.

---

### Post by khc on 2009-03-27
what's the error that you get?

---

