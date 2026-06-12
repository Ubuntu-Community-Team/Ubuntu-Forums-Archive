---
title: "Switching to KDE from GNOME"
date: 2006-04-26
forum: Desktop Environments
---

### Post by bforbes on 2006-04-26
I installed Ubuntu 5.10, but I don't like GNOME. I added the KDE sources for apt, and tried:
```

apt-get install kubuntu-desktop

```
But it said that the dependency kdegraphics-kfile-plugins will not be installed. I tried:
```

apt-get install kdegraphics-kfile-plugins

```
And it said libpoppler0c2-qt will not be installed.
```

apt-get install libpoppler0c2-qt

```
And it says that libpoppler0c2 is already installed as a different version, or something to that tune.

I've read a lot of threads about this, but I still haven't been able to get this to work. Can anyone help me work this out?

---

### Post by mjm115 on 2006-04-26
This may be a foolish question, but after you added the sources, did you

> 
apt-get update


Also, have you tried:

> 
sudo aptitude update
sudo aptitude install kubuntu-desktop


Aptitude is a little better at handling dependency issues than apt.  You can also try it through Synaptic.  Hope this works for you.

---

### Post by bforbes on 2006-04-26
I did:

apt-get update

And I tried it through Synaptic, which gave me the same error.

I'll try the aptitude thing.

---

### Post by bforbes on 2006-04-26
Aptitude gave me the same problem. Any other ideas?

---

### Post by Sutekh on 2006-04-26
Don't use the KDE repositories, would be my suggestion.  The error you are getting is probably because there is a mismatch between available packages in the KDE repositories and the Ubuntu ones. 


The Ubuntu repositories contain the kubuntu-desktop meta-package and everything you need for a nice KDE desktop.

Just use your default sources.list and install kubuntu-desktop.

Later you might want this thread to remove GNOME completely.

[Ubuntu Forums - HowTo: Fully Uninstall the ubuntu-desktop meta-package](http://ubuntuforums.org/showthread.php?t=96046)

---

