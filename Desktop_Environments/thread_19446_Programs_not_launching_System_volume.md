---
title: "Programs not launching? System volume?"
date: 2005-03-11
forum: Desktop Environments
---

### Post by hugh50935 on 2005-03-11
Hi all,

I just installed Ubuntu yesterday. Now, when i started my computer today, i've found that the Network Configuration program won't launch, nor will the Root Terminal, plus a few others. Any clues?

Also, how do I adjust the system volume? at the moment, the sound through my headphones is deafening, but if I try to adjust "PCM volume" it will either go to mute, or full volume!

Thanks, any help would be greatly appreciated!

Hugh

---

### Post by hugh50935 on 2005-03-11
Also, i',m getting the error on startup:

"Could not look up internet address for .
This will prevent GNOME from operating correctly.
It may be possible to correct the problem by adding
 to the file /etc/hosts."

"try again" does nothing, so i just hit "log on anyway" to go to the desktop.

Hugh

---

### Post by andyman on 2005-03-17
[QUOTE=hugh50935]Also, i',m getting the error on startup:

"Could not look up internet address for .
This will prevent GNOME from operating correctly.
It may be possible to correct the problem by adding
 to the file /etc/hosts."

"try again" does nothing, so i just hit "log on anyway" to go to the desktop.

Hugh[/QUOTE]
 Yup, got exactly the same problem.  I'm guessing the hostname needs adding to /etc/hosts (!), however how do you do this when sudo, root etc doesnt work!

I believe the error appears because it could not configure the network on the initial build, couldnt this be a common problem?

---

### Post by andyman on 2005-03-18
reinstalled the OS, this time configuring the network manually so that a hostname and IP would be added to the /etc/hosts file.  Worked, no errors.

Now just need to get my WLAN running.....

(PS. yes I know you can tell I'm new to this!).

---

