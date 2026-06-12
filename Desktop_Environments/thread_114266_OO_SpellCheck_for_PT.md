---
title: "OO SpellCheck for PT"
date: 2006-01-08
forum: Desktop Environments
---

### Post by lamego on 2006-01-08
Hello,
I am trying to add to add Portuguese (Portugal) spellcheck support for OpenOffice, from Synaptic I have installed the PT langage packs, however the included lang pack for OO was PT (Brasilian). I already installed all PT spellcheck related packages but I still dont get the PT (Portugal) spellcheck on OO.

I have been reading:
[http://lingucomponent.openoffice.org/download_dictionary.html](http://lingucomponent.openoffice.org/download_dictionary.html)

Which points me to "File -> Wizards -> Install new dictionaries" .
The above menu option does not work (nothing happens).
Could someone try this ? Should I fill a bug report for this ?

Thanks

---

### Post by dcstar on 2006-01-08
[QUOTE=lamego]Hello,
I am trying to add to add Portuguese (Portugal) spellcheck support for OpenOffice, from Synaptic I have installed the PT langage packs, however the included lang pack for OO was PT (Brasilian). I already installed all PT spellcheck related packages but I still dont get the PT (Portugal) spellcheck on OO.

I have been reading:
[http://lingucomponent.openoffice.org/download_dictionary.html](http://lingucomponent.openoffice.org/download_dictionary.html)

Which points me to "File -> Wizards -> Install new dictionaries" .
The above menu option does not work (nothing happens).
Could someone try this ? Should I fill a bug report for this ?

Thanks[/QUOTE]
No, a lot of people have this issue in the current OO version that Ubuntu uses.

Go to: [http://ooodi.sourceforge.net/](http://ooodi.sourceforge.net/) and get the OOodi macro dictionary installer, it should solve your problem.

There is also a newer version of 00 for Ubuntu available at this repository (add the line to the end of your /etc/apt/sources.list) file:

deb [http://people.ubuntu.com/~doko/OOo2](http://people.ubuntu.com/~doko/OOo2) ./

---

### Post by lamego on 2006-01-08
Is there some easier way ?
I had to install a lot of development packages for this tool and now when I press "Ok" on the initial dialog nothing happens.

---

### Post by dcstar on 2006-01-08
[QUOTE=lamego]Is there some easier way ?
I had to install a lot of development packages for this tool and now when I press "Ok" on the initial dialog nothing happens.[/QUOTE]
??

The file is a OO macro, you download it and open it - no development packages involved.

---

### Post by lamego on 2006-01-09
I don't see any reference to a macro on [http://ooodi.sourceforge.net/](http://ooodi.sourceforge.net/) .
Just a "A GTK+ and libcurl based installer for OpenOffice.org on Unix." .

---

