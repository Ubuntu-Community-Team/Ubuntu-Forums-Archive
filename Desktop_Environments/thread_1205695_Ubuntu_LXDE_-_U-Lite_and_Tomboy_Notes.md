---
title: "Ubuntu LXDE - U-Lite and Tomboy Notes"
date: 2009-07-06
forum: Desktop Environments
---

### Post by afrodeity on 2009-07-06
Wish there was a proper iso for Lubuntu, the Ubuntu project which is working on LXDE environment. I guess I could have done this another way, but it seemed quicker at the time, and now I am paying the price.

I installed U-lite aka Ubuntu Lite. Its a great little distro that comes in at 350mb and runs well on systems below 192mb Ram and 300Mhz CPU, but there are a number of annoying bugs, for example this one;

```

zoleka@ubuntu-desktop:~$ tomboy
[DEBUG]: NoteManager created with note path "/home/zoleka/.tomboy".
[INFO]: Initializing Mono.Addins
[DEBUG]: AddinManager.OnAddinLoaded: Tomboy.Tomboy
[DEBUG]: 	       Name: Tomboy.Tomboy,0.10
[DEBUG]: 	Description: 
[DEBUG]: 	  Namespace: Tomboy
[DEBUG]: 	    Enabled: True
[DEBUG]: 	       File: /usr/lib/tomboy/Tomboy.exe
[DEBUG]: AddinManager.OnAddinLoaded: Tomboy.ExportToHtmlAddin
[DEBUG]: 	       Name: Export to HTML
[DEBUG]: 	Description: Exports individual notes to HTML.
[DEBUG]: 	  Namespace: Tomboy
[DEBUG]: 	    Enabled: True
[DEBUG]: 	       File: /usr/lib/tomboy/addins/ExportToHtml.dll
[DEBUG]: AddinManager.OnAddinLoaded: Tomboy.PrintNotesAddin
[DEBUG]: 	       Name: Printing Support
[DEBUG]: 	Description: Allows you to print a note.
[DEBUG]: 	  Namespace: Tomboy
[DEBUG]: 	    Enabled: True
[DEBUG]: 	       File: /usr/lib/tomboy/addins/PrintNotes.dll
[DEBUG]: AddinManager.OnAddinLoaded: Tomboy.BacklinksAddin
[DEBUG]: 	       Name: Backlinks
[DEBUG]: 	Description: See which notes link to the one you're currently viewing.
[DEBUG]: 	  Namespace: Tomboy
[DEBUG]: 	    Enabled: True
[DEBUG]: 	       File: /usr/lib/tomboy/addins/Backlinks.dll
[DEBUG]: AddinManager.OnAddinLoaded: Tomboy.EvolutionAddin
[DEBUG]: 	       Name: Evolution Mail Integration
[DEBUG]: 	Description: Allows you to drag an email from Evolution into a tomboy note.  The message subject is added as a link in the note.
[DEBUG]: 	  Namespace: Tomboy
[DEBUG]: 	    Enabled: True
[DEBUG]: 	       File: /usr/lib/tomboy/addins/Evolution.dll
[DEBUG]: AddinManager.OnAddinLoaded: Tomboy.FixedWidthAddin
[DEBUG]: 	       Name: Fixed Width
[DEBUG]: 	Description: Adds fixed-width font style.
[DEBUG]: 	  Namespace: Tomboy
[DEBUG]: 	    Enabled: True
[DEBUG]: 	       File: /usr/lib/tomboy/addins/FixedWidth.dll
[DEBUG]: AddinManager.OnAddinLoaded: Tomboy.StickyNoteImportAddin
[DEBUG]: 	       Name: Sticky Notes Importer
[DEBUG]: 	Description: Import your notes from the Sticky Notes applet.
[DEBUG]: 	  Namespace: Tomboy
[DEBUG]: 	    Enabled: True
[DEBUG]: 	       File: /usr/lib/tomboy/addins/StickyNoteImport.dll
[DEBUG]: StickyNoteImporter: Sticky Notes XML file does not exist or is invalid!
[DEBUG]: AddinManager.OnAddinLoaded: Tomboy.WebDavSyncServiceAddin
[DEBUG]: 	       Name: WebDav Sync Service Add-in
[DEBUG]: 	Description: Synchronize Tomboy Notes to a WebDav URL
[DEBUG]: 	  Namespace: Tomboy
[DEBUG]: 	    Enabled: True
[DEBUG]: 	       File: /usr/lib/tomboy/addins/WebDavSyncService.dll
[DEBUG]: AddinManager.OnAddinLoaded: Tomboy.FileSystemSyncServiceAddin
[DEBUG]: 	       Name: Local Directory Sync Service Add-in
[DEBUG]: 	Description: Synchronize Tomboy Notes to a local file system path
[DEBUG]: 	  Namespace: Tomboy
[DEBUG]: 	    Enabled: True
[DEBUG]: 	       File: /usr/lib/tomboy/addins/FileSystemSyncService.dll
[DEBUG]: Unable to locate 'gnomesu' in your PATH
[DEBUG]: Using '/usr/bin/gksu' as GUI 'su' tool
[DEBUG]: Successfully found all system tools
[DEBUG]: Unable to locate 'wdfs' in your PATH
[DEBUG]: Tomboy remote control disabled (DBus exception): Unable to open the session message bus.
[DEBUG]: EnableDisable Called: enabling... True
[DEBUG]: Binding key '<Alt>F12' for '/apps/tomboy/global_keybindings/show_note_menu'
[DEBUG]: Binding key '<Alt>F11' for '/apps/tomboy/global_keybindings/open_start_here'

```

Can anyone suggest an LXDE alternative to Tomboy? Or perhaps a workaround for the above?

---

### Post by afrodeity on 2009-07-06
I can start Tomboy in terminal, lands up on the right side of the top panel, but can't seem to make it stay there. I've tried adding a panel item, using tomboy.desktop, but no go, won't open the application. Solution anyone?

---

### Post by monikgtr on 2011-11-10
You can tray using xpad

---

### Post by Rodney9 on 2011-11-10
> **monikgtr said:**
> You can tray using xpad
 
a little late, but I guess better late than never.

For How-To's, Information and Screen-Casts on Lubuntu go to the
Lubuntu One Stop Thread - 

[http://ubuntuforums.org/showthread.php?t=1844755](http://ubuntuforums.org/showthread.php?t=1844755)


Rodney

---

