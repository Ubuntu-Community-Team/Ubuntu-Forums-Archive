---
title: "Set file permissions for &quot;others&quot; to none and now system completey hosed."
date: 2009-05-29
forum: General Help
---

### Post by u-slayer on 2009-05-29
Okay, I was trying to create a guest user, but restrict access to only the files they actually needed. While still in the main user, I tried to set the file permissions of the root system recursively to deny read access to others. Somehow, this denied access to me and even to the root user! I tried to chmod to fix this, with the root user, but I couldn't access chmod. Now my system is completly hosed. Please help?

---

### Post by doas777 on 2009-05-29
disregard. nothing to see here. look down.

---

### Post by doas777 on 2009-05-29
well sorry, but it probably isn't possible to recover the permissions. you may be able to get it limping by reversing the command, but afterward, you will most likely have to back up and reinstall. 

in future, the consensus is that you should only ever change / permissions with a scalpel, and only when you know exactly what you need and why. think of -R as a sledge hammer.

believe me, all you need to do to restrict a user in ubuntu is take away su and sudo, and thats all just group management.

---

### Post by bodhi.zazen on 2009-05-29
You should look at restricting guests by first giving them a non-admin account. Lilnux security already restrict access to system files and you almost certainly do not need to add to that.

If that is insufficient , look into some type of kiosk mode or apparmor.

---

