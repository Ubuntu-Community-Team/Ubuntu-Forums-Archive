---
title: "Replacing Thunar messed up desktop file operations"
date: 2013-08-11
forum: Desktop Environments
---

### Post by SPARTAN-118 on 2013-08-11
Hello,

I disliked Thunar's lack of a search function that actually worked with the file manager, so I decided to install Nemo instead. Afterwards I attempted to remove Thunar. Now, Nemo is successfully set as the default file manager according to the Settings Manager, and everything works accordingly: double-clicking on the Home folder on the desktop and any links in the bottom panel open in Nemo.

However, I can no longer perform file operations directly from the desktop. Trying to delete a file using the delete key, I get this message: 
> [B]The selected files could not be trashed.
[/B]This feature requires a file manager service to be present (such as the one supplied by Thunar).

Attempting to delete a file, or do any other operation for that matter, results in this error message:

> **The selected files could not be trashed.**
Failed to execute program /usr/bin/Thunar: Success

This implies that, while Nemo is recognized as the default file manager for all other functions, the desktop shell itself can't understand that Thunar is gone. Do I have to reinstall Thunar, or is there a way to get Nemo to do everything?

---

### Post by Buntu Bunny on 2013-08-11
If you do reinstall Thunar, then [this document]("https://help.ubuntu.com/community/FindingFiles") from the Community Help Wiki will tell you how to get Thunar to find files for you.

---

### Post by Frogs Hair on 2013-08-12
The file manager in XFCE doesn't handle the desktop as Nautilus does in a Gnome based DE . That feature is what allows the user to work with files on the desktop outside of the file manager. I don't fully understand how XFCE + Thunar works around this or whether it is possible to enable the same kind function with Nemo. I would start with the preference settings in Nemo and wait for user who knows more about the Nemo - XFCE combination .

---

### Post by SPARTAN-118 on 2013-08-13
> **Buntu Bunny said:**
> If you do reinstall Thunar, then [this document]("https://help.ubuntu.com/community/FindingFiles") from the Community Help Wiki will tell you how to get Thunar to find files for you.

That's not the point. I disliked the awkward combination of Thunar+Catfish (which couldn't even interact with the files it found besides open them). So, I grabbed another file manager which had what I wanted.
Now, I can't even open Steam from the desktop shortcut. Keeps telling me it wants Thunar.

> **Frogs Hair said:**
> The file manager in XFCE doesn't handle the desktop as Nautilus does in a Gnome based DE . That feature is what allows the user to work with files on the desktop outside of the file manager. I don't fully understand how XFCE + Thunar works around this or whether it is possible to enable the same kind function with Nemo. I would start with the preference settings in Nemo and wait for user who knows more about the Nemo - XFCE combination .

I set Nemo as default system-wide, so I don't understand why this isn't working.

EDIT: Okay, so I reinstalled Thunar, and all desktop operations work normally again. Kind of disappointing that it* **has ***to be installed for them to work, but oh well.

Leaving thread open for now in case anybody has any suggestions of fully replacing Thunar with Nemo.

---

