---
title: "cannot disable CTRL ALT DEL"
date: 2009-03-25
forum: General Help
---

### Post by wanchai on 2009-03-25
I googled around and found dozens of postings that explain how to disable ctrl+alt+del by editing /etc/event.d/control-alt-delete

That doesn't seem to work for me. If I press those three keys on my Intrepid machine nothing happens, and I like it that way. However, the control-alt-delete file on that machine has an exec shutdown line and it's not commented out.

On my Jaunty machine, I always get the logout menu when I press the three keys. Changing the control-alt-delete file (and restarting of course) has no effect. (I need to press these damn keys quite often because I'm running this other OS in VMWare, need it for work.)

Is there any other way to control what happens when these three keys are pressed together? I also checked the keybindings in Gnome, the Intrepid machine doesn't have them redirected.

I also have a Debian 4 system with Gnome. Similar thing there: even though c-a-d is mapped to shutdown in /etc/inittab, nothing happens when the keys are pressed. That's fine, but I'd like to understand why it's behaving that way.

---

### Post by wanchai on 2009-03-28
Found it.

In gconf-editor: /apps/gnome_settings_daemon/keybindings there is a key called "power" that by default is bound to CTRL ALT DEL. I cleared this key.

Whatever is specified in /etc/event.d/control-alt-delete is ignored when running Gnome. However, this script does get executed when you press c-a-d on the console.

---

### Post by hj_ebfe on 2010-02-03
Thanks, this worked for me.

---

