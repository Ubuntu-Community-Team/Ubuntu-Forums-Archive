---
title: "Can't access updates after install"
date: 2006-01-21
forum: Desktop Environments
---

### Post by RainKap on 2006-01-21
Hello all

I've been playing sporadically with Linux since I retired about 2 years ago. A recent issue of "Linux Format" had the ISO image of "Breezy Badger" on its cover DVD, so I burned it on to a CD and set about installing it on the box which I've set aside for Linux: an HP Pavilion, Athlon XP1700, 512MB RAM, 40GB and 60GB HDD, NEC DVD writer, Pioneer DVD Reader, Soundblaster Player 1024, D-Link DFE538-TX network card, 128MB Nvidia graphics card.

Installation trundled along merrily with occasional input from me, and a system restart, then I got the logon screen and logged on. A link in the top RH corner of the Gnome desktop offered the possibility to look for updates, so I clicked on it and entered the user password (I was foxed at first by the fact that it didn't like the root password, then a bit of reading around showed that I needed to enter the *user* password, because this was an implicit "sudo"), then a big fat nothing! After logging off and logging on again, I found an icon which, when I hovered the mouse cursor over it, told me that there were 26 updates available. Right-clicking on the icon offered me a menu for installing the updates, reviewing the updates, ... but when I selected any of these options - nothing! There was a similar effect when I tried any of the options from other menus to do anything like administration, such as adding another user.

It looks as though I've made a pretty basic error in the installation, but I don't know where to start looking; can anyone help, please?

TIAFYH

Ian Park (soon to be OAP!)

---

### Post by 23meg on 2006-01-21
Does the update manager run when you type ```
gksudo /usr/bin/update-manager
```? 

If not, what errors are you getting at the terminal?

---

### Post by RainKap on 2006-01-21
Thanks for the pointer, 23meg. I copied and pasted the command string from your post into the terminal window, hit <Enter>, and put in my password when it prompted me, but there was *no response at all*. I tried "su" to become the root user, gave it my root password, then typed /usr/bin/update-manager, and the update manager is now downloading updates as I type this.

This makes me suspect that somethuing has gone awry with the "gksudo" function; do you have any suggestion on how I could test this hypothesis, please?

Thanks

Ian Park

---

### Post by RainKap on 2006-01-21
A follow-up - I tried doing a search in the forums on "gksudo", and found a thread which told me that if I do a "basic" install (i.e. *not* "expert"), then the first user I add would have sudo privileges. I did an "expert" install...

I checked the file /etc/sudoers., and indeed user ford (the first user I added during installation) wasn't there; only root. I tried using visudo to edit this file, and replaced "root" with "ford", then tried accessing user setup via the menus, and it prompted me for my password. I put in the password for ford, but although I took great care to type the password correctly, it told me the password was wrong. Every subsequent attempt to start user-admin through the menu told me that I'd got the password wrong, without giving me the chance to enter it(!). Heigh ho, I think I'll try doing another install, this time in "basic" mode...

Cheers

Ian Park

---

### Post by RainKap on 2006-01-23
Yes, that was it! I did a basic install yesterday afternoon, and it sailed through. I successfully added the updates, then tweaked the settings which I'd put in during the "expert" install but which the basic install skipped over.

Can I respectfully suggest that the help screen (F1 from the install CD boot screen) should include a warning that if you use expert install then you'll have problems using "sudo"?

All the best

Ian Park

---

