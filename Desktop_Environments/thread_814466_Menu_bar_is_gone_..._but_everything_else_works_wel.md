---
title: "Menu bar is gone ... but everything else works well ..."
date: 2008-05-31
forum: Desktop Environments
---

### Post by hlxshady on 2008-05-31
Hello...

My system is ubuntu 8.04 and I'm now using gnome.
Everything was ok.
The recent operations I did was removing evolution and an update of the system using the auto update.

The symptoms are, all menu bars are gone, including the top one and the bottom one. Alt-F2 does not work, Alt-F1 does not work either.
but other hot-keys i set previously works well such as
<Super>D  show desktop, I set it via configuration editor.

All other desktop effect work well, since I've set a hotkey for terminal, I can still launch firefox via a terminal...

anyone has idea about what is going on with my system ...?


Thank you:)

---

### Post by Tomatz on 2008-05-31
> **hlxshady said:**
> Hello...

My system is ubuntu 8.04 and I'm now using gnome.
Everything was ok.
The recent operations I did was removing evolution and an update of the system using the auto update.

The symptoms are, all menu bars are gone, including the top one and the bottom one. Alt-F2 does not work, Alt-F1 does not work either.
but other hot-keys i set previously works well such as
<Super>D  show desktop, I set it via configuration editor.

All other desktop effect work well, since I've set a hotkey for terminal, I can still launch firefox via a terminal...

anyone has idea about what is going on with my system ...?


Thank you:)

If you can open a terminal type:

```
killall nautilus
```

Then post back the results ;)

---

### Post by hlxshady on 2008-05-31
Thanks so much for the fast response...:)

the result is
the firefox was killed and
a file browser (nautilus) was brought up

now i've to start another firefox to make a reply, but the
firefox started just now does not have a window titlebar while
the terminal window does have.
I started another terminal, and it has the title bar too

---

### Post by hlxshady on 2008-05-31
oops...
the firefox was not killed
and it had the window title bar

but the firefox started afterwards do not have title bar
while other applications work normally

---

### Post by hlxshady on 2008-05-31
ok, one more symptom is that
i tried to add a new user in order to figure out whether it is a
problem of user configuration or system configuration.

and the new user has the same problem as i have

so i think it MAY be a problem of the system...


sorry for so much complement
:P

---

### Post by Tomatz on 2008-06-01
> **hlxshady said:**
> ok, one more symptom is that
i tried to add a new user in order to figure out whether it is a
problem of user configuration or system configuration.

and the new user has the same problem as i have

so i think it MAY be a problem of the system...


sorry for so much complement
:P


What happens when you do a:

```
killall gnome-panel
```

---

### Post by hlxshady on 2008-06-01
gnome-panel: no process killed

---

### Post by Tomatz on 2008-06-01
> **hlxshady said:**
> gnome-panel: no process killed


Well thats your problem ;)

Gnome panel is not loading.

In a terminal type:

```
gnome-panel
```

Post the output (if any).

---

### Post by hlxshady on 2008-06-01
yea, it's because of the gnome-panel.

i fixed the problem by re-installing gnome-panel, it was removed along with the evolution-xxx, i can't remember the exact name of this package. there might be some dependency relation between them.

thank you very much Tomatz :)

---

### Post by Tomatz on 2008-06-01
No problem ;)

---

