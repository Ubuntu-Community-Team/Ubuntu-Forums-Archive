---
title: "Trash Applet launches Archive Manager"
date: 2011-05-11
forum: Desktop Environments
---

### Post by pcchynoweth on 2011-05-11
I am running Natty Narwhal with Gnome Classic (I can't get used to Unity). When I click the Trash Can the Archive Manager (file-roller) starts with 

[INDENT]Could not create the archive

Archive type not supported.[/INDENT]

I'm sure the default "open with" for the Trash folder has somehow been modified but I can't figure out how to change it back.

---

### Post by Krytarik on 2011-05-11
Check the specifications in "~/.local/share/applications/mimeapps.list" and remove the respective line.

Greetings.

---

### Post by cvielma on 2011-05-11
Hi.

It is happening only with the Trash applet or every folder?

Through the GUI you could right clic it -> Open With -> Other Application -> write nautilus.

Hope it helps.

Best regards,

---

### Post by Krytarik on 2011-05-12
> **cvielma said:**
> 
It is happening only with the Trash applet or every folder?

Through the GUI you could right clic it -> Open With -> Other Application -> write nautilus.

Due to a fix, it isn't possible anymore to permanently change the mimetype association for folders that way, luckily.

And the Trash applet used to be not affected by the association for "inode/directory", at least until Natty.

So, please just post the content of the mentioned file.

---

### Post by mc4man on 2011-05-12
Did a little ck.ing - this is what's supposed to happen in natty

by default there is no mimeapps.list until you set some association, then it's created

If you were to r. click on a folder and open w/ for example vlc then 2 new sections should be added with 2 inode/directory= lines

Ex. on a fresh install today this is my current mimeapps

> [Default Applications]
x-content/audio-cdda=vlc-cd.desktop
[COLOR="Blue"]inode/directory=nautilus-folder-handler.desktop[/COLOR]

[Added Associations]
x-content/audio-cdda=vlc-cd.desktop;
inode/directory=vlc.desktop;

Now if the blue line wasn't created or removed then the [Added Associations] would take precedence and folders, inc trash, would be opened with vlc (or the first listed if multiple entries

So anyone upgrading to natty should probably start with a new mimeapps.list or make sure that there is a 
[Default Applications] section with 
inode/directory=nautilus-folder-handler.desktop

---

### Post by danielsun23 on 2011-05-18
I am having the exact same problem as initially listed; my trash applet tries to open via archive manager. I have checked my mimeapps.list , and it is the same as the one listed, and still does not work.

This only happens for the trash applet, I can still access the trash folder via Nautilus. 

Thank you in advance.

---

