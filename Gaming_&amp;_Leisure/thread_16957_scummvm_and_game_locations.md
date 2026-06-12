---
title: "scummvm and game locations"
date: 2005-02-24
forum: Gaming &amp; Leisure
---

### Post by Valavien on 2005-02-24
Hi all,

I recently installed scummvm and two games.  beneath a steal sky and another one.  I load scummvm but I don't know where synaptic installed the games so I can load them with scummvm

any ideas?

andrew

---

### Post by Dylanby on 2005-02-25
/usr/share/scummvm

---

### Post by Wardhog on 2005-02-28
[QUOTE=Valavien]Hi all,

I recently installed scummvm and two games.  beneath a steal sky and another one.  I load scummvm but I don't know where synaptic installed the games so I can load them with scummvm

any ideas?

andrew[/QUOTE]

Another way to find where files are installed (if you know the program name)

$which <programname>  will show you where it is if the system can find it in your PATH.

In your case, it would be 'which scummvm' would return /usr/share/scummvm

In Synaptic, you can list the files installed with a certain package (going by memory here - system not at hand) by highlighting the package, right-clicking on it and selecting Properties or equivalent.  There's a tab in the resulting dialog box that lists all installed files.

---

