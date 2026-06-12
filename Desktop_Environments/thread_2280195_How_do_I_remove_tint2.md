---
title: "How do I remove tint2?"
date: 2015-05-28
forum: Desktop Environments
---

### Post by pavilionsahota on 2015-05-28
I am using gnome for the first time today and i really wanted a taskbar. so installed tint2, but now i found a better taskbar called cairo dock. so i tried to remove tint2. 

i tried everything and i mean everything

sudo apt-get remove tint2
sudo apt-get remove --auto-remove tint2
sudo apt-get purge tint2
sudo apt-get purge --auto-remove tint2

i tried it all and yet it's still there staring at me like a troll when i boot up my computer

---

### Post by Copper Bezel on 2015-05-28
--auto-remove only removes packages already marked as unneeded dependencies. That won't make a difference. purge is supposed to remove any configuration files the application adds in user directories in addition to the binary, but doesn't always work. I'm a little baffled, but I've just installed tint2....

Edit: Oh, wait, what was the output when you tried to uninstall it after already having uninstalled it?

How did you get it to autorun in the first place? It isn't autorunning at startup for me under Gnome or Unity. Did you add it to your startup applications or a startup script at some point?

Hmm - and now it uninstalled cleanly for me, as well. Running "tint2" doesn't even bring up a package suggestion, just says "not found."

Could you post a screenshot?

---

### Post by vasa1 on 2015-05-28
> **pavilionsahota said:**
> I am using gnome for the first time today and i really wanted a taskbar. so installed tint2, but now i found a better taskbar called cairo dock. so i tried to remove tint2. 

i tried everything and i mean everything

sudo apt-get remove tint2
sudo apt-get remove --auto-remove tint2
sudo apt-get purge tint2
sudo apt-get purge --auto-remove tint2

i tried it all and yet it's still there staring at me like a troll when i boot up my computer
When you entered those various commands, what was the response in the terminal?
What does **pgrep -l tint2** return?
What happens when you type **pkill tint2**?
Do you have anything like an autostart file, probably somewhere in ~/.config?
What do you see with **ls /usr/share/xsessions**?

---

### Post by pavilionsahota on 2015-05-29
when i try those commands again the output is "tint2 is not installed, so not removed"

pkill & pgrep -l does nothing

and yeah, i added to my list of startups at one point but then removed it before i uninstalled it

---

### Post by buzzingrobot on 2015-05-29
Is ~/.config/tint2 gone?

---

### Post by vasa1 on 2015-05-29
> **pavilionsahota said:**
> when i try those commands again the output is "tint2 is not installed, so not removed"

pkill & pgrep -l does nothing

and yeah, i added to my list of startups at one point but then removed it before i uninstalled it

Then, even if ~/.config/tint2/tint2rc exists, you shouldn't see the tint2 panel!

---

### Post by buzzingrobot on 2015-05-29
Going by memory, tint2 installs as /usr/bin/tint2. Is that gone?  What does "locate tint2" show?

---

### Post by vasa1 on 2015-05-29
> **pavilionsahota said:**
> when i try those commands again the output is "tint2 is not installed, so not removed"

pkill & pgrep -l does nothing

and yeah, i added to my list of startups at one point but then removed it before i uninstalled it
Taken together, it's clear that tint2 isn't running. To give us a hint of what that panel could be, please post the output of```
COLUMNS=150 ps -ef > ~/Desktop/processes.txt
``` within code tags.

---

