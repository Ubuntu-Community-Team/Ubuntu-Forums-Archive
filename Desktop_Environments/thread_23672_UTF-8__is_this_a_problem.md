---
title: "UTF-8 : is this a problem ?"
date: 2005-04-03
forum: Desktop Environments
---

### Post by ploum on 2005-04-03
Hello,

I've installed Hoary from scratch two days ago and it's really great. But I have a lot of problem with UTF-8 :

- messages in the console are sometimes broken (éèà, etc..)
- Files names and MP3/OGG tags are broken (*)
- I don't know if documents I send to windows users are good or not.


For me, it's not really a problem since I'm a geek and, as a beta tester, used to broken things.

I was planning to install a fresh Hoary for my mother tomorrow (day of the release). She use a Debian Sarge, but lot of things are not fully functionnal due to successive upgrade.  A fresh install with only security update is a really good idea IMHO.

But she uses her computer professionnaly, and she has a lot of contact with windows users, sharing mails, txt, pdf and doc files.

She cannot have problems like me !  So, what is your opinion :

- keep the Debian, even if not fully functionnal
- install Hoary, problems can be easily solved
- install Hoary and just install the iso locales



(*) utf8migration tool doesn't work for me. It finds a lot of files to convert then crash with :
Traceback (most recent call last):
  File "/usr/bin/utf8migrationtool", line 91, in change_setup
    os.rename(oldfile, newfile)
OSError: [Errno 2] Aucun fichier ou répertoire de ce type

Also, it doesn't convert Ogg tags ;-)

---

### Post by ubuntu_demon on 2005-04-03
tomorrow is probably not the day of the release. Just wait untill hoary gets released and install hoary on your mothers pc. If there are problems search the forums first and then ask. With a bit of luck there won't be any major issues.

try this in order to fix your UTF8 locales:
sudo dpkg-reconfigure locales

---

### Post by ploum on 2005-04-03
[QUOTE=demon666_nl]tomorrow is probably not the day of the release. Just wait untill hoary gets released and install hoary on your mothers pc. If there are problems search the forums first and then ask. With a bit of luck there won't be any major issues.

try this in order to fix your UTF8 locales:
sudo dpkg-reconfigure locales[/QUOTE]
 thx for replying but :

1) none of my problems were related to dpkg-reconfigure locales. I fact I have only minor issues myself.

2) I can't afford that somes documents send by my mother will not be readable by people using windows. I can't take any risk at all.

---

### Post by ubuntu_demon on 2005-04-03
never upgrade if you can't take any risk at all

But I would upgrade to hoary when it is released (april 8 I believe)

---

### Post by rupert on 2005-04-04
I have this öäü problem as well,
many filenames are broken when i copy them to my harddisk.

files look like that than:
01 - Einst?rzende Neubauten - Was ist ist.mp3 (invalid encoding)


also textfiles get some strange letters where the üöä have been.

I run locales to chane everything to UTF-8.

Will this be fixed till hoary, its hard work to fix countless lines of code when i import my projects.
thx

---

### Post by ploum on 2005-04-04
```
#apt-get install evolution-webcal
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances... Fait
E: Impossible de trouver le paquet ev&#65533;lution-webcal
zsh: exit 100   apt-get install ev&#65533;lution-webcal

```

That's the kind of little problem I have in a terminal.

Could someone explain me why my well typed command is suddenly converted to iso ?
I really don't understand.

Restarting xterm and all is working again...

---

### Post by Slo Mo Snail on 2005-04-05
[QUOTE=ploum]Hello,

I've installed Hoary from scratch two days ago and it's really great. But I have a lot of problem with UTF-8 :

- messages in the console are sometimes broken (éèà, etc..)
- Files names and MP3/OGG tags are broken (*)
- I don't know if documents I send to windows users are good or not.


For me, it's not really a problem since I'm a geek and, as a beta tester, used to broken things.

I was planning to install a fresh Hoary for my mother tomorrow (day of the release). She use a Debian Sarge, but lot of things are not fully functionnal due to successive upgrade.  A fresh install with only security update is a really good idea IMHO.

But she uses her computer professionnaly, and she has a lot of contact with windows users, sharing mails, txt, pdf and doc files.

She cannot have problems like me !  So, what is your opinion :

- keep the Debian, even if not fully functionnal
- install Hoary, problems can be easily solved
- install Hoary and just install the iso locales



(*) utf8migration tool doesn't work for me. It finds a lot of files to convert then crash with :
Traceback (most recent call last):
  File "/usr/bin/utf8migrationtool", line 91, in change_setup
    os.rename(oldfile, newfile)
OSError: [Errno 2] Aucun fichier ou répertoire de ce type

Also, it doesn't convert Ogg tags ;-)[/QUOTE]
 Regarding the vorbis tags: they are defined to be UTF-8, for everything else something must have gone wrong while writing the tags

---

### Post by yanik on 2005-04-05
same here, sometimes they are replaced with ?, and sometimes with weird chains of characters.  It has nothing to do with the way tags are written, it happens on all type of file that have éàè.... in their names

It seems debian (testing) as better french support.  I didn't had those problems under testing.

---

### Post by condorloco on 2005-04-05
I have the problem with the broken id3 tags, too. Everything worked fin in warty and now Rhythmbox doesn't recognize any tags anymore. Files ere only listed under the filename, some are listed as 'invalid filename'.

---

