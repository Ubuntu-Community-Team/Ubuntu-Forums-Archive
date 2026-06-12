---
title: "Problem trying to upgrade Ubuntu"
date: 2005-10-14
forum: Desktop Environments
---

### Post by aleal on 2005-10-14
:???:  Hello. i've got a problem... When i execute the aplication to add or delete programs it says that i have a problem... 

W: No se puede leer la lista de paquetes fuente [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/mx.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No existe el fichero o el directorio)

 Please let me know how can i solve that problem.... THANKS

Aleal:???:

---

### Post by Ampersand on 2005-10-14
Hi
Try pressing 'Reload' in the top left-hand corner of the window. This will download the package lists again, and hopefully get rid of the error.

---

### Post by aleal on 2005-10-14
:???:  No, it doesn't fix the problem.. when i press RELOAD it starts to download all the stuff but [http://mx.archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz:](http://mx.archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz:) El subproceso gzip devolvió un código de error (1)

The error message  says that the repository is not available anymore....

 i think i have to set the correct repositories or something like that.. but i don't know how..  Any help would be appreciated

aleal ;)

---

### Post by Ampersand on 2005-10-14
Quite strange, since the link in the error message appears to work... It might work if you try again in a few minutes, some of the servers have been a bit slow after everyone started updating to Breezy.

Could you post the contents of your /etc/apt/sources.list just to make sure I'm not missing anything obvious?

---

