---
title: "kde on ubuntu"
date: 2006-03-21
forum: Desktop Environments
---

### Post by aditya on 2006-03-21
after i installed kde on ubuntu
some of the things which had led to my frustration
1. when i launched Kpackage to uninstall some of the things which i didnt like 
it prompted me for the (roots) password ??[whats the roots password]
when i entered my passwd it stated that authentication failed !!!!!

2.then i tried to uninstall through synaptic package manager
there the option comes for eg if i wish to uninstall say  "katomic"
it prompts me with the threat ---TO BE REMOVED:
                                                    KDE      
                                                    KDE AMUSEMENTS 
but i dont want that my whole of kde should be removed 


what shall i do???

---

### Post by PsychoTrauma on 2006-03-21
When kpackage asked for you password it was asking for your user password since kubuntu uses sudo.

Try doing:

```
sudo apt-get --purge remove katomic
```

make sure to pay attention to what it wants to remove! If it only wants to remove that package congrads if not push n for no when it asks you if you want to continue.

Did you install kde by using apt-get install kubuntu-desktop?

---

### Post by aditya on 2006-03-21
i entered that password only ,,i dont know why it always displays the message ""authentication failed"

i installed kde through the synaptic package manager

---

### Post by PsychoTrauma on 2006-03-21
[QUOTE=aditya]i entered that password only ,,i dont know why it always displays the message ""authentication failed"

i installed kde through the synaptic package manager[/QUOTE]

It's recommended you get the kubuntu-desktop package so kde will integrate better with ubuntu.

If you really are against that you can set your root password by doing:

```
sudo passwd root
```

---

