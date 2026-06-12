---
title: "gksudo nautilus - Dead"
date: 2009-03-23
forum: General Help
---

### Post by jakupl on 2009-03-23
When I do ```
gksudo nautilus
``` It opens the "enter password" dialog, I enter my password and nothing happens.

This is what the terminal spews out when I do so.

```
jakup@bobby:~$ gksudo nautilus
Initializing nautilus-share extension

(nautilus:7852): GLib-GIO-CRITICAL **: g_simple_async_result_set_from_error: assertion `error != NULL' failed

(nautilus:7852): GLib-CRITICAL **: g_error_free: assertion `error != NULL' failed

(nautilus:7852): GLib-GIO-CRITICAL **: g_simple_async_result_set_from_error: assertion `error != NULL' failed

(nautilus:7852): GLib-GIO-WARNING **: (/build/buildd/glib2.0-2.16.6/gio/gfile.c:5249):IA__g_file_load_partial_contents_finish: runtime check failed: (g_simple_async_result_get_source_tag (simple) == g_file_load_contents_async)
jakup@bobby:~$ 

```

EDIT: this has not always been the case. It used to work well.

---

### Post by fooman on 2009-03-23
do you by any chance have a blank cd/dvd in the drive?

if so....remove it and see if the problem goes away.

---

### Post by jakupl on 2009-03-23
> **fooman said:**
> do you by any chance have a blank cd/dvd in the drive?

if so....remove it and see if the problem goes away.

YES! Wow. That is strange. I can't find this on launchpad. Should I file a bug report? This is reproducible.
This also seems very strange, as my cd drive does not even work.

---

### Post by fooman on 2009-03-23
> **jakupl said:**
> YES! Wow. That is strange. I can't find this on launchpad. Should I file a bug report? 

[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/310122](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/310122)

---

### Post by jakupl on 2009-03-23
> **fooman said:**
> [https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/310122](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/310122)

oh, well nice. THANKS for your help.

---

### Post by berong on 2009-03-23
i have an error also about nautilus...
it says something about "Nautius" and "corba" 
my desktop has my icons such as computer, my folder, and my removable drive, but my taskbar workspace are gone...
i can't click shutdown or anything...
if i open an icon, a dialog box will appear..
what could be the problem...?
i accidentally press CTRL - ALT F1, and i don't know 
what to do next..
i am a total newbie on ubuntu...
please help....

---

### Post by dcstar on 2009-03-25
> **berong said:**
> **i have an error also about nautilus...**
it says something about "Nautius" and "corba" 
........
i am a total newbie on ubuntu...
please help....

Do not hijack threads of one particular problem, start a new thread.

---

