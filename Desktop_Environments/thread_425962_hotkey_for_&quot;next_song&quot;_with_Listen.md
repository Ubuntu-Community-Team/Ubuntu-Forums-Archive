---
title: "hotkey for &quot;next song&quot; with Listen"
date: 2007-04-28
forum: Desktop Environments
---

### Post by jermen on 2007-04-28
Hi all,

yesterday i "upgraded" from 6.10 to 7.04 on my Asus F3JC laptop (I simply removed all data and partitions and installed new version).

I'm using Listen as my music player. In previous Ubuntu version (6.10) I was able to use hotkeys for next song (0x99), previous song (0x90) etc. in Listen. In Feisty hotkeys are still working, but only for Totem. Should they change automatically after "apt-get install listen"?

So, the question is following: **How can I change commands executed by actions defined in "System -> Preferences -> Keyboard Shortcuts"?**

I found solution with "/apps/metacity/global_keybindings/run_command_X", but I think this is just a workaround. And I want to modify also other commands, not only those for changing tracks.

Thanks a lot for your time.

---

### Post by kdub432 on 2007-04-28
I have the exact same question. My keyboard shortcuts by default are sent to rhythmbox, and I would like them changed to go to listen. Any help would be appreciated!

---

### Post by bled on 2007-05-01
Same problem over here! I hope someone can help. It's really annoying.
With Edgy (6.10) the multimedia keys of my Logitech keyboard worked flawlessly. As far as I can remember the most recent started player responded to key presses. Rythmbox, Listen, Exaile - each one worked. However, after upgrading to Feisty (7.04) it no longer works for Listen, only for Rythmbox.

---

### Post by jermen on 2007-05-01
Currently the "solution" with gconf-editor and tree "/apps/metacity/global_keybindings/" is working, I'm executing commands "listen --next" and so on. Of course, I had to remove those bindings from "System -> Preferences -> Keyboard shortcuts".

If you want to use it:

1) remove key bindings for "Skip to next track" at dialog for Keyboard shortcuts.

2) run gconf-editor and for key "/apps/metacity/global_keybindings/run_command_1" assign keycode you want to use (also special keys on my laptop in format "0x90" are working, but you can use also more common shortcuts like "<Control>N").

3) finally just assign command like "listen --next" to key "/apps/metacity/keybinding_commands/command_1".

4) repeat steps 1-3 for all hotkeys you want to use.

Yes, this is stupid workaround, because I want to modify commands executed by gnome and assigned to actions in dialog "Keyboard shortcuts". Of course, I've tried google, but without any useful results.

---

### Post by bled on 2007-05-01
Thank you jermen!
At least my Listen is now working again with my keyboard and I don't always have to use the mouse. That was really annoying after years of keyboard multimedia keys :mrgreen: 
Let's hope for a real fix in the near future.

---

