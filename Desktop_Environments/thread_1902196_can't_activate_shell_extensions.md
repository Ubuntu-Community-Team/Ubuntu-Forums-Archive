---
title: "can't activate shell extensions"
date: 2011-12-30
forum: Desktop Environments
---

### Post by Sifro on 2011-12-30
Hello,

i downloaded an extension, and put it in .local/share/gnome-shell/extensions, so that this directory now contains a "myExt" subdir with the extension.js and metadata.json files.

I open GNOME-TWEAK-TOOL and click on the "Shell Extensions" tab, but i don't see my extension there... what am i doing wrong?

Thanks!



edit: i forgot to mention that i did try to restart gdm (/etc/init.d/gdm restart), and that this is the extension: [https://github.com/KnisterPeter/gnom...-calender-open](https://github.com/KnisterPeter/gnom...-calender-open)

Also, in LookingGlass the ext. doesn't appear too, while other extension installed through apt work fine.

Creating a simple dummy extension with gnome-shell-extension-tool works fine too (the extension is correctly displayed after restarting gdm)

---

### Post by Sifro on 2011-12-30
Considering that the extension is really simple (below is the full code), maybe i can achieve the same result "manually"? I tried with gconf-editor but i got an error saying that schemas and pairs cannot be edited with gconf-editor :(

___
> 

/* -*- mode: js2; js2-basic-offset: 4; indent-tabs-mode: nil -*- */
const Gio = imports.gi.Gio;

function init() {
}

function enable() {
  let calendarSettings = new Gio.Settings({ schema: 'org.gnome.desktop.default-applications.office.calendar' });
  calendarSettings.set_string('exec', '/usr/bin/x-www-browser [https://www.google.com/calendar');](https://www.google.com/calendar');)
  calendarSettings.set_boolean('needs-term', false);
}

function disable() {
  let calendarSettings = new Gio.Settings({ schema: 'org.gnome.desktop.default-applications.office.calendar' });
  calendarSettings.reset('exec');
  calendarSettings.reset('needs-term');
}

---

### Post by Sifro on 2011-12-30
It looks like that this command solves the issue:

> gsettings set org.gnome.desktop.default-applications.office.calendar exec "/usr/bin/x-www-browser https://www.google.com/calendar"


DOes anyone see any problems in it?

---

