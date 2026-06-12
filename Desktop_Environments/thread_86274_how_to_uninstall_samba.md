---
title: "how to uninstall samba"
date: 2005-11-04
forum: Desktop Environments
---

### Post by mxyzptlk on 2005-11-04
i think i messed up my samba is there any way to uninstall it and install again

im stuck with my network almost start killing people by crazyness

hehe just kidding

10x in advanced

---

### Post by Ampersand on 2005-11-04
Run Synaptic, right click on samba and select 'mark for complete removal' and apply. Then install samba again. This should give you a fresh set of config files.

---

### Post by mxyzptlk on 2005-11-05
thanks a lot now its working

from the XP box i can see the Ubuntu server and the shared files, but i cannot see the XP from ubuntu

and i cannot print neither from here nor from there.

and i lost the shared internet connection and the XP is without internet service im afraid that if re-install firestarter i will lost samba.

any suggestion


10x in adavanced

---

### Post by QWERTY on 2005-11-05
I have tried to install Samba without success. I can't see network shares in Network filebrowser or samba shares from Window XP.

Any suggestions?
Thanks

---

### Post by manicka on 2005-11-05
[QUOTE=QWERTY]I have tried to install Samba without success. I can't see network shares in Network filebrowser or samba shares from Window XP.

Any suggestions?
Thanks[/QUOTE]

[http://doc.gwos.org/index.php/Share_files_using_Samba](http://doc.gwos.org/index.php/Share_files_using_Samba)

---

### Post by Ampersand on 2005-11-05
[QUOTE=mxyzptlk]thanks a lot now its working

from the XP box i can see the Ubuntu server and the shared files, but i cannot see the XP from ubuntu

and i cannot print neither from here nor from there.

and i lost the shared internet connection and the XP is without internet service im afraid that if re-install firestarter i will lost samba.

any suggestion


10x in adavanced[/QUOTE]

Could you see the XP shared folder before? What happens if you open a terminal and run
```
sudo mount -t smbfs //XPcomputername/sharedfoldername /mountpoint
```

(replacing XPcomputername, sharedfoldername and mountpoint with the name or IP address of the XP computer, the name of the folder on that computer, and the directory on the Ubuntu computer you want it mounted to).

There's more on this command if you run
```
man mount
```

---

