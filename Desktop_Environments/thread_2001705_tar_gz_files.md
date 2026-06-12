---
title: "tar gz files"
date: 2012-06-11
forum: Desktop Environments
---

### Post by kakashi_12 on 2012-06-11
How the heck to install these, I can never figure it out. This is either a plug-in for the browser or something that runs in the background. In Windows, it runs in the system tray.

It is a plugin that allows me to vpn into work through my browser. I never understood how to work these tar gz files and even where to extract them to.

---

### Post by codemaniac on 2012-06-11
Software packages in Linux are historically packaged in tarballs unlike .exe in Windows .The below link may guide you .

[http://www.cyberciti.biz/faq/install-tarballs/](http://www.cyberciti.biz/faq/install-tarballs/)

---

### Post by sudodus on 2012-06-11
You can probably open it with the archiver, which should be automatic using the file browser (Nautilus). Then you can see if there is some instruction file, readme, document etc. Otherwise there should be some instruction at the web-site where you found the file.

The next step is probably to expand the content to some arbitrary directory, for example a subdirectory in 'Downloads'.

Often there is a shell-script file, that should be run as superuser
```
sudo install.sh
``` or something similar, but the details can vary a lot between the tarballs.

---

### Post by kakashi_12 on 2012-06-12
Thanks for the excellent guide. That helped. It installed in the proper place I see under usr. And it shows up under my Applications list. But the app/plugin itself still is not working for some reason.

Nevermind, got it to work.....

sudo cp /usr/share/ca-certificates/mozilla/* /usr/lib/ICAClient/keystore/cacerts/

[https://help.ubuntu.com/community/CitrixICAClientHowTo](https://help.ubuntu.com/community/CitrixICAClientHowTo)

---

