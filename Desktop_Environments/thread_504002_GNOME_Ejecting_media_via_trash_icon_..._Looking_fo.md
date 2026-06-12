---
title: "GNOME: Ejecting media via trash icon ... Looking for hacker"
date: 2007-07-18
forum: Desktop Environments
---

### Post by Death &amp; Taxes on 2007-07-18
In Mac OS (in all versions IIRC, including the very first ones) you can eject any media by dragging the icon into the trash bin. Sounds strange at first, but you get used to it after a while. I use a Macintosh at work and Linux/GNOME at home. I am so used to it that I frequently drag media icons into the trash, but it does not work in GNOME. It displays a dialog box, saying that if I want to eject the media, I should use "unmount volume" in the popup menu.

Of course I am not the first one who complains about this. There is actually a very long discussion about this at [Bugzilla]("http://bugzilla.gnome.org/show_bug.cgi?id=115763"). The GNOME developers refuse to add this function to the trash icon, stating that it may confuse people to think that they format the media this way. Nevertheless GNOME knows exactly what the user wants to achieve by dragging the icon into the trash, otherwise the message "if you want to eject ..." wouldn't make sense...in other words: GNOME wants to force its user to adjust to the UI, while any good UI should work exactly the other way around. This is very sad, because GNOME is in most parts a very intuitive and user friendly GUI.

Anyway, it is probably unrealistic to believe that the GNOME developers will change their minds about this. I think, however, it should not be too much work to add that function for someone who knows their way around the GNOME source code. Why not create a patch for that function and anyone who wants it can add it on their own?

Unfortunately, my experience with C/C++ is fairly limited, so I doubt I will be able to do it myself. Any Uber-hacker out there that could do it? I am surely not the only user that would find that very convenient.

---

### Post by jaffamuffin on 2007-07-19
I'm not a programmer, but I imagine it would be reativly easy to add in the functinality , just replace the call to the messge about ejecting media, with the call to alctually eject the media?

As a workaround I beleive you can get programs that will watch out for windows/dialogs with specific headings, and then take action.  Maybe using the DBUS system or something. Maybe you could look into this?

i.e. when that dialog pops up, the software detects it and then ejects your media.

---

### Post by Death &amp; Taxes on 2007-07-31
I took a look at the Nautilus sources and figured it out myself.

After unpacking the nautilus sources (I used nautilus-2.18.3), open the file **nautilus-desktop-link-monitor.c** in the subdir **libnautilus-private**

Look for the function **volume_delete_dialog**. It should look like this:

```
static void
volume_delete_dialog (GtkWidget *parent_view,
                      NautilusDesktopLink *link)
{
	GnomeVFSVolume *volume;
	char *dialog_str;
	char *display_name;

	volume = nautilus_desktop_link_get_volume (link);

	if (volume != NULL) {
		display_name = nautilus_desktop_link_get_display_name (link);
		dialog_str = g_strdup_printf (_("You cannot move the volume \"%s\" to the trash."),
					      display_name);
		g_free (display_name);

		if (eject_for_type (gnome_vfs_volume_get_device_type (volume))) {
			eel_run_simple_dialog
				(parent_view, 
				 FALSE,
				 GTK_MESSAGE_ERROR,
				 dialog_str,
				 _("If you want to eject the volume, please use \"Eject\" in the "
				   "popup menu of the volume."),
				 GTK_STOCK_OK, NULL); 
		} else {
			eel_run_simple_dialog
				(parent_view, 
				 FALSE,
				 GTK_MESSAGE_ERROR,
				 dialog_str,
				 _("If you want to unmount the volume, please use \"Unmount Volume\" in the "
				   "popup menu of the volume."),
				 GTK_STOCK_OK, NULL);
		}

		gnome_vfs_volume_unref (volume);
		g_free (dialog_str);
	}
}
```

Replace the **whole** function with the following code:

```

static void
volume_or_drive_ejected_callback (gboolean succeeded,
				    char *error,
				    char *detailed_error,
				    gpointer data)
{
	if (!succeeded) {
		if (*error == 0 &&
		    detailed_error != NULL && *detailed_error == 0) {
			/* This means the mount command displays its own errors */
			return;
		}
		eel_show_error_dialog_with_details (error, NULL, 
		                                    detailed_error, NULL);
	}
}

volume_delete_dialog (GtkWidget *parent_view,
                      NautilusDesktopLink *link)
{
	GnomeVFSVolume *volume;
	char *dialog_str;
	char *display_name;

	volume = nautilus_desktop_link_get_volume (link);

	if (volume != NULL) {
		display_name = nautilus_desktop_link_get_display_name (link);
		dialog_str = g_strdup_printf (_("You cannot move the volume \"%s\" to the trash."),
					      display_name);
		g_free (display_name);

		if (eject_for_type (gnome_vfs_volume_get_device_type (volume))) {
			gnome_vfs_volume_eject (volume, volume_or_drive_ejected_callback, NULL);

		} else {
			gnome_vfs_drive_eject (volume, volume_or_drive_ejected_callback, NULL);
		}

		gnome_vfs_volume_unref (volume);
		g_free (dialog_str);
	}
}
```

Save the file, then

./configure && make && sudo make install

Restart nautilus (*killall nautilus* should do fine) and you've got a working Mac-like drive ejecting mechanism. Of course the "normal" ejecting will work as well.

---

### Post by jaffamuffin on 2007-07-31
Well done.  And thanks for posting back.  

Goes to show you CAN make linux / gnome/ opensource software do what you want.

---

### Post by Death &amp; Taxes on 2007-07-31
> **jaffamuffin said:**
> Goes to show you CAN make linux / gnome/ opensource software do what you want.

Oh yeah, once I actually took the time to look into the code it was just a matter of minutes to fit all the pieces together. It was much easier than I thought, given my limited knowledge of C. The sources are well documented and structured.

Anyway, thanks for the poke. I guess I'll try to tweak some of the rest of GNOME as well ;)

---

