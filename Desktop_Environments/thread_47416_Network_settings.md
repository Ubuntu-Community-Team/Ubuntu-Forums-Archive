---
title: "Network settings"
date: 2005-07-08
forum: Desktop Environments
---

### Post by manc39 on 2005-07-08
Apologies if this is in the wrong forum, I'm a complete Linux newbie and had no idea what category it came under. 

Just installed Kubuntu 5.04 on my other computer.

Trying to get the network/internet settings set up.

Followed the advice here:
[http://ubuntuforums.org/archive/index.php/t-25915.html](http://ubuntuforums.org/archive/index.php/t-25915.html)

When trying to add the gateway and save the file I get a "The document could not be saved, as it was not possible to write to: file///etc/network/interfaces" message.

How can I save it? I assume I need "administrator mode" for the text file editor somehow.

Also, when I try to add a DNS server in network settings it says: "You have to type an alias first", but still adds the server to the list.

---

### Post by Lunde on 2005-07-08
Use sudo (perform the following command as superuser / root) when opening the file for editting. Ex:
**$ sudo gedit /path/to/file**

EDIT: sorry, you use kubuntu. so use the vi or pico instead like:
**$ sudo pico /path/to/file**

---

### Post by Lunde on 2005-07-08
To make sure you don't do anything you'll regret, take a backup of the file firstwith the command:

**$ sudo cp /path/to/file /path/to/file.backup**

Then if you want to restore the original file:

**$sudo mv /path/to/file.backup /path/to/file**

---

### Post by manc39 on 2005-07-08
[QUOTE=Lunde]To make sure you don't do anything you'll regret, take a backup of the file firstwith the command:

**$ sudo cp /path/to/file /path/to/file.backup**

Then if you want to restore the original file:

**$sudo mv /path/to/file.backup /path/to/file**[/QUOTE]
 That doesn't seem to work.

I'm probably doing something wrong but have no way of knowing what.

K Menu > Run command > options - user: root > $ sudo pico /etc/network/interfaces > Run
result: nothing happens

edit: Found from another forum that the command is supposed to be entered into the Konsole.

How do you save the file from the Terminal/Konsole?
edit2: found it- F3

Thanks.

---

### Post by Lunde on 2005-07-08
[QUOTE=manc39]That doesn't seem to work.

I'm probably doing something wrong but have no way of knowing what.

K Menu > Run command > options - user: root > $ sudo pico /etc/network/interfaces > Run
result: nothing happens

edit: Found from another forum that the command is supposed to be entered into the Konsole.

How do you save the file from the Terminal/Konsole?
edit2: found it- F3

Thanks.[/QUOTE]
 If you used **pico**:
**Ctrl+o** = overwrite
Then press **Enter** to confirm the overwrite
and** Ctrl+x** = Exit

All possible commands are written on the bottom line in **pico**

---

### Post by manc39 on 2005-07-08
[QUOTE=Lunde]If you used **pico**:
**Ctrl+o** = overwrite
Then press **Enter** to confirm the overwrite
and** Ctrl+x** = Exit

All possible commands are written on the bottom line in **pico**[/QUOTE]
 Ah, so that **^** character meant Ctrl!

---

### Post by Lunde on 2005-07-08
[QUOTE=manc39]Ah, so that **^** character meant Ctrl![/QUOTE]
 Yes. Had to check.. I did'nt remeber it was written with ^ sorry

---

