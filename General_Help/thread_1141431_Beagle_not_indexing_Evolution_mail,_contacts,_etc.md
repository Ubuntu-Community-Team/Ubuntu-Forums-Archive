---
title: "Beagle not indexing Evolution mail, contacts, etc"
date: 2009-04-28
forum: General Help
---

### Post by Jugney on 2009-04-28
I've been searching the forums and internet but haven't found an answer to this yet, so here goes...

I just installed Intrepid and was setting up Beagle as my search program. I decided to try Evolution because I'd LOVE to have all my emails, calendar entries, contacts and tasks be searchable from Beagle (not to mention have appointments and tasks show up in the gnome calendar). However, Beagle not able to index any Evolution information. I took a look at the log, which said:

```
20090428 11:17:19.9901 09716 Beagle  INFO: Starting Beagle Daemon (version 0.3.8)
20090428 11:17:20.0372 09716 Beagle  INFO: Running on Mono 1.9.1
20090428 11:17:20.0381 09716 Beagle  INFO: Command Line: /usr/lib/beagle/BeagleDaemon.exe --bg
20090428 11:17:20.0701 09716 Beagle  WARN: Extended attributes are not supported on this filesystem. Performance will suffer as a result.
20090428 11:18:21.3357 09716 Beagle ERROR EX: Unable to start EvolutionDataServer backend: Unable to find or open libraries:
20090428 11:18:21.3357 09716 Beagle ERROR EX: System.DllNotFoundException: libedataserver-1.2.so.9
20090428 11:18:21.3357 09716 Beagle ERROR EX:   at (wrapper managed-to-native) Evolution.Source:e_source_get_type ()
20090428 11:18:21.3357 09716 Beagle ERROR EX:   at Evolution.Source.get_GType () [0x00000] 
20090428 11:18:21.3357 09716 Beagle ERROR EX:   at GtkSharp.EvolutionSharp.ObjectManager.Initialize () [0x00000] 
20090428 11:18:21.3357 09716 Beagle ERROR EX:   at Evolution.SourceList..cctor () [0x00000] 
```

Which looks like it's missing libedataserver-1.2. However, I have libedataserver-1.2.11 installed. I tried killing beagled and then reinstalling libedataserver. But get the same error message in the log file.

Any ideas? I have seen some discussion in search results about evolution-sharp, but can't find it in the repo's.

Thank you in advance fellow Ubuntians!

---

### Post by anachoret on 2009-10-03
I have had the same problem. Looks like it's because the incompatibility between Mono's libraries version linked with evolution and installed (and upgraded after some time, may be automatically...) Mono in the OS.

Here is my workaround. I made the symlink from /usr/lib/libedataserverui-1.2.so.8.1.0 to /usr/lib/libedataserverui-1.2.so.9 (you may have different numbers). After that I did restart beagle daemon (beagled) and have not seen such error messages in the log.

---

