---
title: "nautelis location on open"
date: 2021-12-24
forum: Desktop Environments
---

### Post by Disabled20241022 on 2021-12-24
Where do you change the location of the default folder that is opened when you open nautelis?

---

### Post by vanadium on 2021-12-25
There is no way to configure nautilus to open by default in a different folder. You can have it open a different folder by specifying the folder on the command line, for example

```

nautilus ~/Music

```

You could edit the .desktop launcher of Files to open it in a specific folder. To that aim, copy /usr/share/applications/org.gnome.Nautilus.desktop to your local ~/.local/share/applications directory, and edit the copy. Edit the "Exec=" line to become:

```

Exec=nautilus --new-window ~/Music

```

where you replace ~/Music by the appropriate folder. For this to work, you also need to disable dbus activation with the line "DBusActivatable=false".

---

