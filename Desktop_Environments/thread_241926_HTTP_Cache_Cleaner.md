---
title: "HTTP Cache Cleaner"
date: 2006-08-23
forum: Desktop Environments
---

### Post by neko18 on 2006-08-23
Hello. Does anyone know what HTTP Cache Cleaner is? It comes up every once in a while when running Amarok. It's kind of annoying.

---

### Post by neko18 on 2006-08-23
Ok this seems to have fixed it:
```
cd /usr/share/services/
sudo cp http_cache_cleaner.desktop http_cache_cleaner.desktop.ubuntu
sudo echo StartupNotify=false >> http_cache_cleaner.desktop
```

---

### Post by dolphinsonar on 2006-10-13
dont forget to run it as root.

---

### Post by Ramses de Norre on 2006-10-27
This will work without permission errors:
```
cd /usr/share/services/
sudo cp http_cache_cleaner.desktop http_cache_cleaner.desktop.ubuntu
echo StartupNotify=false | sudo tee -a http_cache_cleaner.desktop
```

EDIT: this didn't fix anything here, I still get the http cache cleaner..

---

### Post by motin on 2006-11-05
This thread seems to be a duplicate of [http://ubuntuforums.org/showthread.php?p=1720145](http://ubuntuforums.org/showthread.php?p=1720145)

---

