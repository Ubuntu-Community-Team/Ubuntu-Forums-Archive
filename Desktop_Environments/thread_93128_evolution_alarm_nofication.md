---
title: "evolution alarm nofication"
date: 2005-11-21
forum: Desktop Environments
---

### Post by RikoW on 2005-11-21
Hi everyone,

it seems like, that since some time, evolution is not notifying me for any alarms anymore. It used to do that in Hoary, however, I don't remember, if it used to work already in Breezy and stopped working or if it never worked. All the alarm notification check-boxes in the Preferences and when setting a reminder are set - the little bell symbol is shown next to the entry in evolution.

All the damons seem to be running:

```
> ps x | grep evolution
 8960 ?        Sl     0:14 evolution-2.4
 8969 ?        Sl     0:00 /usr/lib/evolution/evolution-data-server-1.4 --oaf-activate-iid=OAFIID:GNOME_Evolution_DataServer_InterfaceCheck --oaf-ior-fd=39
 8976 ?        Sl     0:20 /usr/lib/evolution/2.4/evolution-exchange-storage --oaf-activate-iid=OAFIID:GNOME_Evolution_Exchange_Component_Factory:2.4 --oaf-ior-fd=42
 8999 ?        Sl     0:00 /usr/lib/evolution/2.4/evolution-alarm-notify --oaf-activate-iid=OAFIID:GNOME_Evolution_Calendar_AlarmNotify_Factory:2.4 --oaf-ior-fd=61
```

However, I never get reminded, which brings the usefulness of the calendar down to about 50%. I use evo to access an exchange server.

Any ideas what might be wrong?

Thanks, 

           Riko

---

### Post by rmjokers on 2005-11-21
I have the same issue here with reminders from an exchange server.  If I add the appointment to my local calendar, the reminder functionality works.  Unfortunately, all of my important appointments are stored on the exchange server.

---

### Post by timetunnel on 2005-11-21
Same here (everything local on one machine). I tried a lot to make it work, but it won't in a way I find useful. What it does here is that it shows the alarm **exactly** at the time you want it, but not later. That mean if you said "notify me 1 day before" your computer has to running **exactly** one day before the event - if you computer is off at that moment, you'll never see the alarm. That's definitely better in KOrganizer.

Jens

---

### Post by dcstar on 2005-11-21
[QUOTE=timetunnel]Same here (everything local on one machine). I tried a lot to make it work, but it won't in a way I find useful. What it does here is that it shows the alarm **exactly** at the time you want it, but not later. That mean if you said "notify me 1 day before" your computer has to running **exactly** one day before the event - if you computer is off at that moment, you'll never see the alarm. That's definitely better in KOrganizer.

Jens[/QUOTE]
This issue is in the Evolution "Bugziller", apparently it was done deliberately to remove the feature of informing you of past alarms when you start up (to fix another issue), but it looks like there have been enough complaints to have it put back in the next version of Evolution.

I'm waiting for it to be released too.........      :???:

---

### Post by korami on 2005-11-22
[QUOTE=dcstar]This issue is in the Evolution "Bugziller", apparently it was done deliberately to remove the feature of informing you of past alarms when you start up (to fix another issue), but it looks like there have been enough complaints to have it put back in the next version of Evolution.

I'm waiting for it to be released too.........      :???:[/QUOTE]


In addition to this (which I hope it will be solved in the next release) I have another issue too: I never get reminded about the anniversaries that I set up for my contacts in the contacts list. Is there any way to receive alarm notification for anniversaries?

---

