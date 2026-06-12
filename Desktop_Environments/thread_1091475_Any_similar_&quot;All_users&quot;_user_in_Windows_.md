---
title: "Any similar &quot;All users&quot; user in Windows for Ubuntu?"
date: 2009-03-09
forum: Desktop Environments
---

### Post by Smigh on 2009-03-09
In windows there's a user called "All users". Files sent to the desktop folder of that user are pulled into the desktop of all users that log in on that computer. I use it to update stuff in systems, even if the actual user folder still doesn't exist. Is there any corresponding user or a simple method in Ubuntu?

---

### Post by bluefrog on 2009-03-09
for new users, /etc/skel is the place.

for existing users a "for" condition and cp will do the trick.

for i in $(awk 'BEGIN{FS=":"} {if ($3 >= 1000) print $1}' /etc/passwd | sed '/nobody/d'); do cp file /home/$i/Desktop/.;done

---

