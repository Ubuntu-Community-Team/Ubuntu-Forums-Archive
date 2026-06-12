---
title: "Guildwars Error"
date: 2007-10-19
forum: Gaming &amp; Leisure
---

### Post by Lordmarshal on 2007-10-19
ok so i have tried installing wine and guildwars over and over but now all i get when i install guildwars i get the code below.. could someone plz help me.

[HTML]fixme:shell:SHGetDataFromIDListA SHGDFIL 3 stub
fixme:shell:SHGetDataFromIDListA SHGDFIL 3 stub
err:ole:CoGetClassObject class {fbf23b40-e3f0-101b-8488-00aa003e56f8} not registered
err:ole:CoGetClassObject no class object {fbf23b40-e3f0-101b-8488-00aa003e56f8} could be created for context 0x1
err:ole:CoGetClassObject class {fbf23b40-e3f0-101b-8488-00aa003e56f8} not registered
err:ole:CoGetClassObject no class object {fbf23b40-e3f0-101b-8488-00aa003e56f8} could be created for context 0x1
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:dbghelp:SymInitializeW what to do ??
err:seh:raise_exception Unhandled exception code c0000005 flags 0 addr (nil)
josh@Reaper:~$ fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
[/HTML]

---

### Post by dorath on 2007-10-20
Lordmarshal,

What version of WINE are you using?  If you're not sure, try the following in a terminal:
```
wine --version
```

You ought to see something like this:
```
dorath@dorath-ubuntu# ~ :)$ wine --version
wine-0.9.46
dorath@dorath-ubuntu# ~ :)$ 

```

---