### Post by igray78756 on 2006-01-26
Someone posted a patch that fixes the problem here:
[http://mail.gnome.org/archives/evolution-patches/2005-November/msg00010.html](http://mail.gnome.org/archives/evolution-patches/2005-November/msg00010.html)

You can apply the patch easily-- first copy the patch into a file named '/tmp/calendar.diff'.
```
$ sudo apt-get build-dep evolution
$ sudo apt-get source evolution
$ cd evolution-2.4.1/calendar
$ cat /tmp/calendar.diff | patch -p0
$ cd ..
$ sudo dpkg-buildpackage -rfakeroot -uc -b
$ sudo dpkg -i ../evolution_2.4.1-0ubuntu7_amd64.deb
$ sudo dpkg -i ../evolution-plugins_2.4.1-0ubuntu7_amd64.deb
```
You may need to change the last two lines to reflect your newly-compiled package names.  Restart evolution, and you should be all set.

---

### Post by scabies on 2006-02-28
I just wanted to confirm that the patch above works great!! i'd missed a meeting yesterday due to not getting calendar alarms, haha. I'm currently running breezy and using evolution to connect with my work's exchange server. 

one thing though, when you go this route synaptic wants to let you know that evolution and evolution-plugins have new versions, even though they're really the same. i tried to rename the packages i created manually to match that of the binary package, but to no avail. any suggestions here would be appreciated!

also, i was able to get this from google cache, but the above page doesn't seem to be accessible anymore (even though i was able to view it just this morning!). so i have pasted the diff file here: 

Index: ChangeLog
===================================================================
RCS file: /cvs/gnome/evolution/calendar/ChangeLog,v
retrieving revision 1.2833
diff -u -p -w -r1.2833 ChangeLog
--- ChangeLog	21 Oct 2005 10:02:34 -0000	1.2833
+++ ChangeLog	8 Nov 2005 06:40:12 -0000
@@ -1,3 +1,10 @@
+2005-11-08  P S Chakravarthi <pchakravarthi novell com>
+
+	Fixes #316710
+	* gui/alarm-notify (alarm_notify_add_calendar):
+	Built the uri string to be used as key for hashtable entries from EUri 
+	rather than directly from e_source API. 
+
 2005-10-21  Mubeen Jukaku  <jmubeen novell com>
 
 	Sankar Committting for Mubeen
Index: gui/alarm-notify/alarm-notify.c
===================================================================
RCS file: /cvs/gnome/evolution/calendar/gui/alarm-notify/alarm-notify.c,v
retrieving revision 1.51
diff -u -p -w -r1.51 alarm-notify.c
--- gui/alarm-notify/alarm-notify.c	13 Jul 2005 10:36:15 -0000	1.51
+++ gui/alarm-notify/alarm-notify.c	8 Nov 2005 06:40:12 -0000
@@ -326,13 +326,18 @@ alarm_notify_add_calendar (AlarmNotify *
 {
 	AlarmNotifyPrivate *priv;
 	ECal *client;
+	EUri *e_uri;
 	char *str_uri;
+	char *pass_key;
 	g_return_if_fail (an != NULL);
 	g_return_if_fail (IS_ALARM_NOTIFY (an));
 	
-
+	/* Make sure the key used in for getting password is properly generated for all types of backends */
 	priv = an->priv;
 	str_uri = e_source_get_uri (source);
+	e_uri = e_uri_new (str_uri);
+	pass_key = e_uri_to_string (e_uri, FALSE);
+	e_uri_free (e_uri);
 	
 	g_mutex_lock (an->priv->mutex);
 	/* See if we already know about this uri */
@@ -345,9 +350,10 @@ alarm_notify_add_calendar (AlarmNotify *
 	   session skip this source loading. we do not really want to prompt for auth from alarm dameon*/
 
 	if ((e_source_get_property (source, "auth") && 
-	     (!e_passwords_get_password (e_source_get_property(source, "auth-domain"), str_uri)))) {
+	     (!e_passwords_get_password (e_source_get_property(source, "auth-domain"), pass_key)))) {
 		g_mutex_unlock (an->priv->mutex);
 		g_free (str_uri);
+		g_free (pass_key);
 		return;
 	}
 	client = auth_new_cal_from_source (source, source_type);
@@ -357,6 +363,7 @@ alarm_notify_add_calendar (AlarmNotify *
 		g_signal_connect (G_OBJECT (client), "cal_opened", G_CALLBACK (cal_opened_cb), an);
 		e_cal_open_async (client, FALSE);
 	}
+	g_free (pass_key);
 	g_free (str_uri);
 	g_mutex_unlock (an->priv->mutex);
 }

---

