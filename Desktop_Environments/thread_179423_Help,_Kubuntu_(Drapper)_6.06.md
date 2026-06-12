---
title: "Help, Kubuntu (Drapper) 6.06"
date: 2006-05-19
forum: Desktop Environments
---

### Post by romUdog on 2006-05-19
Hey guys i have a problem and cannot seem to run GnuPG for some reason it doesnt show up in the menu and it wont launch via run or konsole can someone help me?

---

### Post by aysiu on 2006-05-19
Have you tried pasting these commands into the terminal? ```
sudo apt-get update
sudo apt-get install gnupg
```

---

### Post by romUdog on 2006-05-19
[QUOTE=aysiu]Have you tried pasting these commands into the terminal? ```
sudo apt-get update
sudo apt-get install gnupg
```[/QUOTE]


ill try that

Update - i tried it its already installed

---

### Post by aysiu on 2006-05-19
That may be a command-line utility.

If you want a graphical application, try *kgpg*.

---

### Post by romUdog on 2006-05-19
[QUOTE=aysiu]That may be a command-line utility.

If you want a graphical application, try *kgpg*.[/QUOTE]


It doesnt find it either so maybe drapper is not updated good enough? maybe i should switch back to Breezy 5.10 although i do like the new KDE look in 6.06 Dapper and i look forward to it

---

### Post by aysiu on 2006-05-19
Kgpg is in the Universe repositories.

Follow these directions to get them:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

---

### Post by romUdog on 2006-05-19
okay dude i did your updates to that file and now it suddenly finds that file which it didnt before and it is now installed, thanks ALOT! now i can encrypt all my files ^_^

Now why isnt everything showing up in the menu's though?

---

### Post by aysiu on 2006-05-19
[QUOTE=romUdog]
Now why isnt everything showing up in the menu's though?[/QUOTE] It all depends.

Sometimes they show up. Sometimes they don't.

Sometimes there's an entry, but you have to refresh the KMenu to see it.

Sometimes there is no entry, so you have to create it yourself.

---

