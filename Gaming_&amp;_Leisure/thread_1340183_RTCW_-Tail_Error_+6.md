---
title: "RTCW -Tail Error +6"
date: 2009-11-28
forum: Gaming &amp; Leisure
---

### Post by juicehill on 2009-11-28
When trying to run the 1.0 multiplayer binaries installer for rtcw in ubuntu i'm greated with, 

"Verifying archive integrity...tail: cannot open `+6' for reading: No such file or directory"

I had found a fix that worked for me in 9.10, which had me set an 'enviroment variable' with the export command -- run the archive -- and unset the variable when finished.
[INDENT]julian@julian: export _POSIX2_Version=199209
[indent]: sh wolf.run [/indent]
[indent]: unset _POSIX2_Version=199209[/indent]
[/INDENT]So i get the same error inside 8.04 lts -- but the same fix does not allow me to run this installer.  Which brings me to my question.

What is the difference about 9.10 and 8.04 in the respects of this variable change?  Is there a way to make this fix usable in 8.04 so i can install the wolfenstein directories with the wolf.run file?

here is a torrent link to the .run file in question.
[http://torrents.thepiratebay.org/5148904/wolf-linux-1.0.b2.x86.run.5148904.TPB.torrent](http://torrents.thepiratebay.org/5148904/wolf-linux-1.0.b2.x86.run.5148904.TPB.torrent)

---

