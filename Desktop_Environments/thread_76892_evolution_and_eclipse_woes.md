---
title: "evolution and eclipse woes"
date: 2005-10-15
forum: Desktop Environments
---

### Post by felly on 2005-10-15
i recently upgraded to breezy from hoary (via apt-get dist-upgrade), and now eclipse and evolution don't seem to work.  i feel like they may have been working right after i upgraded, and then i installed new apps which may be causing the issue, but i'm not sure. 

as for eclipse, i have version 3.1 downloaded from eclipse.org, not ubuntu repositories.  i'm quite sure that i am using sun's 1.5 jre (i set this up via update-alternatives, and checked my self).

when i start eclipse, the splash screen starts up but it crashes before getting into the workbench:

here's the output from console:

#
# An unexpected error has been detected by HotSpot Virtual Machine:
#
#  SIGSEGV (0xb) at pc=0xb77a3f8b, pid=9598, tid=2995932080
#
# Java VM: Java HotSpot(TM) Client VM (1.5.0_04-b05 mixed mode, sharing)
# Problematic frame:
# V  [libjvm.so+0x120f8b]
#
# An error report file with more information is saved as hs_err_pid9598.log
#
# If you would like to submit a bug report, please visit:
#   [http://java.sun.com/webapps/bugreport/crash.jsp](http://java.sun.com/webapps/bugreport/crash.jsp)
#


as for evolution:
i can open it and check email fine.  but if i go to edit -> preferences, evolution crashes and i get this from the console:

adding hook target 'source'

(evolution:9697): camel-WARNING **: camel_exception_get_id called with NULL parameter.

(evolution:9697): Gdk-CRITICAL **: gdk_gc_set_foreground: assertion `GDK_IS_GC (gc)' failed

(evolution:9697): Gtk-CRITICAL **: gtk_entry_set_text: assertion `text != NULL' failed

(evolution:9697): e-utils-WARNING **: Cannot resolve symbol 'org_gnome_new_mail_config' in plugin '/usr/lib/evolution/2.4/plugins/liborg-gnome-new-mail-notify.so' (not exported?)
BBDB spinning up...

(evolution:9697): Gtk-CRITICAL **: gtk_tree_sortable_set_sort_column_id: assertion `GTK_IS_TREE_SORTABLE (sortable)' failed

(evolution:9697): Gdk-CRITICAL **: gdk_gc_set_foreground: assertion `GDK_IS_GC (gc)' failed
*** glibc detected *** double free or corruption (fasttop): 0x080dde78 ***


can someone please help a frustrated ubuntu user?
thanks.

i am running kde but i've posted here because evolution is gtk based.






[COLOR="Red"]****UPDATE******
I was able to fix this problem after hours (2 days) of frustration.  In the kde settings (kcontrol), I did:
appearance and themes -> gtk styles and fonts -> under gtk styles, select anything except a theme that starts with "smooth". 

I had smooth-tangerine-dream selected and changed it to another theme that different start with "smooth", and now everything works!  Setting it to the QT look also worked for me.

I have no idea why this causes crashes or why it didn't have any crashes until upgrading to breezy.  Perhaps if others can reproduce this or have the same problems, we should send a bug report?[/COLOR]

---

### Post by haaglin on 2005-11-06
Damn, this is wierd, i get this error when i try to run BMPx:

*** glibc detected *** double free or corruption (fasttop)

and guess what? I had a theme with the word smooth in it, and changing it made BMPx work!! Thanks a lot!!

---

