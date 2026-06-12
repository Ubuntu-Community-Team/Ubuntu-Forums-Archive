---
title: "Log out=borked"
date: 2005-10-16
forum: Desktop Environments
---

### Post by Curlydave on 2005-10-16
Ever since I did a clean install of Breezy final, my logout has been broken. All of the opttions, (shut down, log off, reboot etc) just give me a black screen and don't actually do what they say. My computer will stay on if I try to shut it down, and I'll just have a black screen. Reboot and log off are bugged too. What's up?

---

### Post by souled on 2005-10-16
I get this problem too. Not sure if Shut down or rsetart works, but when I hit 'Log Out' it kicks me to the command line. I have to use startx again in order to get back to gnome. This also happens when i hit ctrl+alt+backspace. It kicks me back to the command line without loading X.

---

### Post by Curlydave on 2005-10-16
[QUOTE=souled]I get this problem too. Not sure if Shut down or rsetart works, but when I hit 'Log Out' it kicks me to the command line. I have to use startx again in order to get back to gnome. This also happens when i hit ctrl+alt+backspace. It kicks me back to the command line without loading X.[/QUOTE]

Actually, my problem's worse than that. I don't even get a command line, and ctrl+alt+backspace does the same thing, not even a non-X command line... Just black.

---

### Post by cwaldbieser on 2005-10-16
[QUOTE=Curlydave]Actually, my problem's worse than that. I don't even get a command line, and ctrl+alt+backspace does the same thing, not even a non-X command line... Just black.[/QUOTE]
Sounds like something is getting hung during the shutdown sequence.  You could maybe try to figure out what it is by doing a CTRL-ALT-F1 to a virtual console, log in, and then kill the graphical log in with something like "sudo killall gdm".  Then you could issue:
```

$ sudo shutdown now

```
and you should see the entire shutdown sequence being logged to the screen.  Hopefully, it will let you know where it is getting stuck.

---

### Post by sk545 on 2005-10-16
i had similar problems:

[http://ubuntuforums.org/showthread.php?t=76723](http://ubuntuforums.org/showthread.php?t=76723)

got it working now, though.  I did 'sudo apt-get remove --purge gdm' than installed gdm again.  So far, it seems to have worked.

---

