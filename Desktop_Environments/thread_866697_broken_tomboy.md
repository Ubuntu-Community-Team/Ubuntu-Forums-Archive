---
title: "broken tomboy"
date: 2008-07-22
forum: Desktop Environments
---

### Post by Marinodimare on 2008-07-22
My Tomboy application is broken, it does not start. When I open it from the commandline ($ tomboy) the following output is produced. I've already tried purging and reinstalling the thing, and I have no idea what has changed between the time at which it worked, and the time at which it broke down. 

Bash output:
```

[DEBUG]: NoteManager created with note path "/home/nillson/.tomboy".
[INFO]: Initializing Mono.Addins
[DEBUG]: AddinManager.OnAddinLoaded: Tomboy.Tomboy
[DEBUG]:               Name: Tomboy.Tomboy,0.10
[DEBUG]:        Description:
[DEBUG]:          Namespace: Tomboy
[DEBUG]:            Enabled: True
[DEBUG]:               File: /usr/lib/tomboy/Tomboy.exe

Unhandled Exception: System.NullReferenceException: Object reference not set to an instance of an object
  at Mono.Addins.Database.AddinDatabase.Repair (IProgressStatus monitor, System.String domain) [0x00000]
  at Mono.Addins.AddinRegistry.Rebuild (IProgressStatus monitor) [0x00000]
  at Tomboy.AddinManager.InitializeMonoAddins () [0x00000]
  at Tomboy.AddinManager..ctor (System.String tomboy_conf_dir) [0x00000]
  at Tomboy.NoteManager.CreateAddinManager () [0x00000]
  at Tomboy.NoteManager..ctor (System.String directory, System.String backup_directory) [0x00000]
  at Tomboy.NoteManager..ctor (System.String directory) [0x00000]
  at Tomboy.Tomboy.Main (System.String[] args) [0x00000]
```

---

### Post by mochiko on 2008-07-27
hey i got the same problem, and this is what i got
```

chitra@chitra-laptop:~$ tomboy
[DEBUG]: NoteManager created with note path "/home/chitra/.tomboy".
[INFO]: Initializing Mono.Addins
[DEBUG]: AddinManager.OnAddinLoaded: Tomboy.Tomboy
[DEBUG]: 	       Name: Tomboy.Tomboy,0.10
[DEBUG]: 	Description: 
[DEBUG]: 	  Namespace: Tomboy
[DEBUG]: 	    Enabled: True
[DEBUG]: 	       File: /usr/lib/tomboy/Tomboy.exe

Unhandled Exception: System.NullReferenceException: Object reference not set to an instance of an object
  at Mono.Addins.Database.AddinDatabase.Repair (IProgressStatus monitor, System.String domain) [0x00000] 
  at Mono.Addins.AddinRegistry.Rebuild (IProgressStatus monitor) [0x00000] 
  at Tomboy.AddinManager.InitializeMonoAddins () [0x00000] 
  at Tomboy.AddinManager..ctor (System.String tomboy_conf_dir) [0x00000] 
  at Tomboy.NoteManager.CreateAddinManager () [0x00000] 
  at Tomboy.NoteManager..ctor (System.String directory, System.String backup_directory) [0x00000] 
  at Tomboy.NoteManager..ctor (System.String directory) [0x00000] 
  at Tomboy.Tomboy.Main (System.String[] args) [0x00000] 
```

I did the purge thing too, and well I saved a copy of .tomboy but now i don't know how to bring all my notes back. Tomboy opens up but all my old notes are just in some file.. 

basically i got the same problems as you.

---

### Post by cajunaggie on 2008-08-26
Similar problem:

```
(Tomboy:11336): Gtk-WARNING **: Theme directory 32x32/categories of theme gmetalik_05 has no size field

[DEBUG]: NoteManager created with note path "/home/jonathan/.tomboy".
[INFO]: Initializing Mono.Addins

Unhandled Exception: System.InvalidOperationException: Reader not positioned on an element.
  at Mono.Addins.Serialization.BinaryXmlReader.ReadBeginElement () [0x00000] 
  at Mono.Addins.Database.FileDatabase.OpenFileForPath (System.String f, System.String objectId, Mono.Addins.Serialization.BinaryXmlTypeMap typeMap, Boolean checkOnly, System.Object& result) [0x00000] 
  at Mono.Addins.Database.FileDatabase.ReadSharedObject (System.String fullFileName, Mono.Addins.Serialization.BinaryXmlTypeMap typeMap) [0x00000] 
  at Mono.Addins.Description.AddinDescription.ReadBinary (Mono.Addins.Database.FileDatabase fdb, System.String configFile) [0x00000] 
  at Mono.Addins.Database.AddinDatabase.ReadAddinDescription (IProgressStatus monitor, System.String file, Mono.Addins.Description.AddinDescription& description) [0x00000]
```

Interstingly though, when I purged, I could start it up again. However when I returned my back-ups, things went wonky again. Thoughts?

---

### Post by alternatealias on 2008-08-29
Looks like the mono-addins package might be broken? From the logs, it looks like MonoAddins is failing to rebuild the addins database or something.

unfortunately I have no idea where the mono-addins database is for tomboy (or is it some global database?)

I had a quick look, but it doesn't appear to be in ~/.tomboy or in ~/.config/

you could try uninstalling and then reinstalling mono-addins I guess, to see if that fixes it.

---

### Post by alternatealias on 2008-08-29
cajunaggie: looks like you might have a different problem, perhaps you have a corrupt note in your ~/.tomboy directory?

You could try moving all of your notes out of ~/.tomboy and then moving a handful back at a time, starting tomboy, seeing if the error occurs.

If the error happens, then you know it was in the latest group of notes you copied back into ~/.tomboy, so you can restart the process copying 1 note at a time until it happens again (just copy over the ones from the "broken batch").

Once you find the broken note, you should probably poke the Tomboy developers to have a look.

[http://bugzilla.gnome.org](http://bugzilla.gnome.org) is where the tomboy application has its bug database.

---

