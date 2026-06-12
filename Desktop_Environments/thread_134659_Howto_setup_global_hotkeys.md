---
title: "Howto setup global hotkeys?"
date: 2006-02-22
forum: Desktop Environments
---

### Post by palomar on 2006-02-22
I want to use a key combination which points to a shell script that works system wide in KDE. How can I setup this?

---

### Post by mmHg on 2006-02-22
System Settings>>Regional and Accessibility>>Keyboard Shortcuts>>Command Shortcuts.

---

### Post by palomar on 2006-02-22
Thanks :)

I have tested with it, but I can't get it to execute a shell script. For example, if I fill in the command 'firefox' with shortcut ctrl+space it starts firefox, but when I set it to /home/rick/myscript.sh nothing happens :(

I'm using action type "Keyboard Shortcut -> Command/URL (simple)". The script I'm using is executable and when I run it manually in console it works.

[update]
A simple (test) shellscript which only starts 'firefox' does actually work. The script I want to bind to a shortcut has a 'sudo' command in it. In /etc/sudoers I have given my username a NOPASSWD option to a specific file in /usr/bin. Could this be the problem it doesn't work as a shortcut in KDE? As I said: when I run the script in console manually it works fine.. Only when starting it using a shortcut it won't work.

---

### Post by mmHg on 2006-02-23
try using kdesu instead of sudo....seems to integrate a little better and it should prompt you for a password even if you're not running it in the terminal.  It might even be easier to add your script to the menu and bind your keys to it through there....good luck!

---

