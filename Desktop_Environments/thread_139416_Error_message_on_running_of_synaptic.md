---
title: "Error message on running of synaptic"
date: 2006-03-04
forum: Desktop Environments
---

### Post by mayankgarg1 on 2006-03-04
Hi friends
I am getting following error message while running synaptic through terminal

mayank@ubuntu:~$ gksudo synaptic

(gksudo:10081): Gdk-WARNING **: locale not supported by Xlib

(gksudo:10081): Gdk-WARNING **: cannot set locale modifiers

(synaptic:10083): Gdk-WARNING **: locale not supported by Xlib

(synaptic:10083): Gdk-WARNING **: cannot set locale modifiers

(synaptic:10083): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed

(synaptic:10083): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed

how can i solve this problem
Please help

---

### Post by hegenious on 2006-03-04
try using sudo instead of gksudo

it will show something like:

(synaptic:18017): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed

(synaptic:18017): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed

I think those can be safely ignored

---

