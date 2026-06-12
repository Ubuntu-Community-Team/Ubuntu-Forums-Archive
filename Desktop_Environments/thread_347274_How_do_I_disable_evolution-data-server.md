---
title: "How do I disable evolution-data-server?"
date: 2007-01-27
forum: Desktop Environments
---

### Post by manifoldronin on 2007-01-27
I am running ubuntu 6.1. I don't use Evolution, so I would like to disable evolution-data-server, evolution-alarm-notify, and evolution-exchange-storage, which I see take up quite some memory. Could somebody tell me how do I do that?  Thanks.

---

### Post by nike984 on 2007-01-27
Go to System=> Perference=>Sessions =>choose startup program Tab.
Select Items related to Evolution ,disable it , and close the window.
All set :D

---

### Post by manifoldronin on 2007-01-27
Thanks, but I had tried that. The only thing related to evolution on that list is "/usr/lib/evolution/2.8/evolution-alarm-notify".  And even after I disabled it, it still gets started next time I log in.

I have also grep'ed /etc/init.d. Nothing seems to contain "evolution" either.

Thanks.

---

### Post by duns0014 on 2007-02-13
See if you have something under ~/.config/autostart/ It looked like evolution put some crap in there.

---

### Post by digitallyduck on 2008-02-01
Hello guys, this is my 1st posting in Ubuntu Forums

cd /usr/lib/bonobo
mkdir servers.backup
mv servers/GNOME_Evolution_Calendar_AlarmNotify.server servers.backup
mv servers/GNOME_Evolution_DataServer_1.2.server servers.backup
mv servers/GNOME_Evolution_Exchange_Storage_2.12.server servers.backup

logout and login
ps -ax , and your bonobo server wouldn't running Evolution server component :)

---

