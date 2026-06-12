---
title: "zotero broke firefox; java problem?"
date: 2011-03-03
forum: Desktop Environments
---

### Post by asdir on 2011-03-03
I had problems installing the Zotero-Plugin from [here](http://www.zotero.org/support/word_processor_plugin_installation#openoffice_libreoffice_neooffice), so I followed their linux guide [here](http://www.zotero.org/support/word_processor_plugin_troubleshooting?s=installed#component_loading_error_on_ubuntu_linux) (scroll down to "component loading error") and installed java via
 ```
sudo apt-get install sun-java6-plugin sun-java6-jre
```
and set it as a default plugin via
```
sudo ln -s /usr/lib/jvm/java-6-sun/jre/lib/i386/libnpjp2.so /usr/lib/mozilla/plugins/
```

Now some stuff in my firefox does not work anymore, among those the youtube-player.

Can anyone tell me how to reverse what I've done (since it did not fix the original problem anyway)?

Edit: As long as a video is embedded it seems to work, though.

---

