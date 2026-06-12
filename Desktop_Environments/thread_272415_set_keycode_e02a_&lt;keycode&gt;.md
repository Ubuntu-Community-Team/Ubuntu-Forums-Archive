---
title: "set keycode e02a &lt;keycode&gt;"
date: 2006-10-06
forum: Desktop Environments
---

### Post by SuperMike on 2006-10-06
My event log is filling up with:

set keycode e02a <keycode>

...again, and I had once fixed this by applying this procedure that is now currently not working:

[INDENT]
[SIZE="1"]There are a lot of complaints of copious dmesg output resembling this:

[4314715.415000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4314715.415000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.

On some machines, this keycode triggers a hibernate event and is therefore disabled. On other machines e02a is an arrow key and this just causes a mess in dmesg. To quiet these error messages, remove the line from /usr/share/hotkey-setup/generic.hk that reads

setkeycodes e02a 256

and run

sudo /etc/init.d/hotkey-setup restart

and your dmesg should stop filling up with these messages.[/SIZE][/INDENT]


...anyone got any ideas why this won't work now?

---

