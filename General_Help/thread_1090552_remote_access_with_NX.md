---
title: "remote access with NX"
date: 2009-03-08
forum: General Help
---

### Post by shahin on 2009-03-08
I installed NX on ubuntu 8.10.  When I run the client on my xp machine, I got an error about startkde not being in the path.  I found an article on nomachine's website about the error. They stated to add the absolute path.  But I noticed that I do not have a startkde file under /usr/bin.  I instead have a "start kdeinit" file.  Which I added to my node.config file so it looks like this:
....
....
#
# Specify path and name of the command to start the GNOME session.
#
CommandStartGnome="/usr/bin/dbus-launch --exit-with-session gnome-session"

#
# Specify path and name of the command to start the KDE session.
#
CommandStartKDE="/usr/bin/dbus-launch --exit-with-session startkdeinit"


now the client runs, and exits without even an error message.  I am gonna look in the logs more.  But if anyone knows how to fix this, please help.

---

### Post by shahin on 2009-03-08
Here is what is in the logs:
Mar  8 13:26:24 thunder NXSERVER-3.3.0-15[8805]: User 'sansari' from '1.1.1.1' logged out. 'NXLogin::reset'
Mar  8 13:26:24 thunder NXNODE-3.3.0-12[8886]: Using port '1010' on node 'thunder' for session 'unix-kde'. Logger::log nxnode 
6100
Mar  8 13:26:24 thunder NXNODE-3.3.0-12[8886]: Using host from available host list: '1.1.1.2'. Logger::log nxnode 6101
Mar  8 13:26:27 thunder NXNODE-3.3.0-12[8935]: ERROR: run command: process: 8946 finished with: 1 Logger::log nxnode 3854
Mar  8 13:26:30 thunder NXNODE-3.3.0-12[8886]: Session 'unix-kde' on port '1010' closed. Logger::log nxnode 6378
Mar  8 13:26:32 thunder NXSERVER-3.3.0-15[8930]: session sessionId:FCD2FCACBAEDD5F996527A31BBC1451B finished 'NXShell::handler
_session_start'
Mar  8 13:26:32 thunder NXSERVER-3.3.0-15[8930]: Session 'FCD2FCACBAEDD5F996527A31BBC1451B' closed by user 'sansari'. 'NXShell
::Static'

---

