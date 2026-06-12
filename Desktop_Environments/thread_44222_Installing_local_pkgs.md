---
title: "Installing local pkgs"
date: 2005-06-25
forum: Desktop Environments
---

### Post by aztektum on 2005-06-25
ok the title should hopefully say it all. I haven't used the apt-get system before, so I'm still learning it, how do I install a single package I have on my hard drive? Anyone have a HOWTO site?

---

### Post by aztektum on 2005-06-25
The voice spoke to him, "Sit down, my son. Let me tell you about 'dpkg'." and all was right in the world.  :grin:

---

### Post by Lunde on 2005-06-25
[QUOTE=aztektum]ok the title should hopefully say it all. I haven't used the apt-get system before, so I'm still learning it, how do I install a single package I have on my hard drive? Anyone have a HOWTO site?[/QUOTE]
 To install .deb file
$ sudo dpkg -i package_file.deb

To uninstall .deb
$ sudo dpkg -r package_name

hope this helps

---

