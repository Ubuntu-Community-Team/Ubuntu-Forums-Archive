---
title: "Icon commands"
date: 2009-06-27
forum: Gaming &amp; Leisure
---

### Post by Azuu on 2009-06-27
I need a command to enable root on a certain .exe(Neverwinter1) from a quick launcher. because for some stupid reason wine (updated) wont run my programs (though it did last week) and a revert did not fix it. The only thing that did was root in terminal and running the .exe manually which is unfeseable since it takes this reaction to every program I use (doom 3).

a little help please.

---

### Post by Tibuda on 2009-06-27
You better fix it. I don't see running wine as root as a safe thing. If you really want to, then you can use gksudo in your launcher.

---

### Post by Azuu on 2009-06-27
true it does need to be fixed, but I wish to know the commands to put in the quicklaunch to make it run that every time.

---

### Post by del_diablo on 2009-06-27
Welcome to my world, lets get started:

```
wine "/Path/To/File"
```
Ex:
```
wine "/home/delly/.wine/drive_c/Spill/Starcraft/StarCraft.exe"
```

Just use your favotire file manager, and copy the executeable you want to start. Then paste into the launcher your making. In the "", no new lines or weird icons. Just the file path in "".

PS: Have you attempted to mod the wine C: folders permissions? It could help.

---

### Post by Azuu on 2009-06-27
> **del_diablo said:**
> Welcome to my world, lets get started:

```
wine "/Path/To/File"
```
Ex:
```
wine "/home/delly/.wine/drive_c/Spill/Starcraft/StarCraft.exe"
```

Just use your favotire file manager, and copy the executeable you want to start. Then paste into the launcher your making. In the "", no new lines or weird icons. Just the file path in "".

PS: Have you attempted to mod the wine C: folders permissions? It could help.

superflourus, it auto starts wine for .exe files.
i need to be in root for it to work.

---

