---
title: "Error loading XP with GRUB"
date: 2005-04-28
forum: Desktop Environments
---

### Post by nightshrill on 2005-04-28
Hello, i'd like to first state that I have looked through this forum for the help. I have a two hdd setup, hda with linux on it, and hdb1 with windows on it. hdb is a slave and hda is master. GRUB did not add a windows xp entry when installing Ubuntu, so I edited my menu.lst to add this:

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdb1
title		Microsoft Windows XP
map (hd0) (hd1) #
map (hd1) (hd0) #
root (hd1,0) 	# /dev/hdb1 (No pretending here)
rootnoverify	# (hd1,0)
makeactive
chainloader	+1

after adding this I received an error when trying to boot into windows the error was this:

map (hd0) (hd1) #
map (hd1) (hd0) #
root (hd1,0) 	# /dev/hdb1 (No pretending here)
rootnoverify	# (hd1,0)

Error 11: Unrecognized device string

Now I am willing to just switch the hard drives around and reinstall windows. However I would need the information to add grub to the windows (then active) hdd, if you can help me with either one it will really help. Thank you very much in advanced.

---

### Post by bored2k on 2005-04-28
[QUOTE=Tips and Tricks]Please do not post questions here. This is for HOWTO's and FAQs only.[/QUOTE].

---

