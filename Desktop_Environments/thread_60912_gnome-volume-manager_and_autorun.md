---
title: "gnome-volume-manager and autorun"
date: 2005-08-29
forum: Desktop Environments
---

### Post by schdefan on 2005-08-29
Hi!
I am using the gnome-volume-manager for automounting purpuse. I burned a script called autorun.sh on a CD. This script will be start after mounting. But i have to confirm a dialog to execute this script. How can I avoid this confirmation dialog?

Thanks for any help
schdefan

---

### Post by schdefan on 2005-10-18
Finally i made same changes in the source code of the gnome-volume-manager.
I downloaded the source and changed 2 lines in the file manager.c
In the function gvm_ask_autorun() i skipped the lines where the dialog is called!


```
 /*
 * gvm_ask_autorun - ask the user if they want to autorun a specific file
 *
 * Returns TRUE if the user selected 'Run' and FALSE otherwise
 */
static gboolean
gvm_ask_autorun (const char *path)
{
	GtkWidget *askme;
	gboolean retval;

	/* MY EDIT */
	retval = TRUE;
	return;
       /* MY EDIT */

       askme = gtk_message_dialog_new (NULL,
					0, GTK_MESSAGE_WARNING,
					GTK_BUTTONS_NONE,
					_("Run command from inserted media?"));
	/*FIXME!! A better secondary label....*/
	gtk_message_dialog_format_secondary_text (GTK_DIALOG (askme),
			_("The file \"%s\" on the inserted media is an auto-run"
			  "file."));

//.....

```

schdefan

---

