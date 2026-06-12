---
title: "gtkmozembed don't use libflashplayer.so 10.0.0.569 x86 on  x64 system"
date: 2008-12-19
forum: Desktop Environments
---

### Post by BenderIII on 2008-12-19
Hi,

apologies if this is not the correct section of the forum.


I have the problem that gtkmozembed is not using the updated libflashplayer.so anymore.

What I have done:
  I updated the libflashplayer.so to the latest version 10.0.0.569 with the help of the getlibs-all.deb to avoid problems with the x86 version of the latest flashplayer on my ubuntu x64, as there is no x64 version from adobe yet :( . After executing the getflash script from getflash10-.10.tar.gz I have an upgraded flashplayer and got it working in firefox with no hassle.

The python script I have, uses the gtkmozembed from python 2.5 and creates a profile directory as required. Looking into the pluginreg.dat I see that it has no entry for the ndwrapper.flashplugin.so like in the firefox/pluginreg.dat . 
Deleting the gtkmozembed/pluginreg.dat has no effect. 
Also adding the ndwrapper.flashplugin.so part manually into the gtkmozembed/pluginreg.dat won't make it run. It still can't find the application/x-shockwave-flash plugin. :mad:

How can I change the plugins used by the gtkmozembed engine? :-? Haven't found anything yet. Not on the [www.pygtk.org/pygtkmozembed/](www.pygtk.org/pygtkmozembed/) nor somewhere else.

---

