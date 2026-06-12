---
title: "Eclipse problem with updates"
date: 2005-10-19
forum: Desktop Environments
---

### Post by mindhaq on 2005-10-19
Hello,

I just installed Eclipse via Synaptic, and have it running with Sun's JDK1.5.
So far, so good :)

When I do Help - Software Updates - Find and Install for the first time after launching Eclipse, I get the following error twice:

Error creating feature "file:/usr/lib/eclipse/features/org.eclipse.rcp.source_3.1.1/". (/usr/lib/eclipse/features/org.eclipse.rcp.source_3.1.1/feature.xml (Datei oder Verzeichnis nicht gefunden)

That required directory (/usr/lib/eclipse/features/org.eclipse.rcp.source_3.1.1/) is really not there, nor any other .source directories in the features directory. I still have the files of an old manual installation (3.1.0) around, and there I have that directory.

I already started with -clean, and also in a fresh workspace - no avail :(

Update:
Found the solution real fast ;)

sudo apt-get eclipse-source

There should be a dependency somewhere for this...

---

### Post by cgoerner on 2006-03-29
Thanks.
That worked a treat.

---

