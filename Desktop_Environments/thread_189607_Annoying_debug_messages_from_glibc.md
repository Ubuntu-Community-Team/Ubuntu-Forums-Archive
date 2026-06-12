---
title: "Annoying debug messages from glibc"
date: 2006-06-05
forum: Desktop Environments
---

### Post by mdh on 2006-06-05
Hi all,

I upgraded to dapper from breezy a couple of days ago and ever since the upgrade, I see these messages on the console when I open apps like gvim, gimp, synaptic and some others.

(gimp:6751): GLib-CRITICAL **: g_key_file_add_group: assertion `g_key_file_lookup_group_node (key_file, group_name) == NULL' failed

(gimp:6751): GLib-CRITICAL **: g_key_file_add_group: assertion `g_key_file_lookup_group_node (key_file, group_name) == NULL' failed

(gimp:6751): GLib-CRITICAL **: g_key_file_add_group: assertion `g_key_file_lookup_group_node (key_file, group_name) == NULL' failed

(gimp:6751): GLib-CRITICAL **: g_key_file_add_group: assertion `g_key_file_lookup_group_node (key_file, group_name) == NULL' failed

(gimp:6751): GLib-CRITICAL **: g_key_file_add_group: assertion `g_key_file_lookup_group_node (key_file, group_name) == NULL' failed

Any thoughts on what has gone wrong ?

P.S.
Also, when I do gimp >> /dev/null, I still see these messages. Does Anyone know why is the redirection not working ?. I faintly remember reading somewhere that '>' redirects stdout output and '>>' redirects stderr output

---

