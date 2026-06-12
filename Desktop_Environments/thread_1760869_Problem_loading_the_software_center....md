---
title: "Problem loading the software center..."
date: 2011-05-17
forum: Desktop Environments
---

### Post by amber.martinez85 on 2011-05-17
Hi all...

I'm a brand new Ubuntu 11.04 user and am just amazed by the speed. However, I am having difficulty getting my 'software center' to load. I'm very green and new to this so I have no idea what to do. I am on a Aspire One net book NAV50. Not a clue how to trouble shoot this.. could really use some help!



Thanks,
Amber

---

### Post by Krytarik on 2011-05-17
Please run the USC from a terminal and post the error messages if you get any:
```
software-center
```
It may also be that related error messages are logged into the file "~/.xsession-errors" in your home directory.

Greetings.

---

### Post by sabelo on 2011-05-18
hi i also recently upgrade to 11.04 and software centre will not load, i tried installing gnome 3 earlier on and it failed since then neither synaptic nor update manager works... when i try to open sy or update manager nptic i get the following message:

Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/za.archive.ubuntu.com_ubuntu_dists_natty_main_i18n_Translation-en, E:The package lists or status file could not be parsed or opened.'

---

### Post by Psychoscorpic on 2011-05-18
Yep - I'm in the same boat.
Same error message, but different culprit being pointed to:
E:Encountered a section with no Package: header, 
E:Problem with MergeList /var/lib/apt/lists /dl.google.com_linux_talkplugin_deb_dists_stable_main_i18n_Translation-en, 
E:The package lists or status file could not be parsed or opened.

> **sabelo said:**
> ...

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/za.archive.ubuntu.com_ubuntu_dists_natty_main_i18n_Translation-en, E:The package lists or status file could not be parsed or opened.'

I've tried with no difference:
(1)
```
sudo dpkg --configure -a
```
(2)
```
sudo gedit sources.list
``` (and #ing out all sources but the first 2)
(3) Modifying Sources selection in Software Center (in the hopes it would overwrite the offending list, since at least Software Center runs until you ask it to actually do something)

Interestingly, I note Sabelo is also using the ZA servers - related, I wonder?

---

### Post by Krytarik on 2011-05-18
> **Psychoscorpic said:**
> 
Interestingly, I note Sabelo is also using the ZA servers - related, I wonder?
Yeah, maybe those server doesn't run stable, or at least at the time your both systems tried to update their package lists.

You both try just deleting the stated files. If there comes another one up after that, do the same for that file, and so on. Backup the concerning files before, just to be sure.

---

