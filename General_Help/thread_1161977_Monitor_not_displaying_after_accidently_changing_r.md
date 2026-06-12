---
title: "Monitor not displaying after accidently changing resolution?"
date: 2009-05-17
forum: General Help
---

### Post by Macfunky on 2009-05-17
I accidently changed the resolution of my screen too high. My monitor shows up "range too high" so i can't see the system to be able to change it back to what it was. Anyone know how i can fix this?

---

### Post by Legace on 2009-05-17
> **Macfunky said:**
> I accidently changed the resolution of my screen too high. My monitor shows up "range too high" so i can't see the system to be able to change it back to what it was. Anyone know how i can fix this?

Select Ubuntu Recovery Mode when booting your system. (If you don't see an option to boot into recovery mode during bootup, press the ESC button continuously until an option is offered).

Then, select Root shell: [img]http://www.howtogeek.com/wp-content/uploads/2008/09/image[6].png[/img]

Finally, type in:
```
rm home/YOUR_USERNAME/.config/monitors.xml
```

Then reboot and you should be fine :)

---

### Post by CatKiller on 2009-05-17
> **Macfunky said:**
> I accidently changed the resolution of my screen too high. My monitor shows up "range too high" so i can't see the system to be able to change it back to what it was. Anyone know how i can fix this?

Is it just your user, so the login screen shows up OK? If that's the case, you can switch to a virtual console with Ctrl-Alt-F1, login and remove your user's custom resolution setting with ```
mv ~/.config/monitors.xml ~/.config/monitors.xml.backup
```

---

### Post by Macfunky on 2009-05-18
Neither of those worked. I keep getting error messages or am told that a directory doesn't exist. Anyone else have any ideas?

---

