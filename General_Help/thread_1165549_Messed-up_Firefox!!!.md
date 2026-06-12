---
title: "Messed-up Firefox!!!"
date: 2009-05-20
forum: General Help
---

### Post by terryq on 2009-05-20
Can anybody advise if there is a method to restore all Firefox default settings back without uninstalling the software?

---

### Post by themusicalduck on 2009-05-20
Go to your home folder, press ctrl+h, find the .mozilla folder and delete it. (Or just change the name if you want to keep a backup of the current configuration.)

Restart firefox and it will create a new config file so that it'll be like a new install.

---

### Post by fooman on 2009-05-20
well,  uninstalling the software would not help anyways.  your messed-up profile would still be the default configuration.

deleting the ~/.mozilla folder would reset all your firefox settings to default....you should backup your bookmarks/favorites before proceeding with that,  as they will also be wiped out.

---

### Post by terryq on 2009-05-20
Tried deleting ~/.mozilla folder but it didn't work. Fortunately I backed it up and restored to as it was. Any other suggestions would be appreciated very much.

---

### Post by terryq on 2009-05-20
Don't want to sound stupid but this is supposed to work :

On Linux , load up Terminal and type in:
/path/to/firefox/firefox -safe-mode

Can anybody translate please? I mean what is the "/path/to/firefox/firefox" part?

---

### Post by lovinglinux on 2009-05-20
You can also open the terminal and run this command:

```
firefox -P
```

It will launch the Firefox Profile Manager, from where you can create a new clean profile and delete the old one if you want.

BTW, you don't need "/path/to/firefox/firefox" (which is the path to firefox executable). If you want to run firefox in safe mode, just run this:
```

firefox -safe-mode
```

---

### Post by terryq on 2009-05-21
Thank you very much indeed Lovinglinux!!!!!!!!!!!

---

