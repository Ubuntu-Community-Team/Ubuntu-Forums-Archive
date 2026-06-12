---
title: "adept /amarok /kopete problems"
date: 2006-05-09
forum: Desktop Environments
---

### Post by jude254 on 2006-05-09
I am using Kubuntu 5.10. I have problems with a few things...:-k 

1) Adept: I cannot find all the packages I want, eg firefox, amsn...apparently it seems I have to update my repositories. What I did was - 1)enable all repositories -2) sudo apt-get update
This is the result: I have all the repositories enabled, but there seem to be something wrong. Here is what I get in the dialog of manage repositories(all comments are in grey, while all the rest is in black ) :


list of repositories

deb    cdrom: [KUBUNTU 5.10 _BREEZY BADGER_ -Release 1386 20051012)]/                breezy             main restricted
(separator)
(separator)
comment             #Uncomment the following two lines to fetch updated software from the network
deb [http://it.archive.uubntu.com/ubuntu](http://it.archive.uubntu.com/ubuntu)                                                                  breezy updates     main restricted
deb-src        [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu)                                                                  breezy updates     main restricted
(separator)
comment    ##Uncomment the following two lines to add software from the universe repository
comment    ##NB software from this repository is entirely unsupported by the ubuntu team
comment    ## and may not be under a free license. Please satisfy yourself as your rights to use the software. Also please note the software in universe will not receive any review or updates from the Ubuntu security team
deb      [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu)                                                                          breezy                    universe multiverse
deb src  [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu)                                                                        breezy                     universe multiverse
(separator)
comment ## Uncomment the following two lines to add software from the backports repository
comment   ## NB software from this repository may not have been tested as extensively as that contained in the main release. Although it includes newer versions of some apps which may provide useful features. 
comment   ## also please note that software in backports will not receive any review or updates from the kubuntu security team
deb             [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu)                                                                 breezy backports       main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu)                                                                          breezy backports         main restricted universe multiverse
(separator)
deb      [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu)                                                                            breezy security                 main restricted
deb-src   [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu)                                                                         breezy security                  main restricted
(separator)
deb                [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu)                                                                  breezy security                 universe multiverse
DEB-SRC     [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu)                                                                   breezy security                universe multiverse
(separator)

Does it look normal? I dont know why I have all those comments. 
Also, by doing fetch updates, it all stays the same. If I do apt-get update it gives me this script:

Err [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy Release.gpg
  risoluzione di 'it.archive.ubuntu.com' temporaneamete fallita
Err [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy-updates Release.gpg
  risoluzione di 'it.archive.ubuntu.com' temporaneamete fallita
Err [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy-backports Release.gpg
  risoluzione di 'it.archive.ubuntu.com' temporaneamete fallita
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg
  risoluzione di 'security.ubuntu.com' temporaneamete fallita
Impossibile ottenere [http://it.archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg](http://it.archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg)  risoluzione di 'it.archive.ubuntu.com' temporaneamete fallita
Impossibile ottenere [http://it.archive.ubuntu.com/ubuntu/dists/breezy-updates/Release.gpg](http://it.archive.ubuntu.com/ubuntu/dists/breezy-updates/Release.gpg)  risoluzione di 'it.archive.ubuntu.com' temporaneamete fallita
Impossibile ottenere [http://it.archive.ubuntu.com/ubuntu/dists/breezy-backports/Release.gpg](http://it.archive.ubuntu.com/ubuntu/dists/breezy-backports/Release.gpg)  risoluzione di 'it.archive.ubuntu.com' temporaneamete fallita
Impossibile ottenere [http://security.ubuntu.com/ubuntu/dists/breezy-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/breezy-security/Release.gpg)  risoluzione di 'security.ubuntu.com' temporaneamete fallita
Lettura della lista dei pacchetti in corso... Fatto
W: Impossibile controllare la lista dei pacchetti sorgente [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/it.archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Impossibile controllare la lista dei pacchetti sorgente [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy/restricted Packages (/var/lib/apt/lists/it.archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Impossibile controllare la lista dei pacchetti sorgente [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/it.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Impossibile controllare la lista dei pacchetti sorgente [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy/multiverse Packages (/var/lib/apt/lists/it.archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Impossibile controllare la lista dei pacchetti sorgente [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy-updates/main Packages (/var/lib/apt/lists/it.archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Impossibile controllare la lista dei pacchetti sorgente [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy-updates/restricted Packages (/var/lib/apt/lists/it.archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Impossibile controllare la lista dei pacchetti sorgente [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy-backports/main Packages (/var/lib/apt/lists/it.archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Impossibile controllare la lista dei pacchetti sorgente [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy-backports/restricted Packages (/var/lib/apt/lists/it.archive.ubuntu.com_ubuntu_dists_breezy-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Impossibile controllare la lista dei pacchetti sorgente [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy-backports/universe Packages (/var/lib/apt/lists/it.archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Impossibile controllare la lista dei pacchetti sorgente [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy-backports/multiverse Packages (/var/lib/apt/lists/it.archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Impossibile controllare la lista dei pacchetti sorgente [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Impossibile controllare la lista dei pacchetti sorgente [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Impossibile controllare la lista dei pacchetti sorgente [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Impossibile controllare la lista dei pacchetti sorgente [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/multiverse Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: È consigliabile eseguire apt-get update per correggere questi problemi
E: Impossibile scaricare alcune file di indice, essi verranno ignorati, oppure si useranno quelli precedenti.

The lines in italian mean:
1) risoluzione fallita= failed resolution
2) impossibile ottenere= impossible to obtain
3)lettura della lista pacchetti in corso...fatto=reading the list of packages....done
4)W: impossible to control the list of packages (cource list)
5)E: impossible to downlaod any file of index (index file?), they will be ingored or previous packages will be used

Hope that makes sense.

2) Amarok: I cannot play mp3s with amarok. Ive seen that (k)ubuntu doesn't have mp3 support out of the box...but I have to install 'gstreamer0.8-mad' package. HOwever, I have checked adept and it says I have all the gstreamer0.8 installed...though I cannot find the -mad package, nor the akode-mpeg (see [https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)) I can only find the akode plugin which is already installed. Also i have tried to install the -mad package thru terminal by sudo apt-get install  gstreamer0.8-mad, and it gives me a similar script to the one I typed before.:confused: 

Kopete: I cannot connect Kopete, and I think this is due to the fact that Im behind a proxy. Is there a solution to that, or should I install a similar package? kopete doesnt have its own proxy setup though, so all my proxy congifuration is in network setting:

http: 192.168.1.2  port 6588
https: 192.168.1.2 port 6588
ftp: 192.168.1.2 port 21

I hope you can help me solve these issues with adept, if i solve that, then I solve most of my problems (except with amarok)

Thanks in advance for reading
Elisa

---

