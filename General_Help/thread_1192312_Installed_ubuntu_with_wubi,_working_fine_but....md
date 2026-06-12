---
title: "Installed ubuntu with wubi, working fine but..."
date: 2009-06-19
forum: General Help
---

### Post by beatthelastboss on 2009-06-19
Working fine but, for all the little things i try to change/edit, the config files open fine but show up empty! I know I am typing them in correctly, not sure what the problem could be. Thanks for helping out if you can.

---

### Post by cariboo on 2009-06-20
First, if you are trying to edit configuration files anywhere but you home directory, you need to be root, for example if you wanted to edit your /etc/apt/sources.list. Press Alt-F2 and type:

```
gksu gedit /etc/apt/sources.list
```

gksu is the graphical version of sudo, gedit is a text editor, and /etc/apt/soucres.list is the file to be edited.

To edit any files in your home directory you just need to open a text editor and edit.

Most system wide configuration files are located in /etc directory.

---

### Post by beatthelastboss on 2009-06-20
Alt+F2 puts you in root? Its awesome if it does!

Edit: Its still coming up blank! I dont really understand how to be "root", im kinda a linux noob, so bare with me :)

Please, I really need some help, it seems like a lot of things are in the ect directory, and all of them are coming up empty!

---

### Post by beatthelastboss on 2009-06-20
Well, I fixed it, but i'm kind of embarrased at my mistake. Apparently its /etc and not /ect... Oops    ](*,)

---

### Post by oldos2er on 2009-06-20
Using tab completion can help you avoid those misspellings.

---

