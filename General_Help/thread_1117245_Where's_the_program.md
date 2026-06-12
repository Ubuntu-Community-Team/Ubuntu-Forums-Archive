---
title: "Where's the program?"
date: 2009-04-05
forum: General Help
---

### Post by Bre Ntt on 2009-04-05
If I use the package installer to install a GUI program (specifically I installed macsyma and maxima) but it for some reason does not show up in my applications menu so

 A) Where can I find the file that starts the program (whatever that would be called, the equivalent of an .exe?)? And 

B) How can I add it to my applications menu.

I was able to find the console verision of maxima after installing both with Synaptic (maxima is in /sbin) but I can't find Macsyma, I found the folder but its just 3 XML files that do nothing when you open them. 

Is this a bug in the package manager for Macsyma perhaps? Or am I not getting something about how software is installed and there is an executable file hiding somewhere?

And C) there doesn't seem to be any easily searchable documentation on this. I searched 'Adding programs to application folder' and a few other things...nothing

---

### Post by zvacet on 2009-04-05
You can find where packages are installed with this commands

```
locate Macsyma
```

```
sudo find / -name Macsyma
```

or you can go to the synaptic and find desired package and right click on it and select properties.There you will seee where is installed.

To add it to applications menu go to the sys>preferences>main menu and on the left select group in whitch you want your package to show.Then on the right side select new item and  under command browse t othe place where package is installed(you alreadx know that from first step).Add name and if you can find icon(look is /usr/share/pixmaps) you have icon in apps menu.

---

