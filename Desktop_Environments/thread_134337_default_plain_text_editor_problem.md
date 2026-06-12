---
title: "default plain text editor problem"
date: 2006-02-21
forum: Desktop Environments
---

### Post by Copter on 2006-02-21
hi!

i have some strange issues with default plain text editor file association. when i chose kedit using 'open with' and checking 'always open with this application' i get new entry i Kmenu and when i close the file i was editing and reopen it, i see this message "KDEinit cant run '/home/copter/myfile.txt'".

i tried to change file association using konqueror and kcontrol in user and root mode. ive deleted empty 'Edytor' template many times (on pics below) but it just keeps comming back. i have no idea what can cause that.

using KDE 3.5 with all packages upraded.

thnx for help

copter :]

---

### Post by Jucato on 2006-02-21
1. Don't change file associations as root, because it will only affect the file associations of root user, and not your own user.
2. I'm not sure, but based on your screenshots, you don't have Kedit installed?
3. Kate (and Kwrite) are the new default plain text editors.

Hope this helps.

---

### Post by Copter on 2006-02-22
thnx for fast reply but it doesnt help me much. as i wrote i have been trying to change file association as root _and_ as my default user (copter). i was trying every method. nothing worked.

ofc if i hadnt kedit installed i would not waste time trying to open files with it. on the first screenshot are showed (from top to bottom) :

Edytor - this thing im removing all the time - not associated with any program
Kate - works fine but i just dont like it
Edytor - associated with KEdit - works great
Edytor tekstu - associated with GEdit - i have unistalled GEdit but this option also keeps comming back after opening some text files
OpenOffice.org Writer - associated with OOo - works great but for plain text i would like to use something more simple.

it seems that since Breezy 5.10 Kubuntu is trying to be smarter than user. just like in Windows XP. i want to change something but the system is forceing me to use some another option. if that is the new policy of Kubuntu (becoming idiot compatible system, where user have to do whatever he is told to do) than i have to think about changing os to something more reliable (freebsd?).

copter :]

btw why is this _all the time comming back_ Edytor named kmail_config_composer ? (screen included). thnx

---

### Post by Copter on 2006-03-03
ok, it seems that removing of KMail did the trick. of course when doing this i got message

** (process:24767): CRITICAL **: egg_desktop_entries_add_group: assertion `egg_desktop_entries_lookup_group (entries, group_name) == NULL' failed

on KDE 3.4 i havent got this kind of problems...

copter :]

---

