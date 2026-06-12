---
title: "How to isntall Opera Web browser"
date: 2009-01-09
forum: General Help
---

### Post by benste on 2009-01-09
Hy folks, I know I installed opera several weeks ago.

All was fin, but now it seems that it disappeared with an update.
Opera isn't aviable either via Synaptic or command line based apt-get

German error message of APT:
```
benste@VAIO-fe31m:~$ sudo apt-get install opera 
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut       
Lese Status-Informationen ein... Fertig
Paket opera ist nicht verfügbar, wird aber von einem anderen
Paket referenziert. Das kann heißen, dass das Paket fehlt, dass es veraltet
ist oder nur aus einer anderen Quelle verfügbar ist.
E: Paket opera hat keinen Installationskandidaten

```

Is it really removed? [https://help.ubuntu.com/community/OperaBrowser]("https://help.ubuntu.com/community/OperaBrowser")says that it must be aviable through ubuntu partner resporistorys but it isn't!

---

### Post by Ellaine on 2009-01-09
Go to Opera.com and download 9.63 in 32bit or 64bit in any language.

---

### Post by benste on 2009-01-09
:-)
This would be too easy,
I don't want to install 3rd party software if it is possible to cover it via synaptic - and update-manager

---

### Post by eriqjaffe on 2009-01-09
You could always add the Opera repository (there are instructions on that page you linked to), and then install it through Synaptic/apt.

---

### Post by mssever on 2009-01-09
Add the Opera repository to your /etc/apt/sources.list: ```
# Opera
deb http://deb.opera.com/opera/ stable non-free
```Then, ```
sudo aptitude update && sudo aptitude install opera
```

---

### Post by -grubby on 2009-01-09
> **benste said:**
> :-)
This would be too easy,
I don't want to install 3rd party software if it is possible to cover it via synaptic - and update-manager

The website has deb packages. If you install it via the package from the Opera website, you will still be able to remove it with Synaptic.

---

### Post by Arup on 2009-01-09
Ubuntu used to come with Opera in repos, sadly it has been removed due to some strange reason, you have to install it via deb file from Opera site.

---

### Post by benste on 2009-01-09
That's my important part,
it was installed,
and is no removed because strangly it disappeared from the repos

Of course I'm able to install opera with some tweaks like adding another package source or using the manual deb file, but isn't it something like a bug that Opera disappeared from the repos AND automaticly deinstalled because of that?

---

### Post by scorp123 on 2009-01-09
> **benste said:**
> All was fin, but now it seems that it disappeared with an update.According to this thread Opera was removed, yes:
[http://ubuntuforums.org/showthread.php?p=6382111#post6382111](http://ubuntuforums.org/showthread.php?p=6382111#post6382111)

You could add Opera's repos directly and then still install it via "apt-get", just as other have already pointed out.

---

