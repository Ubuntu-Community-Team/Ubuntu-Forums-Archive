---
title: "Xfce Hibernate Button"
date: 2007-02-28
forum: Desktop Environments
---

### Post by Baochan on 2007-02-28
I can't find how change the script run with Hiberntate button in Xfce Logout Panel.

I suppose it use /etc/acpi/hibernate.sh but this script don't work for me, and I want use hibernate command (because suspend2 works fine).

How can I make this?

---

### Post by energiya on 2007-03-01
You could rename /etc/acpi/hibernate.sh (if that is the file that is used) and make a new hibernate.sh file. Copy from the other one the first line ("#!/somthing/bla") and on the next line write the full path to the suspend2 hibernate script (something like /bin/hibernate.sh, don't have it installed, so I don't know the exact path).
Be warned: this is a nasty trick, and I'm too tired to think how/if it could affect your PC.

---

