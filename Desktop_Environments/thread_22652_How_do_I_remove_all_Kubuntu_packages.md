---
title: "How do I remove all Kubuntu packages?"
date: 2005-03-28
forum: Desktop Environments
---

### Post by fheinsen on 2005-03-28
Hi -- Kubuntu is great... unfortunately I need to reclaim a bit of hard drive space in this machine (it's a 4-yr old laptop...) and (reluctantly) have to remove KDE.

What is the easiest/fastest way to remove all Kubuntu packages?

---

### Post by telmo on 2005-03-28
You want to remove the OS or just KDE in Ubuntu?
Can't you do it with synaptic? (you have gnome installed)
Don't worry in removing ubuntu-desktop... that doesn't matter!

Hope this helps!

---

### Post by bored2k on 2005-03-28
[QUOTE=telmo]You want to remove the OS or just KDE in Ubuntu?
Can't you do it with synaptic? (you have gnome installed)
Don't worry in removing ubuntu-desktop... that doesn't matter!

Hope this helps![/QUOTE]
 I want to understand the problem comes from an apt-get installed kubuntu-desktop.
Problem is, apt-get remove kubuntu-desktop is just like ubuntu-desktop, you basically remove nothing.

I haven't found a simple way to do this other than manually removing the packages. Maybe someone has and would like to enlighten us ?

---

### Post by apokryphos on 2005-03-29
You can use the *debfoster* command to weed out unnecessary Debian packages brought in by metapackages (i.e. kubuntu-desktop).

---

### Post by fheinsen on 2005-03-29
[QUOTE=telmo]You want to remove the OS or just KDE in Ubuntu?
Can't you do it with synaptic? (you have gnome installed)
Don't worry in removing ubuntu-desktop... that doesn't matter!

Hope this helps![/QUOTE]

I'd like to remove all kubuntu-desktop packages without manually having to remove each package one by one.  Is this possible?

---

### Post by fheinsen on 2005-03-29
[QUOTE=apokryphos]You can use the *debfoster* command to weed out unnecessary Debian packages brought in by metapackages (i.e. kubuntu-desktop).[/QUOTE]

Thank you...  *debfoster* is a possible solution; however, it requires that I explicitly state which installed packages I want to keep on my system. 

Is there a simpler/faster way to remove all the packages in a meta-package such as kubuntu-desktop?

---

### Post by fheinsen on 2005-03-29
[QUOTE=bored2k]I want to understand the problem comes from an apt-get installed kubuntu-desktop.
Problem is, apt-get remove kubuntu-desktop is just like ubuntu-desktop, you basically remove nothing.

I haven't found a simple way to do this other than manually removing the packages. Maybe someone has and would like to enlighten us ?[/QUOTE]

Yup.  Sorry to hear  you haven't found a simple solution either.. I guess I'll have to give *debfoster* a try.

---

### Post by apokryphos on 2005-03-29
[QUOTE=fheinsen]Thank you...  *debfoster* is a possible solution; however, it requires that I explicitly state which installed packages I want to keep on my system. 

Is there a simpler/faster way to remove all the packages in a meta-package such as kubuntu-desktop?[/QUOTE]
Well, yes; you use it in conjugation with the ubuntu-desktop/base metapackage.

---

### Post by fheinsen on 2005-03-29
[QUOTE=apokryphos]Well, yes; you use it in conjugation with the ubuntu-desktop/base metapackage.[/QUOTE]

The problem is I have tons of other little packages I've added over the past six months...  What the hey, I'll just go through them one by one and clean up my system.

Thank you for your help.

---

### Post by fdoving on 2005-03-30
[QUOTE=fheinsen]The problem is I have tons of other little packages I've added over the past six months...  What the hey, I'll just go through them one by one and clean up my system.

Thank you for your help.[/QUOTE]
 I'd recommend: apt-get --purge remove libartsc0

That won't leave much KDE stuff... maybe some artwork packages or something.. with no depends.. but most of KDE is gone.

Good luck.

---

### Post by ubuntu_demon on 2005-03-30
[QUOTE=fdoving]I'd recommend: apt-get --purge remove libartsc0

That won't leave much KDE stuff... maybe some artwork packages or something.. with no depends.. but most of KDE is gone.

Good luck.[/QUOTE]
 regarding the debfoster way :

do "sudo debfoster -q" to assume yes to all questions. Then edit the /var/lib/debfosterkeepers and remove the line kubuntu-desktop and other lines with packages you want to remove. Only packages that don't depend on other packages are listed so the list won't be very long unless you broke some meta-package like ubuntu-desktop.

then run debfoster once more ("sude debfoster") and it will ask you what to do with kubuntu-desktop.Just choose purge.

You can also install deborphan and use "deborphan -a" to see a list of orphaned packages. Some of them you'll want to remove. Don't remove them unless you are sure.

the other way I would use :
sudo apt-get --purge remove kdebase kdelibs4 libqt3c102-mt arts libartsc0

See also this link : [http://www.ubuntuforums.org/showthread.php?t=22697](http://www.ubuntuforums.org/showthread.php?t=22697)

---

### Post by fheinsen on 2005-03-30
[QUOTE=demon666_nl]regarding the debfoster way : ... do "sudo debfoster -q" to assume yes to all questions. Then edit the /var/lib/debfosterkeepers and remove the line kubuntu-desktop and other lines with packages you want to remove. Only packages that don't depend on other packages are listed so the list won't be very long unless you broke some meta-package like ubuntu-desktop ... then run debfoster once more ("sude debfoster") and it will ask you what to do with kubuntu-desktop.Just choose purge.[/QUOTE]

demon, thank you for the detailed response... 

I ended up doing it manually via debfoster.  The list of packages ended up being  a bit long -- not because I had broken any meta packages, but rather because over the past six months I had installed a lot of one-off packages that aren't part of any of the ubuntu-* or kubuntu-* meta-packages.

---

### Post by ubuntu_demon on 2005-03-31
[QUOTE=fheinsen]demon, thank you for the detailed response... 

I ended up doing it manually via debfoster.  The list of packages ended up being  a bit long -- not because I had broken any meta packages, but rather because over the past six months I had installed a lot of one-off packages that aren't part of any of the ubuntu-* or kubuntu-* meta-packages.[/QUOTE]
 debfoster rules :)
It's one of the first things I learned to install. 

PS when I myself removed kunbut-deskop I discoverd I had to reinstall ubuntu-desktop as well .. please check for this

---

### Post by vinil on 2005-11-20
[QUOTE=fdoving]I'd recommend: apt-get --purge remove libartsc0

That won't leave much KDE stuff... maybe some artwork packages or something.. with no depends.. but most of KDE is gone.

Good luck.[/QUOTE]


i wanted to uninstall kde too... and this code help me a lot .. thanks

---

