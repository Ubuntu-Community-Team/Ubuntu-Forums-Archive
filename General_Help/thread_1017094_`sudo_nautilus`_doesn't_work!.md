---
title: "`sudo nautilus` doesn't work!"
date: 2008-12-20
forum: General Help
---

### Post by deltaromeo on 2008-12-20
`sudo gedit` works fine, see below for what happens when I try running sudo nautilus:

```
jade@homepc:~$ sudo nautilus
Initializing nautilus-share extension
seahorse nautilus module initialized

(nautilus:7328): GLib-GIO-CRITICAL **: g_simple_async_result_set_from_error: assertion `error != NULL' failed

(nautilus:7328): GLib-CRITICAL **: g_error_free: assertion `error != NULL' failed

(nautilus:7328): GLib-GIO-CRITICAL **: g_simple_async_result_set_from_error: assertion `error != NULL' failed

(nautilus:7328): GLib-GIO-WARNING **: (/build/buildd/glib2.0-2.16.6/gio/gfile.c:5249):IA__g_file_load_partial_contents_finish: runtime check failed: (g_simple_async_result_get_source_tag (simple) == g_file_load_contents_async)
Segmentation fault
jade@homepc:~$ 

```

can anyone help please?

---

### Post by oldos2er on 2008-12-20
When calling graphical programs in Gnome, use "gksu" instead of "sudo." I doubt if this will solve your problem tho'.

---

### Post by deltaromeo on 2008-12-20
Thanks for that, you're right though, it didn't help.  I got a graphical password prompt but no nautilus appeared, just the same output in the terminal as I posted originally.

Anyone else please?

---

### Post by jms1989 on 2009-01-16
I have this problem too. I even tried deleting all of root's files and directories but no avail.

---

### Post by Indyviews on 2009-01-16
I am just a newbie but I have no trouble with gksudo nautilus

---

### Post by mc4man on 2009-01-16
> I have this problem too. 

By far the most common cause of gksudo nautilus segfaulting is having blank media in a cd/dvd drive


> I even tried deleting all of root's files and directories but no avail
I would hope you failed at that...

---

### Post by Arup on 2009-01-17
sudo apt-get install nautilus-gksu

This will give you the ability to open any folder with root privilege, the convenience of Windows with protection of Linux.

---

### Post by jms1989 on 2009-01-18
> **mc4man said:**
> By far the most common cause of gksudo nautilus segfaulting is having blank media in a cd/dvd drive


Well, that explains my problem. Never realized it until now. Would it fail if you had a disk with data inserted?

---

### Post by Yashiro on 2009-02-21
You can sometimes fix this by closing and restarting the bonobo activation process.

Another odd fix is to remove any cdroms from your drives as mentioned above.

Or try gksudo dbus-launch nautilus.

---

