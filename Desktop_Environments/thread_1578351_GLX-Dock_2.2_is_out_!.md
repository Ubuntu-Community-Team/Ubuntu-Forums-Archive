---
title: "GLX-Dock 2.2 is out !"
date: 2010-09-20
forum: Desktop Environments
---

### Post by fabounet on 2010-09-20
Finally, the 2.2 version of GLX-Dock is out just in time for Maverick.
you can install it easily with our repository :

```
sudo -v
echo "deb http://repository.glx-dock.org/ubuntu $(lsb_release -sc) cairo-dock" | sudo tee -a /etc/apt/sources.list
wget -q http://repository.glx-dock.org/cairo-dock.gpg -O- | sudo apt-key add -
sudo apt-get update
sudo apt-get install cairo-dock cairo-dock-plug-ins
```

A small picture of what you can have with this new version:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=169520&d=1284543064[/IMG]

---

### Post by nilarimogard on 2010-09-20
Where can I find a complete list of new features (also what's new since the beta :D)?

---

### Post by fabounet on 2010-09-21
there is no complete list (because it would be too long ^^ ) but a good overview can be read here: [http://www.glx-dock.org/]("http://www.glx-dock.org/")
no big news since the beta, but a lot of polishing and bug-fixing (as much as possible before the freeze of Ubuntu 10.10) :-)

---

