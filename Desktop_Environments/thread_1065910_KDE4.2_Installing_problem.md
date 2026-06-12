---
title: "KDE4.2 Installing problem"
date: 2009-02-10
forum: Desktop Environments
---

### Post by Ladgalen on 2009-02-10
Hello all !

I am a french users, thus excuse me for my english. 

I follow this link in order to install KDE 4.2

[http://www.kubuntu.org/news/kde-4.2](http://www.kubuntu.org/news/kde-4.2)

After adding the line in my source.list, I add a key with the command on the website :

```

[vallverd@Kargols ~]> gpg --keyserver keyserver.ubuntu.com --recv-keys 493B3065 && gpg --export -a 493B3065 | sudo apt-key add -
gpg: requête de la clé 493B3065 du serveur hkp keyserver.ubuntu.com
gpg: clé 493B3065: « Launchpad PPA for Kubuntu Most Experimental Packages » n'a pas changé
gpg: Quantité totale traitée: 1
gpg:              inchangée: 1
OK
[vallverd@Kargols ~]>

```

But, after that it says that it cannot do the authentification :

```

[vallverd@Kargols ~]> sudo apt-get update
....
Réception de : 6 http://archive.ubuntu.com intrepid-updates/main Packages [296kB]                  
Réception de : 7 http://archive.ubuntu.com intrepid-updates/restricted Packages [6843B]            
Réception de : 8 http://archive.ubuntu.com intrepid-updates/universe Packages [61,0kB]             
Réception de : 9 http://archive.ubuntu.com intrepid-updates/multiverse Packages [5200B]            
421ko réceptionnés en 9s (46,1ko/s)                                                                
Lecture des listes de paquets... Fait
W: GPG error: http://ppa.launchpad.net intrepid Release: Les signatures suivantes n'ont pas pu être vérifiées car la clé publique n'est pas disponible : NO_PUBKEY 60D11217247D1CFF
W: Vous pouvez lancer « apt-get update » pour corriger ces problèmes.
[vallverd@Kargols ~]>

```

Can you help me to install KDE4.2 ?

I was initially under gnome desktop and I install kubuntu-desktop in order to get KDE, thus I installes KDE4.1 first. One people said me to install KDE4.2 because I get a problems with my screen. Actually, I have a laptop (Dell Latitude 620) and I conect it with a normal screen. But under KDE, and only KDE (neither gnome  neither windows), sometimes, said every 10 s, the screen becomes dark and come back to its normal states ? Its a little bit stressing !

Does my install problem come from the fact I already have installed KDE 4.1 ? and Do you have any idea on the origin of my problem ?

Thanks a lot

---

