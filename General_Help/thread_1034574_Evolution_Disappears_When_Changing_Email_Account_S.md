---
title: "Evolution Disappears When Changing Email Account Settings"
date: 2009-01-08
forum: General Help
---

### Post by wykedengel on 2009-01-08
Okay, I am baffled. I currently have my GMail accounts set up through Evolution (I use IMAP). Every time I try to change a setting dealing with an account, Evolution will close on my when I select [Ok]. Being that I have five accounts set up, it becomes a little frustrating quickly.

Has anyone else experienced this? If so, is there a workaround?

---

### Post by thedarkwinter on 2009-01-09
Hi

if you run evolution from the terminal, it might give you some output when you click [ok]. Possibly, that can help with the solution.

cheers,
michael

---

### Post by wykedengel on 2009-01-09
I will do that now and report back.

---

### Post by wykedengel on 2009-01-09
Here is the output from terminal:

evolution-shell-Message: Killing old version of evolution-data-server...
** (evolution:7750): DEBUG: mailto URL command: evolution %s
** (evolution:7750): DEBUG: mailto URL program: evolution

(evolution:7750): Gtk-CRITICAL **: gtk_widget_get_screen: assertion `GTK_IS_WIDGET (widget)' failed

(evolution:7750): Gdk-CRITICAL **: gdk_screen_is_composited: assertion `GDK_IS_SCREEN (screen)' failed

(evolution:7750): Gtk-CRITICAL **: gtk_widget_get_screen: assertion `GTK_IS_WIDGET (widget)' failed

(evolution:7750): Gdk-CRITICAL **: gdk_screen_is_composited: assertion `GDK_IS_SCREEN (screen)' failed

(evolution:7750): Gtk-CRITICAL **: gtk_widget_get_screen: assertion `GTK_IS_WIDGET (widget)' failed

(evolution:7750): Gdk-CRITICAL **: gdk_screen_is_composited: assertion `GDK_IS_SCREEN (screen)' failed

(evolution:7750): Gtk-CRITICAL **: gtk_widget_get_screen: assertion `GTK_IS_WIDGET (widget)' failed

(evolution:7750): Gdk-CRITICAL **: gdk_screen_is_composited: assertion `GDK_IS_SCREEN (screen)' failed
Changing the queries (contains? "summary" "") 

(evolution:7750): Gtk-CRITICAL **: gtk_widget_get_screen: assertion `GTK_IS_WIDGET (widget)' failed

(evolution:7750): Gdk-CRITICAL **: gdk_screen_is_composited: assertion `GDK_IS_SCREEN (screen)' failed

(evolution:7750): Gtk-CRITICAL **: gtk_widget_get_screen: assertion `GTK_IS_WIDGET (widget)' failed

(evolution:7750): Gdk-CRITICAL **: gdk_screen_is_composited: assertion `GDK_IS_SCREEN (screen)' failed

(evolution:7750): Gtk-CRITICAL **: gtk_widget_get_screen: assertion `GTK_IS_WIDGET (widget)' failed

(evolution:7750): Gdk-CRITICAL **: gdk_screen_is_composited: assertion `GDK_IS_SCREEN (screen)' failed

(evolution:7750): Gtk-CRITICAL **: gtk_widget_get_screen: assertion `GTK_IS_WIDGET (widget)' failed

(evolution:7750): Gdk-CRITICAL **: gdk_screen_is_composited: assertion `GDK_IS_SCREEN (screen)' failed

(evolution:7750): Gtk-CRITICAL **: gtk_widget_get_screen: assertion `GTK_IS_WIDGET (widget)' failed

(evolution:7750): Gdk-CRITICAL **: gdk_screen_is_composited: assertion `GDK_IS_SCREEN (screen)' failed

(evolution:7750): Gtk-CRITICAL **: gtk_widget_get_screen: assertion `GTK_IS_WIDGET (widget)' failed

(evolution:7750): Gdk-CRITICAL **: gdk_screen_is_composited: assertion `GDK_IS_SCREEN (screen)' failed

(evolution:7750): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(evolution:7750): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(evolution:7750): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(evolution:7750): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

The last two lines seem to pop up when I press [OK] per the atteched screenshot.

(evolution:7750): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(evolution:7750): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(evolution:7750): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(evolution:7750): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(evolution:7750): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(evolution:7750): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(evolution:7750): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(evolution:7750): Gtk-CRITICAL **: gtk_widget_get_screen: assertion `GTK_IS_WIDGET (widget)' failed

(evolution:7750): Gdk-CRITICAL **: gdk_screen_is_composited: assertion `GDK_IS_SCREEN (screen)' failed

