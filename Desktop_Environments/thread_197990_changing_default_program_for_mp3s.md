---
title: "changing default program for mp3s"
date: 2006-06-16
forum: Desktop Environments
---

### Post by jewishj on 2006-06-16
I want to change the default program used to open .mp3 files to XMMS.  I right-click on an mp3 file, choose properties, and go to the open with tab.. but for some reason it won't let me change the selected program and the remove button is grayed out.  The Add button is still clickable, but if I try to add an application is says "Could not add application to the application database".

Seems almost like I don't have permissions to edit these file properties?

Any ideas on how to fix this?

Thanks

---

### Post by olsonar on 2006-06-16
well, if it's permissions, using 
```
sudo nautilus
```
to change the settings should work.

---

### Post by jewishj on 2006-06-16
That didn't work so I guess it's not permissions.... :sad:

---

### Post by tronica on 2006-06-16
try System - Prefs - Perferred Apps

---

### Post by nitricacid on 2006-06-16
I have the same problem, so if anyone could answer this dilemma, it would be greatly appreciated.

I did use ```
sudo nautilus
``` and added VLC to the list but it doesn't automatically start in VLC, I have to choose it from right clicking and choosing 'open with VLC Media Player'.

---

### Post by nitricacid on 2006-06-16
[QUOTE=tronica]try System - Prefs - Perferred Apps[/QUOTE]

This only has options for 'Web Browser', 'Mail Reader', & 'Terminal Emulator'.

---

### Post by jewishj on 2006-06-16
[QUOTE=tronica]try System - Prefs - Perferred Apps[/QUOTE]

As far as I can tell, that only lets you set the default web browser, email client, and terminal shell.. am I missing something in there?

---

### Post by nitricacid on 2006-06-16
This thread might get more attention in: Ubuntu Forums > The Beginner Community>Absolute Beginner Talk

---

### Post by jewishj on 2006-06-16
Another update...  I tried creating a new user belonging to the same group as me and with the same privileges (identical accounts) and logged in as the new user and it worked fine.

I would like to avoid having to do this though as I have already put a descent amount of effort into customizing my account.

---

### Post by jewishj on 2006-06-17
Even with a root nautilus (sudo nautilus) I cannot add a new program either, it tells me it "could not add application to database"

Perhaps there is a missing file or something that it would normally use to store this sort of thing, or that file doesn't have correct permissions on it?

Does anyone know of a backdoor way of accessing this, maybe some preference in the configuration editor or a config file somewhere or something.

Thanks

---

### Post by nitricacid on 2006-06-17
[QUOTE=jewishj]
Does anyone know of a backdoor way of accessing this, maybe some preference in the configuration editor or a config file somewhere or something.

Thanks[/QUOTE]

As for rite now I just open the application I want to use to play (VLC in this case) my media and then just drag it all to the playlist.
It's a pain in the bum not to have the app start automatically when you click on the media you want to play but at least I can actually watch movies WITH sound now

---

### Post by jewishj on 2006-06-17
I found the answer!!!

1) do "sudo nautilus" to open up a root nautilus
2) delete the .local directory (have to show hidden files to see it) in your user directory ($HOME).. so if you're login is "admin" - it would be /home/admin/.local
3) do "sudo killall nautilus"

and all should work (note: this deleted a couple of custom entries I had added to the applications menu using alacarte, so it may alter a couple of things like that)

---

