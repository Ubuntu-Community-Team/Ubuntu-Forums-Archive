---
title: "Installing KDE 4.2 in Ubuntu killed Gnome"
date: 2009-02-12
forum: Desktop Environments
---

### Post by michaelwholley on 2009-02-12
I have Ubuntu 8.10 (running Gnome) running on my machine. I wanted to take KDE for a spin, and since 4.2 final is available I thought it would be a good time.

I went to kubuntu.org and got the repository off of their site, added their key to gpg, then did an [FONT="Courier New"]apt-get install kubuntu-desktop[/FONT]. While installing KDE I was asked if I wanted to use gdm or kdm, I choose gdm.

When I restarted my machine it would error out when trying to load Gnome or KDE. The error is an .xsession_error. Here is the contents of that file:

[FONT="Courier New"]/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinit.d/default.
gpg-agent [7015]: failed to run the command: No such file or directory[/FONT]

I'd appreciate any suggestions.

---

### Post by michaelwholley on 2009-02-12
Nevermind. KDE didn't break anything.

I noticed in the error I was getting a gpg error. Before installing KDE I moved my .gnupg folder to Dropbox, so my different computers could all access it.

I commented out the line in my .profile file that pointed GnuPG to the new folder location.

Sorry for the false alarm.

---

