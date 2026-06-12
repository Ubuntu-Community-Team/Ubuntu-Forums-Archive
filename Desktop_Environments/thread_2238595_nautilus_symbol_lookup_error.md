---
title: "nautilus: symbol lookup error:"
date: 2014-08-08
forum: Desktop Environments
---

### Post by theodor-h-michailow on 2014-08-08
Hi there, long story short... I updated my ubuntu from 12.04 to 14.04 and now when i click on an icon on the desktop the icons disapear... I opened the console and wrote " #nautilus " then the file manager opens and when i clicl on an icon it  crashes and i get this mesage: ```
root@office1:/home/admin1# nautilus

(nautilus:21382): Gtk-WARNING **: Whoever translated default:LTR did so wrongly.


(nautilus:21382): Gtk-WARNING **: Failed to register client: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files
Initialize nautilus-b1
Initializing nautilus-image-converter extension
Initializing nautilus-open-terminal extension
nautilus: symbol lookup error: /usr/lib/nautilus/extensions-3.0/libnautilus-b1.so: undefined symbol: nautilus_file_is_mime_type


```
i tryed to reinstall unity but with the same result... now i installed Lubuntiu-desktop and it worsk fine ... but i really woudl like to get unity working....
i have searched google but with no real solution... 

10x for the time and efford 10x you all gys.

---

### Post by mc4man on 2014-08-08
No idea where you acquired such an extension. In lieu of figuring that out just remove or move to a .bak
```
sudo rm  /usr/lib/nautilus/extensions-3.0/libnautilus-b1.so
```
or
```
sudo mv  /usr/lib/nautilus/extensions-3.0/libnautilus-b1.so /usr/lib/nautilus/extensions-3.0/libnautilus-b1.so.bak
```

---

### Post by theodor-h-michailow on 2014-08-09
wow : ) so simple ; ) man you are golden thank you so muchhhhhhhhh 10xxxxxx  you helped me alot : )

---

