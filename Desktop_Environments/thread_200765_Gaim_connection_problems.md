---
title: "Gaim connection problems"
date: 2006-06-20
forum: Desktop Environments
---

### Post by Schroeder on 2006-06-20
Hi there,

I have some connection trouble with Gaim (latest version according to apt-get). I have a clean system (just installed a couple of hours ago) and everything works so far. I have internet connection (after disabling IPv6) but Gaim wont connect to any network (ICQ, MSN, IRC). Using the default settings in MSN it stays in the Connecting stage. Using HTTP mode it goes to Handshakign but hangs there. ICQ stays in Connecting as does IRC. 

I just installed Kopete and everything works fine there. No connection problems. 

Does anybody know what the problem is?

Thanks,
Chris

---

### Post by tehwa on 2006-06-20
Have a crack at starting GAIM from the command line with ```
gaim -d
```
Check the output to see where it is stalling. It's a bit of a mess, but it may offer some insight.

---

### Post by Schroeder on 2006-06-21
Here's the output of 'gaim -d':

sound: Initializing sound output drivers.
plugins: registering plugin-load signal
plugins: registering plugin-unload signal
plugins: probing /usr/lib/gaim/autorecon.so
plugins: probing /usr/lib/gaim/docklet.so
plugins: probing /usr/lib/gaim/extplacement.so
plugins: probing /usr/lib/gaim/gaim-remote.so
plugins: probing /usr/lib/gaim/gestures.so
plugins: probing /usr/lib/gaim/gevolution.so
plugins: probing /usr/lib/gaim/history.so
plugins: probing /usr/lib/gaim/iconaway.so
plugins: probing /usr/lib/gaim/idle.so
plugins: probing /usr/lib/gaim/libgg.so
plugins: probing /usr/lib/gaim/libirc.so
plugins: probing /usr/lib/gaim/libjabber.so
plugins: probing /usr/lib/gaim/libmsn.so
plugins: probing /usr/lib/gaim/libnapster.so
plugins: probing /usr/lib/gaim/libnovell.so
plugins: probing /usr/lib/gaim/liboscar.so
plugins: probing /usr/lib/gaim/nautilus.so
plugins: probing /usr/lib/gaim/libyahoo.so
plugins: probing /usr/lib/gaim/libzephyr.so
plugins: probing /usr/lib/gaim/notify.so
plugins: probing /usr/lib/gaim/relnot.so
plugins: probing /usr/lib/gaim/spellchk.so
plugins: probing /usr/lib/gaim/ssl-gnutls.so
plugins: probing /usr/lib/gaim/ssl-nss.so
plugins: probing /usr/lib/gaim/ssl.so
plugins: probing /usr/lib/gaim/statenotify.so
plugins: probing /usr/lib/gaim/tcl.so
plugins: probing /usr/lib/gaim/ticker.so
plugins: probing /usr/lib/gaim/timestamp.so
plugins: probing /home/schroeder/.gaim/accounts.xml
plugins: registering plugin-load signal
plugins: registering plugin-unload signal
prefs: Reading /home/schroeder/.gaim/prefs.xml
prefs: Reading /etc/gaim/prefs.xml
prefs: Finished reading /etc/gaim/prefs.xml
plugins: Loading saved plugin /usr/lib/gaim/docklet.so
tray icon: plugin loaded
tray icon: created
plugins: Loading saved plugin /usr/lib/gaim/notify.so
pounces: Error reading pounces: Failed to open file '/home/schroeder/.gaim/pounces.xml': No such file or directory
status: Error reading statuses: Failed to open file '/home/schroeder/.gaim/status.xml': No such file or directory
Session Management: ICE initialized.
Session Management: Connecting with no previous ID
Session Management: Handling new ICE connection... done.
Session Management: Connected to manager (GnomeSM) with client ID 117f000001000115091147900000101170016
Session Management: Using gaim as command
Session Management: Received first save_yourself
Session Management: Received save_complete
tray icon: embedded
accounts: Writing accounts to disk.
account: Connecting to account 0x817f1a0. gc = 0x8418858
connection: Connecting. gc = 0x8418858
connection: Calling serv_login
server: gaim 1.5.1cvs logging in 32244291 using AIM/ICQ
oscar: oscar_login: gc = 0x8418858
dns: Created new DNS child 11741, there are now 1 children.
dns: Host 'login.oscar.aol.com' resolved
proxy: Connecting to login.oscar.aol.com:5190 with no proxy
proxy: Connect would have blocked.
accounts: Writing accounts to disk.
dns[11741]: nobody needs me... =(

It is stuck in connecting state (for ICQ in this case). Same for MSN.

Any idea whats wrong? I just deinstalled gaim and installed it again. Same behaviour. Do I need any other packages for gaim to work?

Thanks,
Chris

---

### Post by Schroeder on 2006-06-21
I finally figured out what was wrong! :cool: 

My resolve.conf contained 192.168.0.1 as a first entry which caused problems for gaim resolving the servers address. I deleted the entry and...gaim works like a charm. :rolleyes: 

Thanks anyway,
Chris

---

