---
title: "GAIM and Synaptic issues"
date: 2006-09-10
forum: Desktop Environments
---

### Post by ldc_1 on 2006-09-10
Hello All

I am running the latest download of ubuntu. I setup GAIM and it worked for a week or so, now it will not connect, see screenshot below.  I can connect on all Windows systems in my house, my two ubuntu
systems refuse to connect as far as GAIM goes. I have rebooted the systems, I have tried to remove and re-install GAIM, rebooted my network nothing works. While doing this I ran into issues with synaptic, it refuses to make the needed connection to load other packages, trying to load jabber to use in place of GAIM. I have pasted the error messages below that I get in synaptic. FYI, at this time Firefox can get to pages with no problems, so my network is up and running.

I am new to Linux so I will admit my knowledge is limited.  My reason for loading ubuntu was to have some systems for kids to use. They thought that it was cool that ubuntu built the system with only minor problems. They were using GAIM for a week or so with no problem when it just stopped working. We had problems with Firefox after it had run for several days out of the box with no problems. In the case of Firefox I turned on IPV6 (blank:config) and adjusted the MTU to 1475, that seemed to fix the problems.

Any suggestions will be appreciated.

-ldc-








Synaptic errors

[http://us.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg:](http://us.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg:) Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
[http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg:](http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg:) Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
[http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/Release.gpg:](http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/Release.gpg:) Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed ou



Debug outbut from Gaim:
larry@Dads-Ubuntu:~$ gaim -d
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
plugins: /usr/lib/gaim/libzephyr.so is unloadable: libzephyr.so.3: cannot open shared object file: No such file or directory
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
plugins: probing /home/larry/.gaim/icons
plugins: probing /home/larry/.gaim/accounts.xml
plugins: probing /home/larry/.gaim/blist.xml
plugins: probing /home/larry/.gaim/accels
plugins: probing /home/larry/.gaim/prefs.xml
plugins: probing /home/larry/.gaim/smileys
plugins: registering plugin-load signal
plugins: registering plugin-unload signal
blist import: Reading /home/larry/.gaim/blist.xml
blist import: Finished reading /home/larry/.gaim/blist.xml
prefs: Reading /home/larry/.gaim/prefs.xml
prefs: Finished reading /home/larry/.gaim/prefs.xml
plugins: Loading saved plugin /usr/lib/gaim/docklet.so
tray icon: plugin loaded
tray icon: created
plugins: Loading saved plugin /usr/lib/gaim/notify.so
plugins: Loading saved plugin /usr/lib/gaim/autorecon.so
plugins: Loading saved plugin /usr/lib/gaim/relnot.so
pounces: Error reading pounces: Failed to open file '/home/larry/.gaim/pounces.xml': No such file or directory
status: Error reading statuses: Failed to open file '/home/larry/.gaim/status.xml': No such file or directory
Session Management: ICE initialized.
Session Management: Connecting with no previous ID
Session Management: Handling new ICE connection... done.
Session Management: Connected to manager (GnomeSM) with client ID 117f000001000115793546900000046910093
Session Management: Using gaim as command
account: Connecting to account 0x81fa430. gc = 0x82079e0
connection: Connecting. gc = 0x82079e0
connection: Calling serv_login
server: gaim 1.5.1cvs logging in CrosbyDad02 using AIM/ICQ
oscar: oscar_login: gc = 0x82079e0
proxy: No environment settings found, not using a proxy
dns: Created new DNS child 19418, there are now 1 children.
Session Management: Received first save_yourself
dns: Host 'login.oscar.aol.com' resolved
proxy: Connecting to login.oscar.aol.com:5190 with no proxy
proxy: Connect would have blocked.
Session Management: Received save_complete
tray icon: embedded
accounts: Writing accounts to disk.
dns[19418]: nobody needs me... =(
proxy: Connected.
proxy: getsockopt SO_ERROR check: Connection timed out
account: Disconnecting account 0x81fa430
connection: Disconnecting connection 0x82079e0
oscar: Signed off.
blist: Destroying
connection: Destroying connection 0x82079e0
accounts: Writing accounts to disk.
autorecon: do_signon called
autorecon: calling gaim_account_connect
account: Connecting to account 0x81fa430. gc = 0x8471aa0
connection: Connecting. gc = 0x8471aa0
connection: Calling serv_login
server: gaim 1.5.1cvs logging in CrosbyDad02 using AIM/ICQ
oscar: oscar_login: gc = 0x8471aa0
dns: DNS child 19418 no longer exists
dns: Created new DNS child 19585, there are now 1 children.
autorecon: done calling gaim_account_connect
dns: Host 'login.oscar.aol.com' resolved
proxy: Connecting to login.oscar.aol.com:5190 with no proxy
proxy: Connect would have blocked.
account: Disconnecting account 0x81fa430
connection: Disconnecting connection 0x8471aa0
oscar: Signed off.
blist: Destroying
connection: Destroying connection 0x8471aa0

---

### Post by hawko on 2006-09-10
Could your MSN issues be related to the article at the top of this page [http://gaim.sourceforge.net/](http://gaim.sourceforge.net/) ??

Try installing Gaim 2beta3.1 and see if that helps you. That is probably the end of my assistance!

---