(evolution:7750): Gtk-CRITICAL **: gtk_widget_get_screen: assertion `GTK_IS_WIDGET (widget)' failed

(evolution:7750): Gdk-CRITICAL **: gdk_screen_is_composited: assertion `GDK_IS_SCREEN (screen)' failed

(evolution:7750): e-data-server-CRITICAL **: e_account_set_string: assertion `ea != NULL' failed

(evolution:7750): GLib-GObject-CRITICAL **: g_object_get_data: assertion `G_IS_OBJECT (object)' failed

(evolution:7750): evolution-mail-CRITICAL **: auto_account_changed: assertion `info != NULL' failed

(evolution:7750): e-data-server-CRITICAL **: e_account_set_string: assertion `ea != NULL' failed
Segmentation fault

The last lines happen when I click [OK] per the attached screenshot.

Thanks for any help!

---

### Post by mssever on 2009-01-09
> **wykedengel said:**
> Segmentation fault
The good news is that we now know you're getting a segfault (which is a bug). The bad news is that segfaults are incredibly difficult to debug. I suggest that you file a bug report on [https://bugs.launchpad.net](https://bugs.launchpad.net) including the words "segfault", "segmentation fault", and/or "crash" in the bug title. Include as much detail as you can in the bug description. However, given the likely difficulty of fixing this bug, don't expect a speedy response.

---

### Post by wykedengel on 2009-01-09
*Groans* Is there another other PIM I could use (I am not a Thunderbird/Sunbird fan) that I could use instead?

---

### Post by mssever on 2009-01-09
> **wykedengel said:**
> *Groans* Is there another other PIM I could use (I am not a Thunderbird/Sunbird fan) that I could use instead?
I don't know what you mean by PIM. I don't use evolution or any other similar program (I'm a Gmail fan), so I can't recommend a different program. However, there's a small chance that reinstalling evolution will fix your problems. Try that.

If that doesn't work, try renaming your ~/.evolution folder (where all your settings live) to cause Evolution to create a new one and see if Evolution works again. It's possible that your settings got corrupted somehow. Note: By renaming ~/.evolution, you'll lose all your settings and evolution data, except what might be stored in gconf or on a server somewhere. Since I don't use Evolution, I don't know how much you'll actually lose. Of course, you can restore everything to the way it was by simply deleting the NEW ~/.evolution directory and renaming the old one back to what it was.

---

### Post by wykedengel on 2009-01-09
Personal Information Manager. I am looking for something similar to Outlook 2003 (2007) as I have so much going on, I need to be able to track appointments, task and the like.

---

### Post by wykedengel on 2009-01-09
> **mssever said:**
> I don't know what you mean by PIM. I don't use evolution or any other similar program (I'm a Gmail fan), so I can't recommend a different program. However, there's a small chance that reinstalling evolution will fix your problems. Try that.

If that doesn't work, try renaming your ~/.evolution folder (where all your settings live) to cause Evolution to create a new one and see if Evolution works again. It's possible that your settings got corrupted somehow. Note: By renaming ~/.evolution, you'll lose all your settings and evolution data, except what might be stored in gconf or on a server somewhere. Since I don't use Evolution, I don't know how much you'll actually lose. Of course, you can restore everything to the way it was by simply deleting the NEW ~/.evolution directory and renaming the old one back to what it was.


I will also give that a try. In the meantime, I tried Evolution in openSUSE, Mint and Mandriva with the same results (the crashing) so it is most definitely an Evolution problem. Unless Evolution just hates my laptop. *smiles*

---

### Post by mssever on 2009-01-09
> **wykedengel said:**
> I will also give that a try. In the meantime, I tried Evolution in openSUSE, Mint and Mandriva with the same results (the crashing) so it is most definitely an Evolution problem. Unless Evolution just hates my laptop. *smiles*
Did you try those distros on the same machine or a different one? I'm trying to establish whether Evolution is using the same settings in all distros.

Also, while it's been ages since I last used Outlook, I know that Google has tools to do most if not all of what I remember doing in Outlook. Of particular note are Gmail and Google Calendar.

---

### Post by mssever on 2009-01-09
duplicate post due to server error

---

### Post by wykedengel on 2009-01-09
I tried them all on the same machine (using virtualbox). It appears that Evolution crashed doing the same thing on each distro. I like the Google services, I just don't like being tied to an internet connection. (While I was in the mood to experiment, Thunderbird doesn't seem to suffer the same bug.)

---

