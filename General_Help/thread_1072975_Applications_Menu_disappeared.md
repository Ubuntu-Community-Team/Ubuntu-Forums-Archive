---
title: "Applications Menu disappeared"
date: 2009-02-17
forum: General Help
---

### Post by dwieeb on 2009-02-17
This should be a fun one, right?

So my Applications menu does not drop down when I click on it. Places and System do, all the applications work just fine. I can't easily access them though.

When I do click on Applications, a minuscule box drops down but it has absolutely nothing in it.

Database problem? I dunno. No error messages. Please help XD

---

### Post by x33a on 2009-02-17
try killall gnome-panel.

if that doesn't work, remove the menus from the panel, and re-add them.

---

### Post by dwieeb on 2009-02-17
How can I access Terminal? I've always accessed it through my Application menu. :p

---

### Post by mc4man on 2009-02-18
Browse here
places -> home folder -> .config -> menus and delete the file *applications.menu*
Your applications menu will be restored.

(.config is a hidden file, if not seen, then when you open your home folder go view -> "Show Hidden Files" 

 Or just go Places -> Home Folder, remove what's in your location bar and paste this in and press enter
```
~/.config/menus/
```

---

### Post by x33a on 2009-02-18
you can press alt+f2, and enter gnome-terminal to start the terminal.

---

### Post by dwieeb on 2009-02-18
Thank you, mc4man. That worked perfectly.
Thanks for your help, guys!

---

