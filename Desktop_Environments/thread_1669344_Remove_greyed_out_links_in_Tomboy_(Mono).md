---
title: "Remove greyed out links in Tomboy (Mono)"
date: 2011-01-17
forum: Desktop Environments
---

### Post by sojusnik on 2011-01-17
Hi folks,

I'm struggling with an annoying issue regarding Tomboy (v1.4.2 under Ubuntu 10.10).

For instance, when I make a new note called "Superman", the word "Superman" will be linked to this note in my other notes. When I delete the note "Superman", the word "Superman" will look like a grey link in all other notes, and not blue as before, when the note with the title "Superman" was available.

Normally it's enough to delete and rewrite the grey link, but there are cases when a quite common word is grey so it's quite demanding to rewrite each word by hand.

How can I set up tomboy, so that no grey link would appear, when a note with a linked title is deleted?

Compare two pictures for clarification.

---

### Post by directhex on 2011-01-18
> **sojusnik said:**
> Hi folks,

I'm struggling with an annoying issue regarding Tomboy (v1.4.2 under Ubuntu 10.10).

For instance, when I make a new note called "Superman", the word "Superman" will be linked to this note in my other notes. When I delete the note "Superman", the word "Superman" will look like a grey link in all other notes, and not blue as before, when the note with the title "Superman" was available.

Normally it's enough to delete and rewrite the grey link, but there are cases when a quite common word is grey so it's quite demanding to rewrite each word by hand.

How can I set up tomboy, so that no grey link would appear, when a note with a linked title is deleted?

Compare two pictures for clarification.

Sounds like something to file a bug against

---

### Post by sojusnik on 2011-01-18
I made a request in bugzilla.

---

### Post by Andrew_P on 2012-03-30
This has been a long-standing issue with Tomboy Notes.  See [http://lists.beatniksoftware.com/pipermail/tomboy-list-beatniksoftware.com/2007-September/000382.html]("http://lists.beatniksoftware.com/pipermail/tomboy-list-beatniksoftware.com/2007-September/000382.html").  Fortunately, there is now a Tomboy Add-in that allows one to remove broken links.

See [http://live.gnome.org/Tomboy/PluginList]("http://live.gnome.org/Tomboy/PluginList") and download the "RemoveBrokenLinks" dll into your ~/.config/tomboy/addins directory.  Restart Tomboy (use System Monitor to end the process, or log out of the desktop and log back in to make the new add-in available.  Go into Tomboy's Edit > Preferences > Add-ins > Tools menu and enable "RemoveBrokenLinks".  In each note that contains broken links, use Ctrl+R or select it from the Tools menu.

Another way handle it is to use the *Places* menu in the top panel of the GNOME Desktop, select *Search for Files...* and search in ~/.local/share/tomboy for file names containing ".note" and containing the text "link:broken".  This will bring up a list of files that need to be fixed.  You can do this manually with gedit, or print the list to a text file — by right-clicking on the search results and selecting Save as... from the context menu — then come up with a script that uses that list of file names to automatically step through the files and remove all instances of <link:broken> and </link:broken> using an editor like sed, without touching any of the other note files.  An automated method using sed was [proposed in 2007 by Sanford Armstrong]("http://lists.beatniksoftware.com/pipermail/tomboy-list-beatniksoftware.com/2007-September/000382.html"), but his simple script touched *all* the .note files in the directory, an undesirable side effect that could be avoided by identifying the files containing "link:broken" before opening them with an editor.

If you try to develop a script on the tomboy directory, it would be a good idea to back up the directory first, perform the script on the copy; then, once you've convinced yourself that the fixes were successfully performed, copy just the modified files back into your working tomboy directory.  Ideally, such a script should operate on a copy of the .note file and keep the original as a backup with an extension of .note~ or .note.bak.

If you just edit the notes manually with the RemoveBrokenLinks add-in while leaving the GNOME search results window open, you'll see the files disappear from the list one by one if you click the "Find" button to repeat the search.

---

