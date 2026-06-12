---
title: "Error instaling w32codecs"
date: 2005-12-18
forum: General Help
---

### Post by filipenetto on 2005-12-18
Hi people. I'm having the this problem installing the 'w32codecs' package:

$ sudo apt-get install w32codecs

[COLOR="DimGray"]Getting: 1 [ftp://ftp.nerim.net](ftp://ftp.nerim.net) etch/main w32codecs 1:20050412-0.0 [13,2MB]
Downloaded 13,2MB in 5m29s (40,1kB/s)
Fail on download [ftp://ftp.nerim.net/debian-marillat/pool/main/w/w32codecs/w32codecs_20050412-0.0_i386.deb](ftp://ftp.nerim.net/debian-marillat/pool/main/w/w32codecs/w32codecs_20050412-0.0_i386.deb)  Incorrect size
E: Impossible to get some files, maybe run apt-get update or try with --fix-missing?[/COLOR]


So, when I use the 'update' command:

$ sudo apt-get update

[COLOR="DimGray"]W: GPG error: [ftp://ftp.nerim.net](ftp://ftp.nerim.net) etch Release: The folowing signatures cannot be verified because the public keys are not available: NO_PUBKEY 07DC563D1F41B907
W: You must run apt-get update to correct this fails files.
E: Some index files has failed on, they had been ignored or the older files was used in your place.[/COLOR]

Somebody know how to resolve this problem ?

---

### Post by Ranime on 2005-12-18
try this

---

### Post by filipenetto on 2005-12-18
This what ?

: )

---

### Post by schilcha on 2005-12-18
I guess, today is my vague-answer-day... anyways I'll try to help:

I once had similar problems, which I fixed with the following:
```

sudo mv /var/lib/apt/lists /var/lib/apt/backup.of.lists
sudo mkdir -p /var/lib/apt/lists/partial
sudo apt-get update

```

you can remove the backup-copy of lists-subdir if things improved. If this worsens everything, rename the backupdir back to lists and you should be at the same status as now.

Good Luck!

---

### Post by schilcha on 2005-12-18
Also: consider using an official ubuntu-mirror.

---

### Post by filipenetto on 2005-12-18
Hehehe .... I got it !

Not with this way, but, I do the folowing: I have changed my repositories on the 'sources.list', and its works !!

My 'sources.list' is like that:

[COLOR="DimGray"]deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
## deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
## deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

##########################################################
#### Repositorios oficiais do Ubuntu 5.10 - Breezy #######
##########################################################
## Softwares atualizados
deb [http://br.archive.ubuntu.com/ubuntu](http://br.archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://br.archive.ubuntu.com/ubuntu](http://br.archive.ubuntu.com/ubuntu) breezy main restricted
##
## Atualizacoes e correcoes de bugs
deb [http://br.archive.ubuntu.com/ubuntu](http://br.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://br.archive.ubuntu.com/ubuntu](http://br.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
##
## Repositorios Universe com diversos softwares adicionais. Aqui voce encontra pacotes
## totalmente suportados pelo Ubuntu Linux mas nao necessariamente distribuidos sob
## a licenca GPL. Aqui voce nao encontra atualizacoes de seguranca oficiais.
deb [http://br.archive.ubuntu.com/ubuntu](http://br.archive.ubuntu.com/ubuntu) breezy universe
deb-src [http://br.archive.ubuntu.com/ubuntu](http://br.archive.ubuntu.com/ubuntu) breezy universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
##
## Repositorios Multiverse
## Aqui voce encontra muitos programas para o Ubuntu incluindo alguns nao open source.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse
##
## Backports (BR) - Ultimos pacotes estaveis - Brasil
deb [http://br.archive.ubuntu.com/ubuntu](http://br.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
deb-src [http://br.archive.ubuntu.com/ubuntu](http://br.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
##
## Backports (PT) - Ultimos pacotes estaveis - Portugal
# deb [http://pt.archive.ubuntu.com/ubuntu](http://pt.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
# deb-src [http://pt.archive.ubuntu.com/ubuntu](http://pt.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
##########################################################
#### Fim dos repositorios oficiais do Ubuntu 5.10 ########
##########################################################

##########################################################
####################### ATENCAO ##########################
##########################################################
# Os repositorios abaixo nao sao oficiais do Ubuntu.     #
# Se quiser utiliza-los faca por sua propria conta e     #
# risco. Basta retirar o simbolo "#" no comeco da linha  #
# com o endereco do repositorio para ativa-lo. Salve o   #
# arquivo e feche-o. Em seguida execute o comando:       #
# sudo apt-get update                                    #
# Feito isso abra o gerenciador de pacotes e instale o   #
# programa desejado. Apos feito isto, edite novamente    #
# este arquivo e comente novamente a linha colocando o   #
# simbolo "#" no inicio da linha com o endereco          #
#                                                        #
# Utilizar repositorios do Debian pode incluir riscos    #
# Sempre que estiver com um repositorio nao-oficial      #
# ativado, NAO faca nenhuma das atualizacoes indicadas   #
# pelo ubuntu para nao misturar os pacotes debian/ubuntu.#
##########################################################

##########################################################
###### Repositorios NAO oficiais do Ubuntu 5.10  #########
##########################################################

################ Open Office 2.0 Final ###################
# deb [http://people.ubuntu.com/~doko/OOo2/](http://people.ubuntu.com/~doko/OOo2/) ./
##########################################################

################## Codecs Multimidia #####################
##### Atencao: descomente apenas para instalar codecs ####
######### multimidia e depois comente novamente ##########
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) etch main
##########################################################

######### Poucos pacotes, mas possui o Gaim-VV ###########
# deb [http://people.debian.org/~smimram/debian/](http://people.debian.org/~smimram/debian/) unstable main
##########################################################

############## Skype e outros programas ##################
## Descomente para instalar algum programa específico e comente novamente.
# deb [http://debian.neo.pl/wfmh/](http://debian.neo.pl/wfmh/) unstable main contrib non-free
##########################################################

############ Plugins para o Gift (Apollon) ###############
# deb [http://apt.cerkinfo.be/](http://apt.cerkinfo.be/) unstable main contrib non-free
# deb-src [http://apt.cerkinfo.be/](http://apt.cerkinfo.be/) unstable main contrib non-free
##########################################################

###### Aqui voce encontra o libdvdcss para tocar #########
##### DVDs e o VLC (Player de video super compativel) ####
#deb [http://download.videolan.org/pub/videolan/debian](http://download.videolan.org/pub/videolan/debian) sid main
#deb-src [http://download.videolan.org/pub/videolan/debian](http://download.videolan.org/pub/videolan/debian) sid main
########################################################## 
[/COLOR]
Thanks a lot !

---

### Post by Ranime on 2005-12-19
[QUOTE=filipenetto]This what ?

: )[/QUOTE]
My bad :)
I tried to insert a pdf file, I guess it failed :) seems it is to large. So I'll paste the content here:
```
HOWTO: Win32 Video Codecs 
This HOWTO is aimed at all the users of Ubuntu (both 32 and 64bit although wmv9 files don't 
work in Ubuntu 64bit) and it is useful because win32 codecs aren't available anymore in the 
repositories for legal reasons.

This guide is a revised version of a guide of mine specifically aimed at 64bit users. I decided to post 
this new one in order to avoid misunderstandings.

If you want to watch your movies (avi and wmv) or listen to your music files (wma) which require 
Win32 codecs this is what you need:

1)You have to OWN A LEGAL COPY of Windows, because these are proprietary codecs 
(somebody correct me if I'm wrong)

2)Install “xine*ui” and “totem*xine” in Synaptic or type in the command line: 
sudo apt*get install xine*ui ; totem*xine

3) Launch Xine (or Totem) and try to play a video (this will create a .config file)

4) Download the codecs from this website:
http://www.mplayerhq.hu/homepage/design7/dload.html
(just download the “essential codecs package”)
if the link above is temporarily down try this mirror:
http://www4.mplayerhq.hu/homepage/design7/dload.html

5) Open the command line(“Konsole” if you are using KDE, “Terminal” if you are using GNOME) 
and follow these steps: a) Get to the directory where you have downloaded the file (/home/alberto/downloads in my case)
cd /home/alberto/downloads
b) Create the directory in which you are going to put the codecs (/usr/lib/win32) 
sudo mkdir /usr/lib/win32
c) Now, assuming the file you downloaded is “essential*20050412.tar.bz2”:
tar *xjf essential*20050412.tar.bz2 (this will extract the file)
sudo mv essential*20050412/* /usr/lib/win32 (this command will move the files to the desired 
folder)
d) Now restart xine (if you were using it)

Congratulations, now you can open wma, wmv, and avi files by using Totem and Xine!

NOTE: It seems wmv9 don't work with my HOWTO if you use Ubuntu 64bit. 

Alberto
The best guides I've written:
HOWTO: Latest NVIDIA drivers
HOWTO: Kernel Compilation for Newbies
HOWTO: Double Clock Speed Problem
HOWTO: Win32 Video Codecs
HOWTO: Install KBFX 
Last edited by tseliot : 5 Days Ago at 12:14 PM. 

```

As you can see, this isn't mine, but I can't find the thread back... :rolleyes: 

Goodluck!

---

### Post by filipenetto on 2005-12-19
Ok, now appear, but, I already installed the application. 

Thank you for the help !

---

### Post by ronmarley1 on 2005-12-19
Hey Dude,
You may want to try automatix to get some of the must-have items for a new Ubuntu install.  See this link: [http://www.ubuntuforums.org/showthread.php?t=66563&highlight=automatix](http://www.ubuntuforums.org/showthread.php?t=66563&highlight=automatix)

---

### Post by filipenetto on 2005-12-22
Hi man, 

I have used the automatix, but it don't have some codecs of the 'w32codecs'. 

Tks !

---

