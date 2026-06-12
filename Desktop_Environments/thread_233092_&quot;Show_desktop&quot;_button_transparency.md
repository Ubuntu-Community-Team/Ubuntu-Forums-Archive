---
title: "&quot;Show desktop&quot; button transparency?"
date: 2006-08-09
forum: Desktop Environments
---

### Post by amadeus_z on 2006-08-09
Hello,

As you can see from the screenshot, the "show desktop" button using Gorilla icons is not transparent.

How can I make it so?

I can't find any

gnome-show-desktop.* files.

THanks

Amadeus

---

### Post by Anduu on 2006-08-09
My guess would be this is a limitation of the gorilla theme....the theme maker probably forgot to include an icon with a transparent background :(

you could try finding and replacing that icon...

---

### Post by Anduu on 2006-08-09
> **Anduu said:**
> My guess would be this is a limitation of the gorilla theme....the theme maker probably forgot to include an icon with a transparent background :(

you could try finding and replacing that icon...

Well I did some digging around and that doesn't seem to be it...must just be the theme itself...

---

### Post by amadeus_z on 2006-08-12
I had another look and the icon used is a .svg so transparent by definition (vector graphic).

How to change the theme?

---

### Post by dpm on 2006-08-12
I think it's got nothing to do with the theme but rather with how gnome-panel handles the button.

The "Show Desktop" button seems to be a special case in the sense that it is independent of the colour/transparency setting of the panel.

Its background is always grey.

---

