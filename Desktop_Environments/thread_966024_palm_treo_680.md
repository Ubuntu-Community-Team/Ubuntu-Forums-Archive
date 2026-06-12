---
title: "palm treo 680"
date: 2008-11-01
forum: Desktop Environments
---

### Post by DoubleMcLovin on 2008-11-01
I'm sure theres lots of topics like this, but i sorted through about 10 and can't find a situation like mine.

Unlike every other post I read, I cannot initiate the hotsync on my treo device at all using the USB cord. I have tried with gnome-pilot and jpilot. Trying to connect through the usb:  /dev/pilot  and   /dev/USB*

---

### Post by pistos on 2008-11-01
Same story for me with my Treo 680. It no longer syncs with my computer since updating to 8.10 from 8.04. Everything used to work beautifully. I have seen reports/comments from lots of other Palm OS users with the same problem with other Palm OS devices too. Hopefully, a fix will be discovered soon.

---

### Post by Boss_scout on 2008-11-01
I have the same problem...no response on my Treo 680 in 8.10 everything was great in 8.04. Help needed please

---

### Post by leoperbo on 2008-11-02
Same problem here, and it's not funny...

Palm Treo 680
Ubuntu 8.10 (clean install)

---

### Post by themorningflight on 2008-11-03
Glad I saw this thread. Now I know that this is a common problem for Palm users I can stop wasting time mucking about trying to sort it. Hope a fix appears soon as I can only wait a few days or will have to reinstall Hardy:mad:

---

### Post by groupmsl on 2008-11-03
Me too! I'm desperate! Please help!

---

### Post by bluebook on 2008-11-03
I have the same problem. Has anyone reported it in launchpad?

---

### Post by bluebook on 2008-11-03
You might want to add your details here:
[https://bugs.launchpad.net/ubuntu/+source/gnome-pilot/+bug/282491](https://bugs.launchpad.net/ubuntu/+source/gnome-pilot/+bug/282491)

so that the powers that be get on it quick! :)

---

### Post by Boss_scout on 2008-11-05
I found the following on Gnome-pilot maillist but being new to ubuntu I cannot sort it out. Can someone have a look and put this in to simple language that someone who is new to ubuntu can understand and use

This is almost certainly due to changes in hal that occurred after the
release of gnome-pilot 2.0.15.  This is discussed in gnome bug 484509:
[http://bugzilla.gnome.org/show_bug.cgi?id=484509](http://bugzilla.gnome.org/show_bug.cgi?id=484509)

I'm attaching a patch for gpilotd.c that fixes this issue.  I should
probably go ahead and release a new version of gnome-pilot to fix this
bug, but you could raise this bug in Ubuntu to bring the issue to the
attention of the Ubuntu maintainer.  Debian, for example, patched this
issue last April:
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=441652](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=441652)

I believe this is the patch
 
Index: gpilotd/gpilotd.c
===================================================================
--- gpilotd/gpilotd.c	(revision 1547)
+++ gpilotd/gpilotd.c	(revision 1548)
@@ -1079,7 +1079,7 @@
 hal_device_added (LibHalContext *ctx, const char *udi)
 {
 	gboolean visor_net = FALSE;
-	char *bus, *match_str;
+	char *bus, *platform, *match_str;
 	int vendor_id, product_id, i;
 	GPilotDevice *device;
 	DBusError error;
@@ -1090,15 +1090,23 @@
 
 	load_devices_xml ();
 
-	/* HAL match rule: we look for info.bus == 'usb_device'
+	/* HAL match rule: we look for pda.platform == 'palm'
+	 * (or the legacy info.bus == 'usb_device')
 	 * and then try to match the usb_device.product_id and usb_device.vendor_id
 	 * against the list in devices.xml.
 	 */
-	if (!(bus = libhal_device_get_property_string (hal_ctx, udi, "info.bus", NULL)))
+	if (platform = libhal_device_get_property_string (hal_ctx, udi, "pda.platform", NULL)) {
+	    if (strcmp (platform, "palm") != 0) {
+		libhal_free_string (platform);
 		return;
-	if (strcmp (bus, "usb_device") != 0) {
+	    }
+	} else if (bus = libhal_device_get_property_string (hal_ctx, udi, "info.bus", NULL)) {
+	    if (strcmp (bus, "usb_device") != 0) {
 		libhal_free_string (bus);
 		return;
+	    }
+	} else {
+	    return;
 	}
 
 	dbus_error_init (&error);

---

### Post by Boss_scout on 2008-11-06
Thanks to who ever provides the updates.

I have just installed todays updatse and my Treo 680 stncs perfectly

Thank you Thank you to the update team:lolflag::lolflag:

---

### Post by pistos on 2008-11-06
Hmm. No joy here. My Treo 680 is still not talking with my newly updated Ubuntu 8.10 computer, and I have all of the updates applied that come through the Update Manager.  :(

---

### Post by drizad on 2008-11-07
Same for me here. My Palm Treo 680 just cannot be connected to my Intrepid 8.10 after upgrading from Hardy 8.04.

---

### Post by chris062689 on 2008-11-08
Running with a freshly installed Ibex with updates, still can't sync.
Can someone please post steps?  :(

---

### Post by pistos on 2008-11-12
I just installed the latest updates, which I noticed included a new g-pilot application. I was hoping this would be the fix to my syncing problems. Unfortunately, I still don't have syncing with my Treo 680.

Anyone else's working now since the new update?

---

### Post by pistos on 2008-11-28
Just to give an update of the status of this, my Treo 680 syncing is working again. Thank you to the Ubuntu team!  :)

---

### Post by bnleez on 2008-12-22
How did you get your palm to sync?  Step-by-step instructions in laymen's terms  please.

---

### Post by drizad on 2008-12-22
Update your Ubuntu 8.10 with pre-released updates (intrepid-proposed) by going to System > Administration > Synaptic Package Manager. Click on Updates tab and make sure you tick on Pre-released Updates. Reload your package manager. Your Intrepid will be automatically update with the latest driver for your Palm Treo.

To get your palm to sync: go to System > Preferences > PalmOS device. Click 'Add' to add your device and then 'Get from PDA'. It will sync your Palm with your Ubuntu. In 'Devices' tab, make sure you add a 'USB' type of device.

I notice that my Palm still could not sync with JPilot, but fine with PalmOS. Anybody found the solution on that?

---

