---
title: "Aptitude uninstalling KDE"
date: 2007-06-29
forum: Desktop Environments
---

### Post by oneofth3m on 2007-06-29
Hi,

I have recently installed kde desktop for Ubuntu 7.04 using the following commands

```
sudo aptitude install kubuntu-desktop
```

Kubuntu-desktop was installed and i was able to use KDE

Later i wanted to install kpoker and issued the following commands.

```

sudo aptitude update
sudo aptitude install kpoker

```

As a habit i pressed 'Y' and it started uninstalling all the kubuntu-desktop applications.

The applications in the KDE menu started disappearing (uninstalled)

Immediately i performed installation again but this time with 

```

sudo aptitiude update
sudo aptitude install kubuntu-desktop

```

After installing KDE again i installed Kpoker using SYNAPTIC

Now everything is fine.

I wanted to know if i install any other applications via aptitude will it unistall KDE again.

---

### Post by kugn on 2007-06-29
Normally installing applications using aptitude doesn't uninstall KDE. But there are times when the repository servers are updating packages when certain packages disappear temporarily. In your case, it might be that the certain pacakges that KDE apps depend on were temporarily off the server, and aptitude, being an aggressive package installer, implores you to remove all those apps that depend on those missing packages.

i guess you need to be more careful about what actions aptitude or apt-get takes before you hit 'Y'

:)

---

### Post by oneofth3m on 2007-06-30
Thanks for sharing the information

---

