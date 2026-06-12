---
title: "Update 404 error?"
date: 2006-08-02
forum: Desktop Environments
---

### Post by cjtenny on 2006-08-02
root@camsbox:~# apt-get update
yields some problems.... it goes at 9 bytes per second?

then:
root@camsbox:~# apt-get -y upgrade > output
gives this:
```
Reading package lists...
Building dependency tree...
The following packages will be upgraded:
  eog file-roller firefox firefox-gnome-support gnome-accessibility-themes
  gnome-applets gnome-applets-data gnome-games gnome-games-data gnome-menus
  gnome-session gnome-themes gtk2-engines-clearlooks gtk2-engines-crux
  gtk2-engines-highcontrast gtk2-engines-industrial
  gtk2-engines-lighthouseblue gtk2-engines-mist gtk2-engines-pixbuf
  gtk2-engines-redmond95 gtk2-engines-smooth gtk2-engines-thinice gtkhtml3.8
  kdenetwork-filesharing kdenetwork-kfile-plugins kdnssd kopete kpf kppp krdc
  krfb language-pack-en language-pack-en-base language-pack-gnome-en
  language-pack-gnome-en-base libeel2-2 libeel2-data libgnome-menu2
  libgtk2.0-0 libgtk2.0-bin libgtk2.0-common libgtk2.0-dev libgtkhtml3.8-15
  libnautilus-burn3 libnspr4 libnss3 libtiff4 libtiff4-dev libtiffxx0c2
  libtotem-plparser1 nautilus-cd-burner python-gmenu totem totem-gstreamer
  yelp
55 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 1867kB/43.1MB of archives.
After unpacking 184kB of additional disk space will be used.
Err http://us.archive.ubuntu.com dapper-updates/main libtotem-plparser1 1.4.3-0ubuntu1
  404 Not Found [IP: 146.137.96.7 80]
Err http://us.archive.ubuntu.com dapper-updates/main totem-gstreamer 1.4.3-0ubuntu1
  404 Not Found [IP: 146.137.96.7 80]
Err http://us.archive.ubuntu.com dapper-updates/main totem 1.4.3-0ubuntu1
  404 Not Found [IP: 146.137.96.7 80]

```

anybody know why I'm getting a 404?

---

### Post by bmonkey on 2006-08-02
no idea :( i been having the same problem trying to install zenity.. :(

W: Failed to fetch [http://za.archive.ubuntu.com/ubuntu/pool/main/z/zenity/zenity_2.14.3-0ubuntu1_i386.deb](http://za.archive.ubuntu.com/ubuntu/pool/main/z/zenity/zenity_2.14.3-0ubuntu1_i386.deb)
  404 Not Found

Yesterday i had that for about 15 other updates.. today thank god the rest worked.. its just that for me now :( i think its a server problem :/

---

### Post by kerry_s on 2006-08-02
take out the country code in /etc/apt/sources.list(example)->

[http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/)

to

[http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)

---

### Post by cjtenny on 2006-08-02
thanks

---

