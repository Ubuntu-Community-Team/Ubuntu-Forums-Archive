---
title: "Error Starting Up Kile in 8.10"
date: 2009-02-28
forum: General Help
---

### Post by Dahaka14 on 2009-02-28
I have never had this problem before, until I reformatted last week in 8.10.  When trying to run Kile 2.0, an error message came up about "dcopserver" not running, so I ran it under the terminal.  Then, I tried to run Kile again, and it gave me the message "Malformed URL file:///home/(username)."  I've searched for help on this and can't find it.  Can someone please help me?

---

### Post by Dahaka14 on 2009-03-07
I hate to be a bugger, but is there really nobody that can help me with this problem?  I figured out a way around it, and maybe it will give a clue to the Ubuntu gurus: I can start Kile fine using "sudo kile," but this creates a problem because then all of my files created under Kile have root only permissions.

To give you some more ideas, I tried running Kile from the terminal and got "There was an error setting up inter-process communications for KDE.  The message in the terminal was:

Session management error: None of the authentication protocols specified are supported
trying to create local folder /home/peter/.kde/share: Permission denied
trying to create local folder /home/peter/.kde/share: Permission denied
trying to create local folder /home/peter/.kde/share: Permission denied
trying to create local folder /home/peter/.kde/share: Permission denied
trying to create local folder /home/peter/.kde/share: Permission denied
trying to create local folder /home/peter/.kde/share: Permission denied
trying to create local folder /home/peter/.kde/share: Permission denied
trying to create local folder /home/peter/.kde/share: Permission denied
trying to create local folder /home/peter/.kde/share: Permission denied
trying to create local folder /home/peter/.kde/tmp-peter-laptop: Permission denied
trying to create local folder /home/peter/.kde/share: Permission denied
trying to create local folder /home/peter/.kde/share: Permission denied
trying to create local folder /home/peter/.kde/share: Permission denied
trying to create local folder /home/peter/.kde/share: Permission denied
trying to create local folder /home/peter/.kde/share: Permission denied
trying to create local folder /home/peter/.kde/socket-peter-laptop: Permission denied
trying to create local folder /home/peter/.kde/socket-peter-laptop: Permission denied
kdeinit: Aborting. No write access to '/home/peter/.ICEauthority'.
trying to create local folder /home/peter/.kde/share: Permission denied
trying to create local folder /home/peter/.kde/share: Permission denied
trying to create local folder /home/peter/.kde/share: Permission denied
trying to create local folder /home/peter/.kde/share: Permission denied
trying to create local folder /home/peter/.kde/share: Permission denied
trying to create local folder /home/peter/.kde/share: Permission denied
trying to create local folder /home/peter/.kde/cache-peter-laptop: Permission denied
trying to create local folder /home/peter/.kde/cache-peter-laptop: Permission denied
trying to create local folder /home/peter/.kde/share: Permission denied
trying to create local folder /home/peter/.kde/share: Permission denied
trying to create local folder /home/peter/.kde/share: Permission denied
trying to create local folder /home/peter/.kde/tmp-peter-laptop: Permission denied
trying to create local folder /home/peter/.kde/share: Permission denied
trying to create local folder /home/peter/.kde/share: Permission denied
trying to create local folder /home/peter/.kde/share: Permission denied
trying to create local folder /home/peter/.kde/socket-peter-laptop: Permission denied
trying to create local folder /home/peter/.kde/socket-peter-laptop: Permission denied
kdeinit: Aborting. No write access to '/home/peter/.ICEauthority'.
trying to create local folder /home/peter/.kde/cache-peter-laptop: Permission denied

and the message returned returned by the system was (in a window):

Could not read network connection list.
/home/(user)/.DCOPSERVER_(local-host)_0

Please check that the "dcopserver" program is running!

So then I tried to run dcopserver in the terminal and got:

/usr/bin/iceauth:  /home/peter/.ICEauthority not writable, changes will be ignored
DCOPClient::attachInternal. Attach failed Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
ICE Connection rejected!

DCOPClient::attachInternal. Attach failed Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
DCOPServer self-test failed.
ICE Connection rejected!


Can someone PLEASE help me fix Kile?  I've tried uninstalling and reinstalling many times.

---

### Post by taps on 2009-04-01
I have the same problem. Intrepid, Gnome.

I created a new user with admin privileges on my machine. Kile runs fine when I'm logged in as the original user. When logged in as the new user, I can only run Kile as sudo. Tried a couple of solutions offered, but to no avail.

I can start dcopserver manually and get past the first hurdle (what a tedious waste of time!), but get the "malformed url" message.

Surely someone here has some ideas!

EDIT:
Here's the error message from terminal:
```

DCOPClient::attachInternal. Attach failed Could not open network socket
DCOPClient::attachInternal. Attach failed Could not open network socket
DCOPClient::attachInternal. Attach failed Could not open network socket
---------------------------------
It looks like dcopserver is already running. If you are sure
that it is not already running, remove /home/tapani/.DCOPserver_simojoki-desktop__0
and start dcopserver again.
---------------------------------

DCOPClient::attachInternal. Attach failed Could not open network socket
DCOPClient::attachInternal. Attach failed Could not open network socket
kdeinit: Communication error with launcher. Exiting!
DCOPClient::attachInternal. Attach failed Could not open network socket
DCOPClient::attachInternal. Attach failed Could not open network socket
DCOPClient::attachInternal. Attach failed Could not open network socket
DCOPClient::attachInternal. Attach failed Could not open network socket
DCOPClient::attachInternal. Attach failed Could not open network socket
---------------------------------
It looks like dcopserver is already running. If you are sure
that it is not already running, remove /home/tapani/.DCOPserver_simojoki-desktop__0
and start dcopserver again.
---------------------------------

DCOPClient::attachInternal. Attach failed Could not open network socket
DCOPClient::attachInternal. Attach failed Could not open network socket
kdeinit: Communication error with launcher. Exiting!
DCOPClient::attachInternal. Attach failed Could not open network socket
DCOPClient::attachInternal. Attach failed Could not open network socket
KCrash: Application 'kile' crashing...
Warning: connect() failed: : Connection refused
KCrash cannot reach kdeinit, launching directly.

```

---

### Post by taps on 2009-04-01
Ah ... too quick to complain. :redface:

I changed the permissions on the .kde folder and its subfolders (they were set to root for some reason).

I then deleted the file /home/tapani/.DCOPserver_simojoki-desktop__0

Now Kile starts beautifully.

---

