---
title: "Firefox and multiple Java versions"
date: 2006-03-22
forum: Desktop Environments
---

### Post by Nick Payne on 2006-03-22
I use different java apps through a web browser that need different versions of Java. One needs 1.42_05 and the other 1.50_04. If I install 1.42_05 (using the instructions at [http://help.ubuntu.com/starterguide/C/ch03s02.html](http://help.ubuntu.com/starterguide/C/ch03s02.html)) then I can access the one app through Firefox ok but the other complains about missing plugin. If I then install 1.50_04 then the second app works ok but the first one now complains about missing plugin. Is it possible to have links to both versions of the Java plugin in /opt/firefox/plugins?

---

### Post by joshuapurcell on 2006-03-22
The problem would be that Firefox wouldn't know which plugin to use for the given application. I would see if having two Firefox installs helps the situation. You can get a complete working binary install of Firefox [here](http://www.getfirefox.com/), then unzip this in a directory that is different from your current install (like some new folder in /opt). Once it is installed then get your needed java plugin installed (the other version would be installed in your first Firefox install). Just make sure not to run both installs of Firefox at the same time... I'm sure that would confuse things a bit. This approach is how the Automatix script installs Firefox 1.5, but I think that script also creates a symbolic link to your current Firefox install as it installs the new version (which would make the same plugins available in both installs).

---

