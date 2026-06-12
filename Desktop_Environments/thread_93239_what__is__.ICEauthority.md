---
title: "what _is_ .ICEauthority"
date: 2005-11-21
forum: Desktop Environments
---

### Post by steve.horsley on 2005-11-21
I have been suffering occasional problems with gnome crashing on login. I have finally nailed it down to the file ~/.ICEauthority. Deleting this file allows gnome to start again. I suspect the proble may start when I use an X application tunnelled over SSH (e.g. from work), but haven't proved that conclusively yet.

What IS this nasty little file, and what creates it? 

Steve

---

### Post by GeneralZod on 2005-11-21
You know, it's bafflingly hard to find any details about this.  From trawling the web, I gather that it is created by X and acts (as you may have guessed :)) as a security feature that is part of an Access Control List mechanism for controlling access to the X-server.  It *should* always be owned by your user, but occasionally ends up being owned by root at which point you will be unable to log in to X until you delete it or make it writable by your user account.

I've heard some people say that starting K3B as root (e.g. via sudo) can cause this to happen, but I've never tried this myself.

---

### Post by TLE on 2005-11-21
I don't have much extra information about the particular file, but the error is registered as a bug. Perhaps you can find additional information in the bugtracker.
[http://bugzilla.ubuntu.com/show_bug.cgi?id=2053]("http://bugzilla.ubuntu.com/show_bug.cgi?id=2053")

---

### Post by steve.horsley on 2005-11-21
[QUOTE=TLE]I don't have much extra information about the particular file, but the error is registered as a bug. Perhaps you can find additional information in the bugtracker.
[http://bugzilla.ubuntu.com/show_bug.cgi?id=2053]("http://bugzilla.ubuntu.com/show_bug.cgi?id=2053")[/QUOTE]

Nice link, thanks. But I don't recall using any KDE progs under sudo recently.

Steve

---

### Post by janrinok on 2005-11-22
I have found that if I start X as sudo while in this directory, it creates the file with root as the owner.  If I SSH from another machine into the user account via 'ssh -X machinename', and then start a program running under gnome it can also create the file with a different user as the file owner.  Both cause the same problem.  The only solution that I have found is to change the /root directory before starting any programs using sudo.  So, as an example, if you wanted to change a configuration file using gedit while logged on to your machine via ssh, the following ensures that the file is not corrupted:

cd /root
sudo gedit filetobeedited

---

### Post by steve.horsley on 2005-11-22
[QUOTE=janrinok]I have found that if I start X as sudo while in this directory, it creates the file with root as the owner.  If I SSH from another machine into the user account via 'ssh -X machinename', and then start a program running under gnome it can also create the file with a different user as the file owner.  Both cause the same problem.  The only solution that I have found is to change the /root directory before starting any programs using sudo.  So, as an example, if you wanted to change a configuration file using gedit while logged on to your machine via ssh, the following ensures that the file is not corrupted:

cd /root
sudo gedit filetobeedited[/QUOTE]

That's almost certainly what happened. I'll change directory first next time. Thanks.

Steve

---

### Post by ed_d on 2005-11-22
Also, instead of deleting it everytime, just chown username:username ~/.ICEauthority

---

