---
title: "how to move the trash can from panel to desktop?"
date: 2006-03-16
forum: Desktop Environments
---

### Post by joey111 on 2006-03-16
hi, i'd like to have the trashcan on the desktop, not on the panel (not enogh space, dont often look at it)
.Welll i know how to remove it from panel, but as i cannot find it in the kmenu i cant add it to desktop!
someone knows??

---

### Post by Xian on 2006-03-16
You just need to right-click on your desktop and create a URL shortcut to your trash folder.

---

### Post by joey111 on 2006-03-28
well, it says it wants to overwrite something; if i do or rename, the trash can icon  just still doesnt appear on the desktop;

---

### Post by wylfing on 2006-03-28
[LIST=1]
[*]Open a terminal and type ```
gconf-editor
```
[*]Drill down to apps > nautilus > desktop.
[*]You should see an item for having the trash on the desktop. Select it.
[*]Right-click the trash icon on your panel and choose Remove from Panel.
[/LIST]

---

### Post by GeneralZod on 2006-03-28
[QUOTE=wylfing][LIST=1]
[*]Open a terminal and type ```
gconf-editor
```
[*]Drill down to apps > nautilus > desktop.
[*]You should see an item for having the trash on the desktop. Select it.
[*]Right-click the trash icon on your panel and choose Remove from Panel.
[/LIST][/QUOTE]

He's using KDE :)

[QUOTE=joey111]well, it says it wants to overwrite something; if i do or rename, the trash can icon  just still doesnt appear on the desktop;[/QUOTE]

More details, please :) What precisely did you try (step-by-step), and what did it say it wanted to overwrite?

---

### Post by joey111 on 2006-03-28
[QUOTE=GeneralZod]He's using KDE :)



More details, please :) What precisely did you try (step-by-step), and what did it say it wanted to overwrite?[/QUOTE]
i tried link to application and link to location
-system:/trash
-/trash
but the trash can icon never appears but the icon of an empty file or the computer system icon.

---

### Post by GeneralZod on 2006-03-29
[QUOTE=joey111]i tried link to application and link to location
-system:/trash
-/trash
but the trash can icon never appears but the icon of an empty file or the computer system icon.[/QUOTE]

You need to enter

```

trash:/

```

as the URL you're linking to.

---

### Post by t.rei on 2006-05-03
Ok, I've done that, but now my trashcan won't ever be empty (according to the icon) and I allready checked fÃor hidden files... Well maybe later I'll check it out some more - Now I need some English/German kooperation on my kde. ;)

---

### Post by Shmalignant on 2008-06-03
Ok, so my trash can icon is now on my desktop, but it defaults to the lower left side.  I tried to drag it to the lower right side, but it won't go.  Anybody know how to solve this?


...nvm, It let me move it, but not as low as I'd like :o(

---

