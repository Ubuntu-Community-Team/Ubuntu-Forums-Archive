---
title: "Tomboy won't Start"
date: 2006-09-28
forum: Desktop Environments
---

### Post by wenzlicker on 2006-09-28
When I try to run tomboy, I get this:

tomboy --start-here

```
Unhandled Exception: System.ApplicationException: Name 'com.beatniksoftware.Tomboy' does not exist.
  at DBus.Service.Get (DBus.Connection connection, System.String name) [0x00000] 
  at Tomboy.RemoteControlProxy.GetInstance () [0x00000] 
  at Tomboy.TomboyCommandLine.Execute () [0x00000] 
  at Tomboy.Tomboy.Main (System.String[] args) [0x00000] 
```

NOTE: I'm using edgy beta

---

### Post by orb9220 on 2006-09-28
Not positive but isn't tomboy an applet? And you add it to the panel with right-click add to panel?

---

### Post by wenzlicker on 2006-09-28
Tomboy is a program that sits in your notification area (similar to gaim's buddy list). Its for taking notes. When you run tomboy, it puts the icon in your notification area. When you run tomboy --start-here, it opens your default note. Siply running tomboy produces the following:

```
NoteManager created with note path "/home/wenzl1dk/.tomboy".
Trying Plugin: Evolution.dll ... EvolutionPlugin. Done.
Trying Plugin: ExportToHTML.dll ... ExportToHTMLPlugin. Done.
Trying Plugin: PrintNotes.dll ... PrintPlugin. Done.
Trying Plugin: StickyNoteImport.dll ... StickyNoteImporter. Done.
Tomboy remote control disabled: Name 'com.beatniksoftware.Tomboy' does not exist.
EnableDisable Called: enabling... True
Binding key '<Alt>F12' for '/apps/tomboy/global_keybindings/show_note_menu'
Binding key '<Alt>F11' for '/apps/tomboy/global_keybindings/open_start_here'

```

but no icon is placed in my notification area. <Alt>F11 produces nothing (look below for why), but <Alt>F12 does show the menu. It looks like my problem is that the icon is not showing up.

I renamed the Start Here note to Todo:, after renaming it back to Start Here, <Alt>F11 worked.

so, where is my icon?

---

### Post by orb9220 on 2006-09-29
That's wierd I just booted the new edgy liveCD and tomboy was in the applets.

---

### Post by wenzlicker on 2006-09-29
I added the tomboy applet to my deskbar. They must have changed the way it works from dapper to edgy. In dapper, I always just had in in my notification area. Oh well! I got my icon back. Thanks.

---

