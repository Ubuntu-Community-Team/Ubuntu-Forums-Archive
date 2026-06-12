---
title: "Keybindigs not working or wrong way to launch a script??"
date: 2014-12-26
forum: Desktop Environments
---

### Post by pepe-aravaca on 2014-12-26
PROBLEM:
I want a shell script to be lauched whenever a specific key combination is pressed (e.g.: "<Ctrl>/") but I can NOT get it work :cry:

ENVIRONMENT:
It is an old computer running Ubuntu Lucid 10.04 and Gnome-session 2.30.0 and a 2.6.32-26-generic kernel. It shows a very limited gnome desktop lauched as user "usuario" so it is configured with a remote console.

DONE SO FAR:
From the console as user "ususario":
gconftool-2 -t str --set /apps/metacity/global_keybindings/run_command_10 "<Ctrl>/"
gconftool-2 -t str --set /apps/metacity/keybinding_commands/command_10 "/usr/bin/test18.sh"

Contents of /usr/bin/test18.sh (permits are 755):
#!/bin/bash
sleep 1
LANG="en.UTF-8"
echo "OK" > /home/usuario/result.out

RESULT OF TESTS:
The test file /home/usuario/result.out is not created when the key combination "Ctrl" and "/" are pressed simultanously, but the script works when launched from the console.

QUESTION:
What am I missing? :confused:
Thanks in advance.

---

### Post by Impavidus on 2014-12-26
It's a long time ago that I last used gconftool-2, but I think the syntax is correct. I don't know whether the properties you set are indeed the ones you need to set to assign a keyboard shortcut or whatever these things are properly named. It should be possible to set them through the GUI too.

It's not very neat to make a script writing a file in a specific user's home directory and put the script in a directory for system wide executables. Better use the $HOME variable to make it write to the home directory of the user invoking the script or store it in ~/bin and make it executable for the owner only. But it doesn't really matter in case you're the only user on your system.

Most importantly though, 10.04 desktop is end of live. Many packages haven't had (security) updates in 20 months. Even worse, as the server release is still supported, upgrades to server packages may cause instability in the desktop packages. Better to move on to a supported release. Also see [http://ubuntuforums.org/showthread.php?t=2229730](http://ubuntuforums.org/showthread.php?t=2229730)

---

### Post by pepe-aravaca on 2014-12-29
Yes, it is a single user system and it boots directly into that single user desktop.
Security is not a big issue as it is an isolated network and I discard upgrading as it is a temporary solution so doing it can cause more problems to a working environment and more effort than working in the final system.

Thanks for your answer.

---

