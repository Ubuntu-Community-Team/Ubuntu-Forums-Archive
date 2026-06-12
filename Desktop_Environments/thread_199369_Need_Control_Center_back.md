---
title: "Need Control Center back"
date: 2006-06-18
forum: Desktop Environments
---

### Post by nekr0z on 2006-06-18
I seem to have occasionaly removed the Kubuntu original Control Center menu item in the K menu, so that I only have KDE Control Center left. Could anyone please tell me how to get it back?

Thanks in advance.

---

### Post by aysiu on 2006-06-18
You removed it so that it's left? I'm confused.

You can edit the menu by right-clicking on the KMenu icon. The command for the control center is ```
kcontrol
```

---

### Post by Neo Ex on 2006-06-18
KControl forever! :D 
However, the command for the System Settings program is
```
systemsettings -caption "%c" %i %m
```
So, you can add an entry in the menu with KMenuEdit.
You can also check if in the /home/*username*/.config/menus/applications-kmenuedit.menu you have something like
```
 <Exclude>
  <Filename>kde-systemsettings.desktop</Filename>
 </Exclude>
```
If you have this, you can remove the line which begins with <Filename>. If you haven't, don't worry, the first method should work.

---

### Post by nekr0z on 2006-06-19
That's right, I needed "System Settings" back, and "Control Center" was what I still had. I didn't remember how "System Settings" was originally called in English (I use Russian langpack), but hoped somebody would understand, and you did. :-)

Thank you.

---

