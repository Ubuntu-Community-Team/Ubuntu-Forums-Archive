---
title: "Using different users on same desktop"
date: 2010-12-01
forum: Desktop Environments
---

### Post by blirp on 2010-12-01
In 10.04, I separated different roles with separate users on my desktop. For instance, I had multiple instances of Evolution running simultaneously for different mailboxes and purposes. There are legal reasons for keeping them separate, so adding all the mailboxes to Evolution is not an option. Using 'Switch User' IS an option, but a rather cumbersome one.

This setup worked nicely in 10.04. I opened a terminal window, and executed:
$ xhost +
$ su otheruser
$ cd
$ evolution &

In 10.10, this gives me:
----
$ evolution &
[1] 16029
otheruser@mymachine:~$ ** Message: couldn't connect to dbus session bus: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
**
GLib-GIO:ERROR:/build/buildd/glib2.0-2.26.0/gio/gdbusconnection.c:2270:initable_init: assertion failed: (connection->initialization_error == NULL)

[1]+  Aborted                 evolution
----

I get the same error for Firefox, but Opera works.

Is there anything I can do to fix this? A group 'otheruser' should be added to to allow the gdbusconnection to succeed?

M.

---

### Post by blirp on 2010-12-07
I can use

$ xhost +
$ gksudo -u otheruser gnome-terminal

This will open a terminal logged on as 'otheruser' after I type my own password. From this terminal, I can do whatever I like. It's also possible to start 'thunderbird' directly from the gksudo command.

M.

---

### Post by sisco311 on 2010-12-07
Instead of **xhost +** you should use:
```
xhost +SI:localuser:**otheruser**
```
to add only otheruser to the list of users allowed to connect to the X server.

and instead of **su otehruser** use:
```
su - otheruser
```
or
```
sudo -u otheruser -i
```

---

