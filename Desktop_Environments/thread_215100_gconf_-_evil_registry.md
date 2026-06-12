---
title: "gconf - evil registry?"
date: 2006-07-13
forum: Desktop Environments
---

### Post by quick on 2006-07-13
hi,

just something i wanted to say

i think having something like a windows registry ( i mean gconf ) 
is somewhat evil :twisted: 
the windows registry always is full of shit because the programs dont remove their settings well and stuff like this

wouldnt it be better to stick to the ~/.programm/settings 
stuff?? 

do you think this evil gconf thing will be replaced sometime?

tell me what you think about gconf!

greetings ! :-D

---

### Post by meng on 2006-07-13
I'm no expert, but I think there are some system-wide (or GNOME-wide) settings in there as well as the occasional program-specific setting. But if you're concerned about orphaned settings, can't you just delete .gconf and re-set your settings as you need them?

---

### Post by Ramses de Norre on 2006-07-13
There are 37 apps in my ~/.gconf/apps out of 2092 packages installed (roughly estimated with dpkg -l|grep ii|wc -l I guess not all of this are configurable apps but I didn't know a better way to estimate this..). So it seems to me this isn't so bad.. My whole ~/.gconf folder contains 1.3MB, not too much I think =)

---

### Post by meng on 2006-07-13
> **Ramses de Norre said:**
> There are 37 apps in my ~/.gconf/apps out of 2092 packages installed (roughly estimated with dpkg -l|grep ii|wc -l I guess not all of this are configurable apps but I didn't know a better way to estimate this..).
More than I realized. Interesting!

---

### Post by Arisna on 2006-07-13
I don't think it's too bad.  With the Windows Registry, mistakes can render your installation unbootable.  Messing around in gconf as an unprivileged user, worst case scenario is that you'll hose your desktop configuration and have to use a tty/Failsafe Terminal to recover.  The difference between GConf and the Windows Registry is the difference between using a toothpick to clean your teeth and using a toothpick to perform open heart surgery on yourself. :)

---

### Post by quick on 2006-07-13
reading your answers i now think better of gconf (i really feared it because i dont like win registry) but the way you made me see it is good :) 

best point is really that you cant kill so much if u make a mistake and that you can reset by just deleting the hidden folders in your home directory

thanks for your replies once again i learned something more :)

---

### Post by Jucato on 2006-07-13
Some differences between gconf and windows registry
1. Windows registry is a special database, a single file, that controls *everything installed* in Windows, from system settings to programs. Any changes in the programs/settings are registered in the registry.

Gconf, on the other hand, is just a folder that contains the settings/configuration/customization for individual programs. 
Each program has an individual configuration file. 

So Windows Registry is actually "one file to rule them all", while Gconf is just one directory with multiple files.

2. Windows registry contains all the configuration for the whole system, both administrative and user-specific. Once it's compromised, the whole system is compromised.

Gconf only holds user-defined/user-specific configurations. That's why it's in you /home/username/ folder. It doesn't carry over to other users, nor does it carry over to the / (root) system. If it's compromised, only that user will be compromised.

I think this is the most important difference between the two.

---

### Post by quick on 2006-07-14
thanks for clearing things up! :)

---

### Post by mcduck on 2006-07-14
..and best of all, gconf is actually in human-readable format, and pretty much every key has a description that tells what the key does. Windows registry is just a huge file with long alphanumeric names for every key and no explanations for anything..

---

