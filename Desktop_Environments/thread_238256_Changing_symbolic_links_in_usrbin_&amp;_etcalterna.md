---
title: "Changing symbolic links in /usr/bin &amp; /etc/alternatives"
date: 2006-08-17
forum: Desktop Environments
---

### Post by umonkey on 2006-08-17
Today when I ran the Debian Reference program it loaded the html files in Opera instead of Firefox. I thought this was strange, but I assume that an install script changed something when I installed Opera. After looking at the debian-reference shell script I noticed that it was really executing a symbolic link /usr/bin/x-www-browser which points to a similar link in /etc/alternatives which points to the actual opera executable. 

I'd like to change this link to refer to Firefox. But before I do that I would like to know if Ubuntu and/or Gnome has a system for managing these generic symbolic links. Perhaps a gui program for setting your preferred default programs. If so I would prefer to use that instead of modifying the link directly with ln. There are actually quite of few of these generic application links in /usr/bin and /etc/alternatives.

---

### Post by Ramses de Norre on 2006-08-17
```
sudo update-alternatives --config x-www-browser
```
Or install galternatives which provides a GUI.

---

### Post by umonkey on 2006-08-17
Thanks. That's exactly what I was looking for. :)

---

### Post by sudipta_cht on 2008-06-30
If you're interested, you could also try galternatives:
> sudo apt-get install galternatives
gksudo galternatives

---

