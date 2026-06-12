---
title: "Changing Keyboard Layout before Login?"
date: 2005-07-13
forum: Desktop Environments
---

### Post by mandarin on 2005-07-13
I use Ubuntu in English with a Swiss German keyboard. This evening, I changed my password to one including umlauts such as ä, ö and ü.

Now, I've rebooted my system and can no longer login because the login screen doesn't support my Swiss German keyboard and I cannot enter ä, ö and ü. Any idea how I could login nevertheless or change the keyboard layout before login?

Mandarin

---

### Post by mandarin on 2005-07-13
P.S.: How can I report this annoying bug?

---

### Post by mandarin on 2005-07-13
I've found a possible solution:> X keyboard configuration

As always, I installed using an English interface, but - being situated in Austria - used a German keyboard. While this worked fine, the following problem might appear: During the D-I -based installation, a user account is created. If you happen to use a password with special characters, you'll most probably have a problem to login, as the X-configuration uses a US-keyboard-layout (which means you won't be able to enter your special characters properly...).
To change this, press CTRL+ALT+F1, log in on the command-line as the user you created, edit the X-config-file (using something like `$ sudo vi /etc/X11/XF86Config-4`), and change the keyboard-layout from "us" to "de" (and most probably the "pc104" to "pc105" too).
Restart X: `$ sudo /etc/init.d/gdm restart` I'll let you know whether it works or not!

Mandarin

---

