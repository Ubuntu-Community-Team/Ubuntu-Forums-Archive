---
title: "xinitrc problems"
date: 2008-07-06
forum: Desktop Environments
---

### Post by Levant on 2008-07-06
Hi all,

I'm having a peculiar problem with the .xinitrc file on one of my two computers. The computers in question (a desktop and laptop) have identical .xinitrc files, but only one of them actually seems to work. The file is very basic right now, and is as shown:

```

#!/usr/bin/env bash
gnome-settings-daemon &
NetworkManager &
exec wmii

```

The desktop executes the file perfectly, while on the laptop, only the final line "exec wmii" seems to be executed, owing to the fact that the wireless is broken and I have ye olde grey theme in the gtk stuff.

Why might this be? It's a big pain in the *** right now, let me tell you that...

---

### Post by mali2297 on 2008-07-06
Do you have the same system installed on both computers?
What kind? (Minimal installation of Hardy?)

Have you tried executing the commands manually?

Also, out of curiosity, what is the purpose of the first line?

---

### Post by Levant on 2008-07-06
> **mali2297 said:**
> Do you have the same system installed on both computers?
What kind? (Minimal installation of Hardy?)

Have you tried executing the commands manually?

Also, out of curiosity, what is the purpose of the first line?

Thanks for your quick reply,

Yes, both computers have a stock installation of Hardy Heron. The only difference is that the problem computer is using amd64 while the desktop is i386.

I have tried manual execution after booting into my environement. To be more specific, here is the message the terminal returns:

```

# gnome-settings-daemon &
** (gnome-settings-daemon:6636): WARNING**: Couldn't connect to a session bus: Failed to connect to socket /tmp/dbus-GUnXHVih3: Connection refused

** (gnome-settings-daemon:6636): WARNING **: Could not get a connection to the bus

# sudo NetworkManager &
[1] 8798

```

The first line is just for reference purposes, as is typical with these sorts of files.

---

### Post by kerry_s on 2008-07-06
are both of those suppose to run as root?

if so you need to add the programs to sudoers so you can launch them with sudo.

you can loss all that fancy stuff:
```
#!/usr/bin/env bash
gnome-settings-daemon &
NetworkManager &
exec wmii

```
to
```

sudo gnome-settings-daemon &
sudo NetworkManager &
wmii
```

sudo visudo

yourname ALL=NOPASSWD: /path/to/program, /path/to/other/program

---

