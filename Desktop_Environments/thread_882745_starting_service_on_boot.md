---
title: "starting service on boot"
date: 2008-08-07
forum: Desktop Environments
---

### Post by cetheriel on 2008-08-07
GCal's homepage says something about init/launchd/rc scripts in order to run its service-starter-script during boot. however, it is not obvious to me. does anyone know how to do it?

---

### Post by DaneM on 2008-08-07
Can you elaborate?

Which script/service would you like to run?  Which version of Ubuntu (or variants) are you using?  Please give me a more detailed description of your goal so I can help you better.

Thanks.

--Dane

---

### Post by cetheriel on 2008-08-07
i run Hardy (8.04.1) and the service is GCal Daemon standalone-start.sh
it runs some java programs.

---

### Post by DaneM on 2008-08-08
1) (in a terminal) sudo gedit /etc/rc.local
2) Before the "exit 0" line, put in the path to your .sh script.
3) (in a terminal) chmod +x /path/to/your/script (this makes it executable)

That should do it!

---

