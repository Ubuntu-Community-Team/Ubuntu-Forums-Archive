---
title: "Murrine Gtk2 Cairo  Installation"
date: 2006-08-08
forum: Desktop Environments
---

### Post by adds2one on 2006-08-08
Hello,

I am trying to install this theme:

[http://www.gnome-look.org/content/show.php?content=42755](http://www.gnome-look.org/content/show.php?content=42755)

I followed the instructions, downloaded the .deb and did:

```
sudo dpkg -i  gtk2-engines-murrine_0.9-1_i386.deb
```

This is the code that came up:

```
Selecting previously deselected package gtk2-engines-murrine.
(Reading database ... 112364 files and directories currently installed.)
Unpacking gtk2-engines-murrine (from gtk2-engines-murrine_0.9-1_i386.deb) ...
Setting up gtk2-engines-murrine (0.9-1) ...
```

But there has been no visible change to my theme and I can find no new theme in System->Preferences->Themes

What am I missing? Also will I be able to uninstall this theme if I get it installed?

Thanks you - J

---

### Post by mcduck on 2006-08-08
The .deb file is just the theme engine. You still need to get a some theme file that uses the Murrine engine. GTK themes come in .tar.gz ot .tar.bz-packages, and are installed by drag&drop to the theme manager.

Uninstalling .deb packages is easy, after they are installed they show in the Synaptic Package Manager.

---

### Post by Lord Illidan on 2006-08-08
Gawd, this looks good...

[IMG]http://www.gnome-look.org/content/pre1/42755-1.jpg[/IMG]

---

### Post by adds2one on 2006-08-08
Ah! I understand! Thank you!! I needed the Murrine Theme Pack!

---

### Post by IsKall on 2006-08-24
When I drop the theme into the theme manager I still get "Invalid Format"

why do i get that?

---

### Post by Maagus on 2006-08-24
I had the same problem. You probably have the theme in tar.gz, just extract it and pack it again to tar.bz2

---

