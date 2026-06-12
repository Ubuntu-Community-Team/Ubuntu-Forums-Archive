---
title: "Add hostname to LXDM screen"
date: 2017-09-05
forum: Desktop Environments
---

### Post by agenkin on 2017-09-05
Is there an easy way to display the machine's host name on the LXDM screen?  Ideally dynamically (either via the output of the `hostname` command or the contents of /etc/hostname), i.e. not via an image.  Although I guess I could generate a PNG image with the hostname from a script on each machine.

I'm using the default LXDM theme (Industrial) with the bottom pane disabled.

A pointer to any documentation on the LXDM theme creation would be appreciated.

Thanks!

---

### Post by Dennis N on 2017-09-05
> Is there an easy way to display the machine's host name on the LXDM screen?
Do you mean LXDE instead of LXDM? By screen, do you mean on the Desktop? If so, why not add it to your Wallpaper by adding the text to the wallpaper image with an image editor, like Gimp?

---

### Post by agenkin on 2017-09-05
No, I mean LXDM, the display manager.

Editing the background image in GIMP is not a good solution for us, because we have about 150 workstations (hence the need to display the hostname on the login screen).  I was hoping that I could edit the LXDM theme to display the hostname, just like it displays current time.

---

### Post by Dennis N on 2017-09-05
OK so you want it visible somewhere on the login screen. Got it.

---

