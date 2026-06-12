---
title: "HELP!  Major Problem With Backup Software"
date: 2009-02-25
forum: General Help
---

### Post by ram2008 on 2009-02-25
For some reason I can't get either of my backup programs (Simple Backup & Pybackpack) to work.  I've used Simple Backup with no problems in the past.  Pybackpack is a new program I just downloaded a couple of days ago.  If I do system>administration>simple-backup, the program's gui flashes on the screen for a fraction of a second and then nothing.  Same thing when I try to run pybackpack.  So I tried running both programs from a terminal and I get the following error messages in the terminal:

For Simple Backup:

(simple-backup-config:13194): GLib-GIO-CRITICAL **: g_simple_async_result_set_from_error: assertion `error != NULL' failed
/usr/sbin/simple-backup-config:1002: Warning: g_error_free: assertion `error != NULL' failed
  gtk.main()

(simple-backup-config:13194): GLib-GIO-CRITICAL **: g_simple_async_result_set_from_error: assertion `error != NULL' failed

(simple-backup-config:13194): GLib-GIO-WARNING **: (/build/buildd/glib2.0-2.16.6/gio/gfile.c:5249):IA__g_file_load_partial_contents_finish: runtime check failed: (g_simple_async_result_get_source_tag (simple) == g_file_load_contents_async)
Segmentation fault


For Pybackpack:

(pybackpack:12636): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

(pybackpack:12636): GLib-GIO-CRITICAL **: g_simple_async_result_set_from_error: assertion `error != NULL' failed
/var/lib/python-support/python2.5/pybackpack/backuptool.py:61: Warning: g_error_free: assertion `error != NULL' failed
  gtk.main()

(pybackpack:12636): GLib-GIO-CRITICAL **: g_simple_async_result_set_from_error: assertion `error != NULL' failed

(pybackpack:12636): GLib-GIO-WARNING **: (/build/buildd/glib2.0-2.16.6/gio/gfile.c:5249):IA__g_file_load_partial_contents_finish: runtime check failed: (g_simple_async_result_get_source_tag (simple) == g_file_load_contents_async)
Segmentation fault

When I first installed Pybackpack it would create the backup and the CD image but would not allow me to burn the CD suggesting that I didn't have permission.  Here's the actual error message: "An error occurred while setting up the temporary CD image directory '/tmp/pybackpack.cdimage/'.  Please ensure you have write access to this location."  In Users and Groups I have permission to use the CD drive.  I did notice that root is the owner of that device.  Should that be the case?  I tried to use the chown command to change that but it didn't work.

Any help will be much appreciated.  I'm just about ready to give up on Ubuntu.  It seems there just one problem  after the other.

---

