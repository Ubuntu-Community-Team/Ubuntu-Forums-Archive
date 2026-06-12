---
title: "my gnome panel doesn't work"
date: 2010-07-25
forum: Desktop Environments
---

### Post by el.norman on 2010-07-25
hello everyone 

This is kinda complex to explain but the only panel that I have doesn't work. When I right click it it only presents me the "help" and about panel" options and when I right click and object except a program in the navigator it only presents me "help."

My question is, is there a way to create a new panel by terminal or a command without right clicking the actual panel, or a setup in gconf-editor to fix my panel?

---

### Post by AceRoom on 2010-07-26
You can reset the gnome-panel back to default.

Log out and execute this from a virtual terminal. This will reset GNOME itself back to default.

```
rm .gconf* .gnome2* -rf
```

Then you can change the config back to what you want.

---

### Post by kerry_s on 2010-07-26
> **AceRoom said:**
> You can reset the gnome-panel back to default.

Log out and execute this from a virtual terminal. This will reset GNOME itself back to default.

```
rm .gconf* .gnome2* -rf
```

Then you can change the config back to what you want.

don't do this, it's bad & will reset a lot of other things.

press-> **alt+f2**
type-> **nautilus**
press-> **ctrl+h**
go in to-> **.gconf**-> **apps**
there delete the "**panel**" folder

---

### Post by AceRoom on 2010-07-26
That's why I've clearly mentioned that it will reset GNOME itself to default. Anyway, do as kerry suggested.

---

### Post by mcduck on 2010-07-26
> **el.norman said:**
> hello everyone 

This is kinda complex to explain but the only panel that I have doesn't work. When I right click it it only presents me the "help" and about panel" options and when I right click and object except a program in the navigator it only presents me "help."

My question is, is there a way to create a new panel by terminal or a command without right clicking the actual panel, or a setup in gconf-editor to fix my panel?

That sounds like you have enabled the locked down panel option in gconf.

To unlock the panel just open the gconf-editor, browse to apps/panel/global/ and turn off the "locked_down"-option.

---

### Post by el.norman on 2010-07-26
> **mcduck said:**
> That sounds like you have enabled the locked down panel option in gconf.

To unlock the panel just open the gconf-editor, browse to apps/panel/global/ and turn off the "locked_down"-option.

Thanks this solved my problem, all this was do by me changing the configurations when i was changing other conf and accidentally checked this one

thanks

---

