---
title: "Oops PDF preview missing..."
date: 2006-06-01
forum: Desktop Environments
---

### Post by Anduu on 2006-06-01
Not sure what happened but I no longer get a thumbnail preview of pdf files....previous thumbnails are still there but new pdfs dont preview.

I checked in gconf under desktop/gnome/thumbnailers/application@pdf and there is nothing entered.

How can I fix this?

Cheers :confused:

---

### Post by Anduu on 2006-06-01
Eep?

---

### Post by psylence on 2006-06-01
I have: 

(name -> value)
command -> evince-thumbnailer -s %s %u %o
enable -> checked (boolean)

give it a try

---

### Post by Anduu on 2006-06-01
SWEET!

Thanx psy :mrgreen: 

I uninstalled Evince not realizing it would break pdf preview...reinstalled and all is well \\:D/

---

