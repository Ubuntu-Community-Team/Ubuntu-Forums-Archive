---
title: "Various admin privileges problems problems on KDE"
date: 2007-11-05
forum: Desktop Environments
---

### Post by krelian on 2007-11-05
This has been happening ever since I installed Gutsy (clean install no an upgrade). When I login and my session starts I get popups to enter my admin password or just information that some file cannot be written because of no admin rights.
- Kdesudo ("no command arguments supplied"), 
- knetworkmanager ("will not save configuration, configuration file is not writable),
- Kmix (asks to enter admin password through kdesudo, the command name is kmix- session "long session number"
- Katapult - the same as kmix

and some other pop up windows that I cannot remember at the moment. It looks like some of kde's config files are registered as belonging to root so that nothing can be written to them when I log on with my regular user.

I also need to mention that this is happening every time and is not only the result of one bad shutdown or something similar.

Any ideas?

---

### Post by sisco311 on 2007-11-05
looks like an ownership issue. try:
```
sudo chown -R username\: /home/username
```

---

### Post by maybeway36 on 2007-11-05
Install this package:
[http://ubuntu.lnix.net/misc/kdesudo_1.1-0ubuntu5_i386.deb]("http://ubuntu.lnix.net/misc/kdesudo_1.1-0ubuntu5_i386.deb")
There's a "newer" version in gutsy-proposed, but it seems to be a regression. see: [https://bugs.launchpad.net/ubuntu/+source/kdesudo/+bug/155032]("https://bugs.launchpad.net/ubuntu/+source/kdesudo/+bug/155032")

---

