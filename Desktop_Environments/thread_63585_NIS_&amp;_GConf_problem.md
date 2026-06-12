---
title: "NIS &amp; GConf problem"
date: 2005-09-08
forum: Desktop Environments
---

### Post by remi.a on 2005-09-08
Hi there,

I have just installed the hoary on my pc, all work fine with local users, except that after having setup NIS, I am expecting problem just after the GDM login.

Just after the login, I can see the classical windows and all the icons indicating that some apps (nautilus for ex) are loading, and after some seconds, I have a two error windows showing praticaly the same long text (I do not have the gnome-panel appearing). This is the long text in the windows :

```
Erreur GConf : Aucune base de données disponible pour enregistrer votre configuration: Incapable de stocker une valeur à la clé 
« /apps/nautilus/preferences_version », car le serveur de configuration n'a pas de base de données accessible en écriture. 
Il existe plusieurs causes courantes à ce problème : 
1) Votre fichier de configuration de chemin /etc/gconf/2/path ne contient aucune base de données ou est introuvable. 
2) Quelqu'un a créé par erreur deux processus gconfd. 
3) Votre système d'exploitation est mal configuré et le verrouillage de fichier NFS ne fonctionne pas dans votre répertoire personnel. 
4) Votre machine cliente NFS s'est bloquée et n'a pas proprement indiquée au serveur au redémarrage de supprimer les verrous des fichiers. Si vous avez 2 processus gconfd (ou en aviez 2 au moment ou le second a été lancé), déconnectez vous, tuez toutes les copies de gconfd et reconnectez vous. 
Cela peut résoudre le problème. 
Si vous avez des verrous non valides, supprimez ~/.gconf*/*lock. Le problème provient peut-être du fait que vous essayez d'utiliser GConf depuis 2 machines à la fois et qu'ORBit a toujours sa configuration par défaut qui lui interdit les connexions distantes CORBA - mettez "ORBIIOPIPv4=1" dans /etc/orbitrc. 
Comme toujours, vérifiez le journal user.* pour les détails sur les problèmes que gconfd a rencontrés. 
Il ne peut y avoir qu'un gconfd par répertoire personnel, et il doit posséder un fichier de verrouillage dans ~/.gconfd ainsi que des fichiers de verrouillage dans les emplacements de stockage individuel tel que ~/.gconf
``` 

Yes this is in french... 

In two words this text say that GCONF cannot acces to is database. One of the probably reason (the number 3) is that the locketing system of NFS doesn't work in my personnal directory.

- Note that I doesn't have any problem with local users (the gnome-panel work, no errors messages etc..)
- Note that the NIS config has already worked in a previous install (Hubuntu warty) with the same NIS server config (I do not have acces to the NIS server).
- Note that I only want to use the NIS user "arquier", I dont have, for the moment, mounted any nfs file system. I will mount my nfs filesystem when this problem will be solved. For the moment the NIS user "arquier" use the local user dir : "/home/arquier"

The things I have done manualy to setup NIS after the first login with a local user :

1/ I have installed the nis package with synaptic
(and NIS seems to work fine, nisdomainname give me the right group name, and I view the list of other users when I press "~+tab")

2/ I have added this two lines to /etc/passwd
+arquier:::::/home/arquier:/bin/bash
+::::::

3/ I have added this line to /etc/group
+:::

/4 I have added in /etc/group the name "arquier" (this is my NIS login) to the groups adm, dialout, cdrom, floppy, audio, and dip.

/5 I have created the dir /home/arquier , and changed permissions to "arquier.umn" (my NIS user name).(my NIS group name)

/6 I have restarted my computer.


And that all. I have surrely forgetten to do something, but I do not see.


Thanks a lot for your help !

---

### Post by remi.a on 2005-09-09
Hi , it me again,


After having thoses problem I can start a terminal, and I can launch the gnome-panel.

When I start it, it gives me the message :

```
(gnome-panel:17784): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

(gnome-panel:17784): GLib-GObject-CRITICAL **: g_object_unref: assertion `object->ref_count > 0' failed

(nautilus:17815): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
```


Perhaps it helps to understand.

---

### Post by tchernobog on 2008-02-28
I'm having this problem in 2008... did you manage to solve it?

---

