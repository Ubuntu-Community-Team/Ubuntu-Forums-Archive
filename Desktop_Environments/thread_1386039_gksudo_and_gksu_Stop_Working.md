---
title: "gksudo and gksu Stop Working"
date: 2010-01-20
forum: Desktop Environments
---

### Post by deejross on 2010-01-20
I am running a file server on Jaunty. It was a fresh install about a month ago and I have been having problems ever since. I connect external drives to the machine to do nightly backups. Lately, I have been using GParted (Gnome Partition Editor) to format the drives before using them as backups, as I keep a backup for every day of the week.

After using GParted a couple of times, it will stop working and I can't open it or any other application that needs root privileges. I can't use Gnome to mount drives anymore. I have to open Terminal and use the mount command to mount drives. Trying to start gparted or any other application, including nautilus from the Terminal using gksudo or gksu, I get the following error message:
```

gksudo nautilus
(nautilus:25353): nautilus-extension-gnome-mount-WARNING **: Cannot connect to system bus: org.freedesktop.DBus.Error.LimitsExceeded : The maximum number of active connections for UID 0 has been reached

(nautilus:25353): nautilus-extension-gnome-mount-WARNING **: Could not initialize hal context


** (nautilus:25353): WARNING **: Cannot connect to DBus The maximum number of active connections for UID 0 has been reached

process 25353: arguments to dbus_connection_send_with_reply_and_block() were incorrect, assertion "connection != NULL" failed in file dbus-connection.c line 3298.
This is normally a bug in some application using the D-Bus library.
process 25353: arguments to dbus_connection_remove_filter() were incorrect, assertion "connection != NULL" failed in file dbus-connection.c line 5309.
This is normally a bug in some application using the D-Bus library.
libhal.c 3126 : LibHalContext *ctx is NULL

```

I have Googled the error message about the DBus maximum number of connections, but I don't turn anything up other than one forum post from someone who says to issue a restart to DBus using ```
sudo /etc/init.d/dbus restart
``` but if I do that, Gnome logs me out and comes back up with several error messages, along with a HAL error. When that happens, I lose control of my mouse and keyboard and I'm forced to reboot the machine.

Once the machine is rebooted, everything works fine until I run a few more privileged applications, then the applications stop working again and this whole process starts all over. The only way to fix the problem so far is to reboot the machine, which is completely unacceptable.

Please help! Thank you.

---

### Post by deejross on 2010-01-20
bump

---

### Post by deejross on 2010-01-20
I hate to keep bumping, but this is a pretty serious problem

---

### Post by deejross on 2010-01-21
Still having trouble with this. Anyone have any ideas?

---

### Post by deejross on 2010-01-21
Another shameless bump

---

### Post by Jackzor on 2010-01-21
> **deejross said:**
> Another shameless bump

Well. I doubt you want to do this.. But.. Since no one else has anyideas.. Reinstall?   Or...

YOu could look though the package manager for something to reinstall.. I don't know anything about. I'm mostly posting to let you know that everyone isn't ignoring you. I hate that feeling.

---

### Post by jromer on 2010-01-21
I often times gksudo nautilus...this had stopped working. I get the follow message in the terminal...

seahorse nautilus module initialized
(nautilus:6165): GLib-GIO-CRITICAL **: g_simple_async_result_set_from_error: assertion `error != NULL' failed

(nautilus:6165): GLib-CRITICAL **: g_error_free: assertion `error != NULL' failed

(nautilus:6165): GLib-GIO-CRITICAL **: g_simple_async_result_set_from_error: assertion `error != NULL' failed

(nautilus:6165): GLib-GIO-WARNING **: (/build/buildd/glib2.0-2.16.6/gio/gfile.c:5249):IA__g_file_load_partial_contents_finish: runtime check failed: (g_simple_async_result_get_source_tag (simple) == g_file_load_contents_async)

---

### Post by deejross on 2010-01-25
jromer: I don't think your problem is related to mine in any way.

I am still fighting this problem and I'm running a file server on this machine (again, a brand new install). So reinstalling it won't fix the problem, as I have seen this on other Jaunty installations as well.

---

### Post by mindwarp on 2010-01-25
Ross,

Sorry about your troubles so far.  Under /etc/dbus-1/system.conf, there will be a line that says max_match_rules_per_connection.  Under Jaunty this was set pretty low, and for Karmic was actually increased from 512 to 5000 ([http://www.mail-archive.com/karmic-changes@lists.ubuntu.com/msg11414.html](http://www.mail-archive.com/karmic-changes@lists.ubuntu.com/msg11414.html)).  If you edit this value to 5000 and restart, you should have better luck.

You can paste the following into the bottom of the file:
```

  <!-- increase default match rules limit from 512 to 5000 because the
       aptdaemon needs relatively many per package in the queue -->
  <limit name="max_match_rules_per_connection">5000</limit>

```

Hope that helps,

Steve

---

### Post by deejross on 2010-01-25
I will give this a shot and let you know if I have any more problems. Thank you very much for your reply. I really do appreciate it.

---

### Post by luke_lukem on 2010-06-04
Hi everyone, i have a slightly different problem, but the thread's title fits the same:

When i launch an application that needs gksu, it simply hangs waiting for a gksu window that never shows up.
If i launch another administrative app, it hangs as well.
When i look at the process list, i get a lot of gksu instances, all sleeping.
if i kill those instances, the mentioned apps resume with an authentication error

Then, if i use a terminal and type sudo <app>, it hangs for a few seconds and then prompts for password and it works fine.

I don't know why it works so badly, but it needs to be fixed soon, many new users will surely find this very frustrating.

PD: i run ubuntu 10.04-64bit on a AMD-Athlon-x2

Cheers to all.

---

