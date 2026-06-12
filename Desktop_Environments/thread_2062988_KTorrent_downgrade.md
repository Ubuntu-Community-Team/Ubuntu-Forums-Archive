---
title: "KTorrent downgrade"
date: 2012-09-26
forum: Desktop Environments
---

### Post by henged on 2012-09-26
I'm attempting to downgrade my KTorrent to version 4.1.0 following [these]("http://forum.kde.org/viewtopic.php?f=235&t=106323&sid=3c9e2e45f3a0ff3548a8b49f4e70fb69#p243841") instructions.
i got as far as 'make' and all was going well until....

```
[ 83%] Building CXX object plasma/applet/CMakeFiles/plasma_applet_ktorrent.dir/applet.o                                       
/media/Data/Data/Tech/Apps/ktorrent-4.1.0/plasma/applet/applet.cpp: In member function ‘void ktplasma::Applet::iconClicked()’:
/media/Data/Data/Tech/Apps/ktorrent-4.1.0/plasma/applet/applet.cpp:343:3: error: ‘TaskDict’ is not a member of ‘TaskManager’
/media/Data/Data/Tech/Apps/ktorrent-4.1.0/plasma/applet/applet.cpp:343:25: error: expected ‘;’ before ‘tasks’
/media/Data/Data/Tech/Apps/ktorrent-4.1.0/plasma/applet/applet.cpp:344:21: error: ‘TaskManager::TaskDict’ has not been declared
/media/Data/Data/Tech/Apps/ktorrent-4.1.0/plasma/applet/applet.cpp:344:40: error: expected ‘;’ before ‘i’
/media/Data/Data/Tech/Apps/ktorrent-4.1.0/plasma/applet/applet.cpp:344:58: error: ‘i’ was not declared in this scope
/media/Data/Data/Tech/Apps/ktorrent-4.1.0/plasma/applet/applet.cpp:344:63: error: ‘tasks’ was not declared in this scope
make[2]: *** [plasma/applet/CMakeFiles/plasma_applet_ktorrent.dir/applet.o] Error 1
make[1]: *** [plasma/applet/CMakeFiles/plasma_applet_ktorrent.dir/all] Error 2
make: *** [all] Error 2
```can anyone shed any light?
cheers!

---

### Post by kio_http on 2012-09-27
Why do you want to downgrade in the first place?

---

### Post by henged on 2012-09-27
because particular versions are approved by particular sites
[]("http://ubuntuforums.org/showthread.php?p=12261634#post12261634")

---

### Post by DeceptiveHornet on 2012-09-27
sudo apt-get remove --purge ktorrent and then see if you can fin a deb or version specific edition of it in the repo.

---

### Post by latebeat on 2012-09-27
> **henged said:**
> because particular versions are approved by particular sites
[]("http://ubuntuforums.org/showthread.php?p=12261634#post12261634")

I had the same issue and in the end I switched to qbittorent. You should try it as I find it to download torrents and magnets much faster. It really is like &#956;torrent but for linux.

---

### Post by henged on 2012-09-28
> **latebeat said:**
> I had the same issue and in the end I switched to qbittorent. You should try it as I find it to download torrents and magnets much faster. It really is like &#956;torrent but for linux.

Thanks, qbittorrent looks great, unfortunately it's not an approved client for this particular site...

i'll keep fiddling with ktorrent and see what happens!

---

