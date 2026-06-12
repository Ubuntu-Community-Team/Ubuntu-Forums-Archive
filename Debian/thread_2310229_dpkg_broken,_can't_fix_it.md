---
title: "dpkg broken, can't fix it"
date: 2016-01-17
forum: Debian
---

### Post by Toms_Simes on 2016-01-17
Hey, not on Ubuntu but on Debian (using ubuntu forums since they are the best and ubuntu uses the same package manager anyways ) and whenever i try any dpkg command ( wheater to install or update or dpkg-reconfigure ) I get this error:

root@chronos2:/var/lib/dpkg# sudo apt-get update
Ign [http://ftp.rnl.tecnico.ulisboa.pt](http://ftp.rnl.tecnico.ulisboa.pt) jessie InRelease
Hit [http://ftp.rnl.tecnico.ulisboa.pt](http://ftp.rnl.tecnico.ulisboa.pt) jessie-updates InRelease
Obter:1 [http://security.debian.org](http://security.debian.org) jessie/updates InRelease [63,1 kB]
Hit [http://ftp.rnl.tecnico.ulisboa.pt](http://ftp.rnl.tecnico.ulisboa.pt) jessie Release.gpg                                  
Hit [http://ftp.rnl.tecnico.ulisboa.pt](http://ftp.rnl.tecnico.ulisboa.pt) jessie Release                                      
Hit [http://ftp.rnl.tecnico.ulisboa.pt](http://ftp.rnl.tecnico.ulisboa.pt) jessie-updates/main Sources                   
Obter:2 [http://security.debian.org](http://security.debian.org) jessie/updates/main Sources [108 kB]             
Obter:3 [http://ftp.rnl.tecnico.ulisboa.pt](http://ftp.rnl.tecnico.ulisboa.pt) jessie-updates/main i386 Packages/DiffIndex [367 B]
Hit [http://ftp.rnl.tecnico.ulisboa.pt](http://ftp.rnl.tecnico.ulisboa.pt) jessie-updates/main Translation-en
Hit [http://ftp.rnl.tecnico.ulisboa.pt](http://ftp.rnl.tecnico.ulisboa.pt) jessie/main Sources
Obter:4 [http://security.debian.org](http://security.debian.org) jessie/updates/main i386 Packages [192 kB]                     
Hit [http://ftp.rnl.tecnico.ulisboa.pt](http://ftp.rnl.tecnico.ulisboa.pt) jessie/main i386 Packages                                        
Obter:5 [http://security.debian.org](http://security.debian.org) jessie/updates/main Translation-en [103 kB]                         
Hit [http://ftp.rnl.tecnico.ulisboa.pt](http://ftp.rnl.tecnico.ulisboa.pt) jessie/main Translation-pt                                             
Hit [http://ftp.rnl.tecnico.ulisboa.pt](http://ftp.rnl.tecnico.ulisboa.pt) jessie/main Translation-pt_BR                                            
Hit [http://ftp.rnl.tecnico.ulisboa.pt](http://ftp.rnl.tecnico.ulisboa.pt) jessie/main Translation-en                                               
Obtidos 466 kB em 15s (29,2 kB/s)                                                                                                                                                            
A ler as listas de pacotes... Erro !
E: Erro de leitura - read (5: Erro de entrada/saída)
E: As listas de pacotes ou o ficheiro de status não pôde ser analisado ou aberto.

(Output is in portuguese, tried to change lang to english to make you guys's life easier but dpkg-reconfigure aint workin' )

I replaced /var/lib/dpkg/status with /var/lib/dpkg/status-old did nothing

I know there are 2 posts related to this but I cant solve it anyways

I cant reinstall, I need it fixed in this instalation, this is a server..

Thanks

---

### Post by howefield on 2016-01-17
Thread moved to the "*Debian*" forum.

---

### Post by XBNCPRk on 2016-01-17
First, Welcome to the forums! 

Because this is an international forum used by people in every time zone, english is the common language used for posts, and it may take more than two hours for help. 

That said, you said youve tried replacing status with status-old without any success... have you tried using any of the compressed, older versions from /var/backups/dpkg.status.*?

---

### Post by Toms_Simes on 2016-01-17
Hey! thanks its just that i need to fix this quickly and its beyound my level of expertise :p; Can you help me do what you suggested?

---

### Post by matt_symes on 2016-01-17
Hi

This is the error.

```

read the package lists ... Error!
Read error - read (5: Input / output error)
The package lists or status file could not be parsed or opened.
```

Let's try this first. 

Please post the output of this command.

```
file  /var/lib/dpkg/status
```

Then let's clean out the old package list files.

```
sudo rm -fr /var/lib/apt/lists/*
```

Then please post the output of the command below so we can see if anything is left

```
ls -l /var/lib/apt/lists/
```

After that, try updating the package list again.

```
sudo apt-get update
```

Kind regards

---

### Post by Toms_Simes on 2016-01-17
Ok so I did "file /var/lib/dpkg/status" I got : /var/lib/dpkg/status: UTF-8 Unicode text, with very long lines
Then I did rm -fr /var/lib/apt/lists/*, It was sucessfull

Then I did ls -l /var/lib/apt/lists , i got: total 0

Then I did apt-get update... Its Fixed! Thanks a lot! :D

Can you try to explain me what was the problem in the first place? ( The more you know/learn )

---

### Post by matt_symes on 2016-01-17
Hi

> **Toms_Simes said:**
> Then I did apt-get update... Its Fixed! Thanks a lot! :D

Can you try to explain me what was the problem in the first place? ( The more you know/learn )

One of your package list files could not be opened or read for some reason. 

These list files are stored in a cache (/var/lib/apt/lists/) so we deleted those cached files and then regenerated the cached files using *apt-get update*.

Sometimes this will fix it, other times there are other fixes that are needed.

You may want to run an fsck on your drive at some point, just to ensure there's not a deeper file system problem.

Anyway, I'm glad this fixed your problem.

Please mark this thread as SOLVED using the thread tools under post #1. It will help others looking for a solution to a similar problem and is an easy way you can help the community :)

Kind regards

---

### Post by Toms_Simes on 2016-01-18
Still not solved actually :p Now I cant install software because i've got a ton of broken dependencies, so I did apt-get install -f and apt-get upgrade -f... Didnt work because at the very end it checks the lang and I have some problem with dpkg-reconfigure and my lang..

This is the output of apt-get install -f (not the full output just the error part):
É necessário obter 0 B/419 MB de arquivos.
Após esta operação, serão utilizados 965 MB adicionais de espaço em disco.
Deseja continuar? [S/n] s 
A ler os changelogs... Feito
A extrair templates a partir dos pacotes: 100%
A pré-configurar os pacotes...
 dict-common::dc_set: Warning: dictionaries-common/default-wordlist is already set to
      [portugues europeu (European Portuguese)].
      Not setting to [american (American English)]
dpkg: erro: a interpretar o ficheiro '/var/lib/dpkg/status' perto da linha 19372 pacote 'coinor-libclp1':
 EOF durante o valor do campo `Description' (falta newline final)
E: Sub-process /usr/bin/dpkg returned an error code (2)
root@chronos2:~# 
 
Its in portuguese btw

---

### Post by matt_symes on 2016-01-18
Hi

This is the error.

```
dpkg: error: to interpret the file "/var/lib/dpkg/status' near the line 19372 package 'coinor-libcap1':
EOF for the value of the 'Description' field (lack newline end)
E: Sub-process / usr / bin / dpkg returned an error code (2)
```

Can we take a look around line 19372 ? Please post the output of the command below.

```
sed '19362,19382!d' /var/lib/dpkg/status
```

Kind regards

---

### Post by Toms_Simes on 2016-01-19
root@chronos2:~# sed '19362,19382!d' /var/lib/dpkg/status
Maintainer: Debian Science Team <debian-science-maintainers@lists.alioth.debian.org>
Architecture: i386
Source: clp
Version: 1.15.10-1
Depends: coinor-libcoinutils3, coinor-libosi1, libbz2-1.0, libc6 (>= 2.4), libgcc1 (>= 1:4.1.1), libstdc++6 (>= 4.4.0), zlib1g (>= 1:1.1.4)
Description: Coin-or linear programming solver (shared libraries)
 Clp (Coin-or linear programming) is an open-source linear programming solver
 written in C++. It is primarily meant to be used as a callable library, but a
 basic, stand-alone executable version is also available. It is designed to
 find solutions of constrained linear mathematical optimization problems.
 .
 This package contains theroot@chronos2:~# 

That was the output

---

### Post by Toms_Simes on 2016-01-20
Up up up

---

### Post by Toms_Simes on 2016-01-21
been waiting for some time now :( i need this fixed, i need to install software in my server

---

### Post by mc4man on 2016-01-21
That last line is supposed to say - 
```
This package contains the clp executable.
```

or maybe 
```
This package contains the clp executable
```

or maybe
```
This package contains the clp executable
.
```

(not sure about the period in a status file, in the orig debian control file the 1st. example is what's there.

---

