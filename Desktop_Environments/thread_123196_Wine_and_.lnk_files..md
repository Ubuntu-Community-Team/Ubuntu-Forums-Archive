---
title: "Wine and .lnk files."
date: 2006-01-29
forum: Desktop Environments
---

### Post by UltraSonicSite on 2006-01-29
I need to know how to get wine to work with .lnk files (aka, shortcuts to programs) This is because in order for Tribes 2 to work it needs to be run through a shortcut that has options on how to run tribes2.exe

Example:
```

c:\Dynamix\Tribes2\GameData\tribes2.exe -online

```
But through the shortcut file.

[quote=Terminal]
ultrasonicsite@ubuntu:~/Desktop$ wine Tribes\ 2\ Online.lnk
wine: cannot determine executable type for L"H:\\Desktop\\Tribes 2 Online.lnk"
[/quote]

---

### Post by UltraSonicSite on 2006-01-29
Nevermind, fixed it with:
```

wine tribes2.exe -online

```

---

### Post by andlinux21 on 2006-01-29
i hope someone has the answer to this because i had the same problem and now my wine wont work at all

---

### Post by UltraSonicSite on 2006-02-05
Ok now I need gelp with mods. Supposately you are just required to do:

```
tribes2.exe -online -mod Construction -nopure
```

But it doesn't load the mod! The argument is supposed to search for a folder named 'Construction' within the "GameData" folder, but it seems that linux does not do that! How can I fix it?

---

### Post by UltraSonicSite on 2006-03-13
By the way use 'winefile' for lnk files.

type winefile in the console and go to the lnk file

---

### Post by deadlydeathcone on 2007-09-12
You're might all be dead by now, but you can convert all .lnks in a directory to proper menu entries with the command
```
find . -name "*.lnk" -exec wine winemenubuilder '{}' \;
```

---

