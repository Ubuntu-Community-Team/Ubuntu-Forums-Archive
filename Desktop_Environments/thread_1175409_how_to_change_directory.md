---
title: "how to change directory ?"
date: 2009-06-01
forum: Desktop Environments
---

### Post by tonjaa on 2009-06-01
[COLOR=Green][COLOR=DarkOrange]tonjaa@tonjaa-desktop:~$ ls[/COLOR]
amsn_received  Examples           PassMark  sysrcd           Updater
bin            GNUstep            Photos    Templates        Videos
Desktop        Music              Pictures  The KMPlayer
Documents      My Received Files  Public    untitled folder
[COLOR=DarkOrange]tonjaa@tonjaa-desktop:~$ [/COLOR]cd /File System
bash: cd: /File: No such file or directory
[COLOR=DarkOrange]tonjaa@tonjaa-desktop:~$ [/COLOR][/COLOR]
i want to change directory to File System but i can't . 
and i want to know what's correct command to do that?

---

### Post by owenll on 2009-06-01
```
cd /
```

If I've understood the question correctly

---

### Post by uupreti on 2009-06-01
> **tonjaa said:**
> [COLOR=Green][COLOR=DarkOrange]tonjaa@tonjaa-desktop:~$ ls[/COLOR]
amsn_received  Examples           PassMark  sysrcd           Updater
bin            GNUstep            Photos    Templates        Videos
Desktop        Music              Pictures  The KMPlayer
Documents      My Received Files  Public    untitled folder
[COLOR=DarkOrange]tonjaa@tonjaa-desktop:~$ [/COLOR]cd /File System
bash: cd: /File: No such file or directory
[COLOR=DarkOrange]tonjaa@tonjaa-desktop:~$ [/COLOR][/COLOR]
i want to change directory to File System but i can't . 
and i want to know what's correct command to do that?

If you directory name is File System then you have to do.

```
cd /File\ System
```

This backslash will be used for bash not to interpret blank space in special meaning.

---

### Post by owenll on 2009-06-01
...or you could navigate to the folder in Nautilus and drag it into the terminal to give you the correct path

---

### Post by MadnessRed on 2009-06-01
or just use quotes

cd '/File system'

---

### Post by Tibuda on 2009-06-01
You can also use the tab-completion. Type "cd /File" and press the tab key.

---

### Post by MadnessRed on 2009-06-01
tab completeion is easier for longer file names, escaping the space is simpler but may confuse some people. Quotes makes more sence but is the most work, unless you have lots of spaces.

---

### Post by tonjaa on 2009-06-01
[COLOR=Sienna]thank you so much.[/COLOR]
[COLOR=DarkOrange]for human beings[/COLOR]

---

