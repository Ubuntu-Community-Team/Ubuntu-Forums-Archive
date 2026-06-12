---
title: "script runs at console, not in nautilus"
date: 2010-12-16
forum: Desktop Environments
---

### Post by john_roshi on 2010-12-16
Hello Nautilus fans,
   I'm trying to write a simple Nautilus script for bcrypt.
[FONT="Courier New"]zenity --info --text="processing file: $1"
echo "password"$'\n'"password" | bcrypt -c $1 [/FONT]
  (Note the first line is just a diagnostic message.)
  It runs fine in a terminal. 
  When run from Nautilus as a Nautilus script, it displays
the diagnostic message, but bcrypt doesn't perform the 
desired action on the file.
  Does anyone see what's wrong?
Thanks,
--john

---

