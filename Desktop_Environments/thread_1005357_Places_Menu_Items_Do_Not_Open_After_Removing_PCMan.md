---
title: "Places Menu Items Do Not Open After Removing PCManFM"
date: 2008-12-08
forum: Desktop Environments
---

### Post by Asph on 2008-12-08
I have installed PCManFM in Ubuntu Intrepid a while ago and after finding some extensions for Nautilus File Manager, I decided to return to Nautilus, so uninstalled PCManFM.

However, my Places Menu on gnome bar seems like it has not recognized this uninstall and it still tries to open my drives (actually all items except "Network" and "Computer") with PCManFM.Since there is no such application anymore it just gives me an error message.Nowadays, I cant remember the message cuz i tried to re-install and remove PCManFM once more and now places menu tries to open items with VLC Media PLayer!.

I searched for a config file that includes default applications for places menu items but had no luck locating it.I'd appreciate if anyone can point me its location or can come up with a different solution.Thanks.

---

### Post by sigurnjak on 2008-12-10
Have you tried kill all nautilus  ? I think is a right command ?

---

### Post by Asph on 2008-12-11
> **sigurnjak said:**
> Have you tried kill all nautilus  ? I think is a right command ?
no, i didn't and i doubt that would work. Maybe you've misread it mate, nautilus is my only file manager atm and i want to make it default again for all file managing tasks. However, after installing PCMan File Manager it took over most of the folder shortcuts, especially in places menu. But killing/removing/autoremoving/purging PCManFM doesnt change it, the shortcuts still want to open with it and when they cant, they somehow decide to open with vlc media player.

---

### Post by sigurnjak on 2008-12-11
If you kill nautilus it may try reestablishing  links . Also try reverse of this :
[http://www.ubuntugeek.com/how-to-replace-nautilus-with-pcman-file-manager-in-ubuntu.html](http://www.ubuntugeek.com/how-to-replace-nautilus-with-pcman-file-manager-in-ubuntu.html)

---

### Post by Asph on 2008-12-11
> **sigurnjak said:**
> If you kill nautilus it may try reestablishing  links . Also try reverse of this :
[http://www.ubuntugeek.com/how-to-replace-nautilus-with-pcman-file-manager-in-ubuntu.html](http://www.ubuntugeek.com/how-to-replace-nautilus-with-pcman-file-manager-in-ubuntu.html)
Ok mate, now it made sense to me. I'll try that as soon as I can. Thank you.

---

