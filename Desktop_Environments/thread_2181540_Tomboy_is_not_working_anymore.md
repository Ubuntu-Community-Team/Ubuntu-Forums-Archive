---
title: "Tomboy is not working anymore"
date: 2013-10-18
forum: Desktop Environments
---

### Post by donmatas on 2013-10-18
My tomboy is not working any more. If I run it, it gets stuck and it does not open.

I am using Mint 12.04 (Cinnamon).

Any help will be appreciated.

---

### Post by kostkon on 2013-10-18
> **donmatas said:**
> My tomboy is not working any more. If I run it, it gets stuck and it does not open.

I am using Mint 12.04 (Cinnamon).

Any help will be appreciated.
Try running it in the terminal and see if you'll get any error messages
```
tomboy.exe
```
or even in debug mode like this
```
tomboy.exe --debug
```

Hope that helps.

---

### Post by donmatas on 2013-10-18
> **kostkon said:**
> Try running it in the terminal and see if you'll get any error messages
```
tomboy.exe
```
or even in debug mode like this
```
tomboy.exe --debug
```

Hope that helps.

```
 $ tomboy --debug
** Running Mono with --debug    **
[DEBUG 13:33:05.450] NoteManager created with note path "/home/matas/.local/share/tomboy".
[INFO 13:33:06.014] Initializing Mono.Addins
[DEBUG 13:33:06.679] AddinManager.OnAddinLoaded: Tomboy.Tomboy
[DEBUG 13:33:06.680] 	       Name: Tomboy.Tomboy,0.10
[DEBUG 13:33:06.680] 	Description: 
[DEBUG 13:33:06.681] 	  Namespace: Tomboy
[DEBUG 13:33:06.681] 	    Enabled: True
[DEBUG 13:33:06.681] 	       File: /usr/lib/tomboy/Tomboy.exe
[DEBUG 13:33:07.825] AddinManager.OnAddinLoaded: Tomboy.ExportToHtmlAddin
[DEBUG 13:33:07.825] 	       Name: Export to HTML
[DEBUG 13:33:07.825] 	Description: Exports individual notes to HTML.
[DEBUG 13:33:07.825] 	  Namespace: Tomboy
[DEBUG 13:33:07.825] 	    Enabled: True
[DEBUG 13:33:07.825] 	       File: /usr/lib/tomboy/addins/ExportToHtml.dll
[DEBUG 13:33:07.830] AddinManager.OnAddinLoaded: Tomboy.WebSyncServiceAddin
[DEBUG 13:33:07.830] 	       Name: Web Sync Service Add-in
[DEBUG 13:33:07.830] 	Description: Synchronize Tomboy Notes with Tomboy Online and other compatible web services
[DEBUG 13:33:07.830] 	  Namespace: Tomboy
[DEBUG 13:33:07.830] 	    Enabled: True
[DEBUG 13:33:07.830] 	       File: /usr/lib/tomboy/addins/WebSyncServiceAddin.dll
[DEBUG 13:33:07.844] AddinManager.OnAddinLoaded: Tomboy.WebDavSyncServiceAddin
[DEBUG 13:33:07.845] 	       Name: WebDav Sync Service Add-in
[DEBUG 13:33:07.845] 	Description: Synchronize Tomboy Notes to a WebDav URL
[DEBUG 13:33:07.845] 	  Namespace: Tomboy
[DEBUG 13:33:07.845] 	    Enabled: True
[DEBUG 13:33:07.845] 	       File: /usr/lib/tomboy/addins/WebDavSyncService.dll
[DEBUG 13:33:07.848] Unable to locate 'gnomesu' in your PATH
[DEBUG 13:33:07.849] Using '/usr/bin/gksu' as GUI 'su' tool
[DEBUG 13:33:07.849] Successfully found all system tools
[DEBUG 13:33:07.849] Unable to locate 'wdfs' in your PATH
[DEBUG 13:33:07.849] AddinManager.OnAddinLoaded: Tomboy.FileSystemSyncServiceAddin
[DEBUG 13:33:07.849] 	       Name: Local Directory Sync Service Add-in
[DEBUG 13:33:07.850] 	Description: Synchronize Tomboy Notes to a local file system path
[DEBUG 13:33:07.850] 	  Namespace: Tomboy
[DEBUG 13:33:07.850] 	    Enabled: True
[DEBUG 13:33:07.850] 	       File: /usr/lib/tomboy/addins/FileSystemSyncService.dll
[DEBUG 13:33:07.854] Loading notes
[DEBUG 13:33:08.526] AddinManager.OnAddinLoaded: Tomboy.BacklinksAddin
[DEBUG 13:33:08.527] 	       Name: Backlinks
[DEBUG 13:33:08.527] 	Description: See which notes link to the one you're currently viewing.
[DEBUG 13:33:08.527] 	  Namespace: Tomboy
[DEBUG 13:33:08.528] 	    Enabled: True
[DEBUG 13:33:08.528] 	       File: /usr/lib/tomboy/addins/Backlinks.dll
[DEBUG 13:33:08.529] AddinManager.OnAddinLoaded: Tomboy.PrintNotesAddin
[DEBUG 13:33:08.529] 	       Name: Printing Support
[DEBUG 13:33:08.530] 	Description: Allows you to print a note.
[DEBUG 13:33:08.530] 	  Namespace: Tomboy
[DEBUG 13:33:08.530] 	    Enabled: True
[DEBUG 13:33:08.531] 	       File: /usr/lib/tomboy/addins/PrintNotes.dll
[DEBUG 13:33:08.532] AddinManager.OnAddinLoaded: Tomboy.FixedWidthAddin
[DEBUG 13:33:08.532] 	       Name: Fixed Width
[DEBUG 13:33:08.533] 	Description: Adds fixed-width font style.
[DEBUG 13:33:08.533] 	  Namespace: Tomboy
[DEBUG 13:33:08.533] 	    Enabled: True
[DEBUG 13:33:08.534] 	       File: /usr/lib/tomboy/addins/FixedWidth.dll
[DEBUG 13:33:08.536] AddinManager.OnAddinLoaded: Tomboy.EvolutionAddin
[DEBUG 13:33:08.536] 	       Name: Evolution Mail Integration
[DEBUG 13:33:08.540] 	Description: Allows you to drag an email from Evolution into a Tomboy note.  The message subject is added as a link in the note with an envelope icon next to it.
[DEBUG 13:33:08.541] 	  Namespace: Tomboy
[DEBUG 13:33:08.541] 	    Enabled: True
[DEBUG 13:33:08.541] 	       File: /usr/lib/tomboy/addins/Evolution.dll
[DEBUG 13:33:08.583] AddinManager.OnAddinLoaded: Tomboy.UnderlineAddin
[DEBUG 13:33:08.583] 	       Name: Underline
[DEBUG 13:33:08.583] 	Description: Adds ability to underline text.
[DEBUG 13:33:08.584] 	  Namespace: Tomboy
[DEBUG 13:33:08.584] 	    Enabled: True
[DEBUG 13:33:08.584] 	       File: /usr/lib/tomboy/addins/Underline.dll
[DEBUG 13:33:08.586] AddinManager.OnAddinLoaded: Tomboy.InsertTimestampAddin
[DEBUG 13:33:08.586] 	       Name: Insert Timestamp
[DEBUG 13:33:08.586] 	Description: Inserts current date and time at the cursor position.
[DEBUG 13:33:08.590] 	  Namespace: Tomboy
[DEBUG 13:33:08.590] 	    Enabled: True
[DEBUG 13:33:08.590] 	       File: /usr/lib/tomboy/addins/InsertTimestamp.dll
[DEBUG 13:33:08.591] AddinManager.OnAddinLoaded: Tomboy.StickyNoteImportAddin
[DEBUG 13:33:08.593] 	       Name: Sticky Notes Importer
[DEBUG 13:33:08.593] 	Description: Import your notes from the Sticky Notes applet.
[DEBUG 13:33:08.594] 	  Namespace: Tomboy
[DEBUG 13:33:08.594] 	    Enabled: True
[DEBUG 13:33:08.594] 	       File: /usr/lib/tomboy/addins/StickyNoteImport.dll
[DEBUG 13:33:08.595] StickyNoteImporter: Sticky Notes XML file does not exist or is invalid!
[DEBUG 13:33:08.610] Creating Buffer for 'Embajada Británica'...
[DEBUG 13:33:08.842] Embajada Británica tags:
```

---

