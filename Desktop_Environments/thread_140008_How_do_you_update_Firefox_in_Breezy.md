---
title: "How do you update Firefox in Breezy?"
date: 2006-03-05
forum: Desktop Environments
---

### Post by mark.logue on 2006-03-05
I've tried the Synaptic Package Manager, but it believes v1.0.7 to be the latest Firefox.  I also tried copying the Firefox-1.5 folder into /usr/lib, but it won't run from there either.  Is Firefox 1.5 unstable for Ubuntu-Breezy?

---

### Post by adamkane on 2006-03-05
There are HOWTOs and WIKIs that explain how to "install" Firefox 1.5, but it isn't supported, and you may run into installation problems. Use the HOWTOs or try a new service, that allows you to use 1.5 without actually installing it.

[https://wiki.ubuntu.com/FirefoxNewVersion]("https://wiki.ubuntu.com/FirefoxNewVersion")
[http://klik.atekon.de]("http://klik.atekon.de")

---

### Post by BeeWee on 2006-03-05
You also can use [automatiKs](http://ubuntuforums.org/showthread.php?p=794355) (for KDE) or [Automatix](http://ubuntuforums.org/showthread.php?t=138405) (for GNOME) to install Firefox 1.5

BeeWee

---

### Post by mark.logue on 2006-03-07
Awesome!  Automatix worked like a champ.  

I tried the various HOWTO's before posting but they were lame.  Thanks for giving me a *real* solution.

---

### Post by towsonu2003 on 2006-03-07
[QUOTE=mark.logue]
(...) HOWTO's (...) were lame.[/QUOTE]
how?

---

### Post by Luke on 2006-03-07
[QUOTE=mark.logue]I tried the various HOWTO's before posting but they were lame.  Thanks for giving me a *real* solution.[/QUOTE]

[https://wiki.ubuntu.com/FirefoxNewVersion](https://wiki.ubuntu.com/FirefoxNewVersion) worked great for me. i hope i don't have *fake* firefox. :roll:

---

### Post by WelterPelter on 2006-03-07
Automatix is the way to go.

---

### Post by towsonu2003 on 2006-03-07
[QUOTE=WelterPelter]Automatix is the way to go.[/QUOTE]
people have choices. your way won't work for me ;)


hmmm, anyway, OP solved his/her issue, so all is good

---

### Post by Ramses de Norre on 2006-03-07
I second that, I don't really like the automatix way of working neither.
But I guess it's very helpful for some people.

---

### Post by aysiu on 2006-03-07
My guess is that Automatix works just fine, but it does seem a bit of overkill if someone just wants to install Firefox.

If someone says, "I want Firefox 1.5, all sorts of multimedia codecs, and Limewire, and a bunch of other programs," I'd recommend Automatix in a second.

If someone says, "How do I install Firefox 1.5?" recommending Automatix to that person seems to me like recommending someone install a satellite dish if she just wants to watch one episode of *The L Word*.

---

### Post by WelterPelter on 2006-03-07
[QUOTE=towsonu2003]people have choices. your way won't work for me ;)
[/QUOTE]

No argument there. I just recommend it as the fast way for those, like me, who may not be wizards at setup. I'm sure as my experience matures, I'll prefer to set most things up myself.

---

### Post by arnieboy on 2006-03-08
[QUOTE=aysiu]My guess is that Automatix works just fine, but it does seem a bit of overkill if someone just wants to install Firefox.

If someone says, "I want Firefox 1.5, all sorts of multimedia codecs, and Limewire, and a bunch of other programs," I'd recommend Automatix in a second.

If someone says, "How do I install Firefox 1.5?" recommending Automatix to that person seems to me like recommending someone install a satellite dish if she just wants to watch one episode of *The L Word*.[/QUOTE]
Automatix is not an overkill... It installs Firefox 1.5 along with all its plugins that anyone would need. Automatix does not force you to install all options at one go. U choose what u want to install.
Hope this makes it clearer.

---

### Post by adamkane on 2006-03-08
Klik allows you to run Firefox from a single file. It doesn't install or alter your setup. You can still use extensions, search plugins, and Firefox 1.5 becomes your default browser. 

Only drawback is that I can't delete the amazon and ebay search plugins. The klik files are mounted on a small cramfs file system, and cramfs is read-only, so some files aren't editable/deletable. This doesn't affect usability. It's an elegant way to preserve Firefox 1.0 within Ubuntu 5.10.

Install Klik
klik.atekon.de

Install Firefox 1.5
klik.atekon.de/firefox

Create a Gnome launcher
Panel -> Add to Panel... -> Custom Application Launcher 

Name: Firefox
Command: /home/<username>/.zAppRun /<path to>/firefox.cmg
Icon: /<path to>/firefox.png

---

### Post by towsonu2003 on 2006-03-08
[QUOTE=adamkane]Klik allows you to run Firefox from a single file. It doesn't install or alter your setup. [/QUOTE]
just a note. it alters /etc/fstab, but I don't know what else it alters... also, it didn't work for me -don't know why-.

---

