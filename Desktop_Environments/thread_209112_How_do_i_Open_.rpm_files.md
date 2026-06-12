---
title: "How do i Open *.rpm files?"
date: 2006-07-04
forum: Desktop Environments
---

### Post by sean_ on 2006-07-04
I'm not sure if this belongs here, but I searched the forums, and searched google and it didn't help. How do I open *.RPM files?

---

### Post by aysiu on 2006-07-04
```
sudo aptitude update
sudo aptitude install alien
sudo alien -i *.rpm
```

---

### Post by Glass_Onion on 2006-07-04
You can't. Though you can convert them into *.DEB files.

[http://ubuntuguide.org/wiki/Dapper#How_to_convert_.rpm_files_to_.deb_files](http://ubuntuguide.org/wiki/Dapper#How_to_convert_.rpm_files_to_.deb_files)

EDIT: Ah, just about got beat. :lol:

---

### Post by aysiu on 2006-07-04
[QUOTE=Glass_Onion]You can't. Though you can convert them into *.DEB files.

[http://ubuntuguide.org/wiki/Dapper#How_to_convert_.rpm_files_to_.deb_files](http://ubuntuguide.org/wiki/Dapper#How_to_convert_.rpm_files_to_.deb_files)

EDIT: Ah, just about got beat. :lol:[/QUOTE]
That's one way to do it, but it creates an extra step that will just prompt sean to ask, "How do I install a .deb file?"

By the way, RPMs should be your second-to-last resort.

#1 Repositories
#2 .deb files
#3 .rpm files
#4 .tar.gz files

For more info, go here: [http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by Glass_Onion on 2006-07-04
Suppose. Does your way a different method of doing what UbuntuGuide says or does it install the *.RPM?

---

### Post by aysiu on 2006-07-04
[QUOTE=Glass_Onion]Suppose. Does your way a different method of doing what UbuntuGuide says or does it install the *.RPM?[/QUOTE]
```
sudo alien -i *.rpm
``` installs all the .rpm files in that folder.

Of course, if you want to install a very specific .rpm, you specify the name: ```
sudo alien -i packagename.rpm
```

So this is the difference: ```
sudo alien packagename.rpm
sudo dpkg -i packagename.deb
``` versus ```
sudo alien -i packagename.deb
```

---

### Post by Jagot on 2006-07-04
[QUOTE=Glass_Onion]Suppose. Does your way a different method of doing what UbuntuGuide says or does it install the *.RPM?[/QUOTE]

aysiu's method installs the rpm - no converting to .deb.

EDIT: aysiu beat me to it and did it better.

---

### Post by sean_ on 2006-07-04
Got it to work, converted it to alien and installed it using the .deb

---

