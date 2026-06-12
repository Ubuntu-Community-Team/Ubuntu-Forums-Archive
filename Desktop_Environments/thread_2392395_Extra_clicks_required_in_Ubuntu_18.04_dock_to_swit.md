---
title: "Extra clicks required in Ubuntu 18.04 dock to switch application"
date: 2018-05-20
forum: Desktop Environments
---

### Post by kaushiksv on 2018-05-20
Hello,

I have multiple terminals open, they are grouped into a single icon on the dock. However when switching from another application (firefox) in 18.04, clicking on the terminal icon on dock  opens a preview list of terminals, and then I am required to click on one of it bring that window to front. Back in 12.04, it would automatically open the most recently used terminal window. If required, I'd use Mac style Ctrl+~ to switch windows in same app (I had compiz installed). Now I am required to make few extra clicks, and it gets especially annoying when we have lot of switching between applications, and many windows open. Is there a way to fix this, preferably without compiz?

Thanks in advance.

Regards,
Kaushik

---

### Post by kerry_s on 2018-05-20
most people just use the super key to switch apps. ubuntu dock can also be setup to show overview or minimize on click.

---

### Post by kaushiksv on 2018-05-21
Thanks for the reply kerry. I changed the */org/gnome/shell/extensions/dash-to-dock/click-action* setting to *cycle-windows* using dconf-editor. Everything fine :)

---

### Post by kerry_s on 2018-05-21
works for me. you can always switch to the real dash-to-dock to access the settings ubuntu hides.
[ATTACH=CONFIG]279788[/ATTACH]

---

