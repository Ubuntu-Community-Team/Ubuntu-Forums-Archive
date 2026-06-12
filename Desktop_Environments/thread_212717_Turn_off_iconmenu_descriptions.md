---
title: "Turn off icon/menu descriptions?"
date: 2006-07-10
forum: Desktop Environments
---

### Post by siby on 2006-07-10
Hi everyone,

How do I turn off icon/item descriptions in Gnome? 

Thank you,

Rob

---

### Post by DJ Scribblinni on 2006-07-10
System>Preferences>Menu and Toolbar Preferences
The option is right there; Toolbar button labels

I'm thinking that's what you're asking...

---

### Post by siby on 2006-07-10
I want to turn off the yellow description box that comes up when you move your pointer over an icon. Nothing changes no matter what I sellect in the *Menues & Toolbars* manager. Good looks on the quick reply, though.

Rob

---

### Post by siby on 2006-07-12
No one knows?

---

### Post by metalheart on 2006-07-12
```
gconf-editor
```

Browse to /apps/panel/global and uncheck tooltips_enabled

---

### Post by siby on 2006-07-13
^ Ah, thanks.

Rob

---

