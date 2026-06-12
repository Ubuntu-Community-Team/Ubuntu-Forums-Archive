---
title: "Map a bash command to a keyboadr button"
date: 2009-06-19
forum: Desktop Environments
---

### Post by kpt_hadok on 2009-06-19
Hello,

Is it possible to map a bash commmand like " mocp -n" to a keyboadr button in ubuntu 9.04?

I have tried using System -> Preferences -> Keyboard shortcuts, but with no luck.

If I create a shortcut key with the command "m -n" and assign it to a key (XF86AudioNext) on my logitech keyboard, nothing happens.

Looking for a simple solution

---

### Post by bryonak on 2009-06-19
A few not so simple solutions spring to mind, but lets see...

Do you use Compiz? If so, it will often override GNOME shortcuts. Install the compizconfig-settings-manager via synaptic, start it from System -> Preferences and configure the shortcuts there.
If you're using GNOME only, try setting the command to "echo 0 >> TESTING" and execute it, then look for a file called "TESTING" in your home directory.
If it exists, then it's your mcop command that fails. If not, the shortcut function fails to execute.


About the harder ones:
You can use xbindkeys, which grabs any input, and send events with xvkbd, xte (xautomation) or xmacro. These are powerful tools if you don't mind a bit of configuration.

---

### Post by kpt_hadok on 2009-06-22
That you for a great answer.

I will look into xbindkeys and fully customize my keyboard. It might be a time consuming challenge, but I think it will make up for it in the long run by streamlining my desktop use.

thanks again.

---

