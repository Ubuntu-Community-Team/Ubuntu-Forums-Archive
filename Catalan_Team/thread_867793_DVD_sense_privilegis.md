---
title: "DVD sense privilegis"
date: 2008-07-23
forum: Catalan Team
---

### Post by slink on 2008-07-23
Hola

després d'actualitzar a Hardy em vaig trobar que no podia veure un DVD que sí podía amb Feisty. 

Primer de tot vaig anar al guia ubuntu i vaig seguir les instruccions per (re)instal.lar els codecs i el suport DVD. ( [http://ubuntuguide.org/wiki/Ubuntu:Hardy#How_to_install_multimedia_support_on_Hardy_Heron](http://ubuntuguide.org/wiki/Ubuntu:Hardy#How_to_install_multimedia_support_on_Hardy_Heron) ) seguía igual

llavors vaig veure que el meu usuari no pot accedir a la carpeta VIDEO_TS (?) així que només entrant com a root puc accedir al DVD





```
slink@ubuntu:/media/MYDVD12$ ls -a -l
total 10
2 drwxrwxrwx 4 slink  136 2005-04-13 11:26 ./
4 drwxr-xr-x 6 root 4096 2008-07-22 15:48 ../
2 drwxrwxrwx 2 slink   40 2005-04-13 11:26 AUDIO_TS/
2 dr--r--r-- 2 slink  768 2005-04-13 11:43 VIDEO_TS/
```
aquí m'extranya que la carpeta AUDIO_TS tingui drets d'escriptura... és un DVD!


```
slink@ubuntu:/media/MYDVD12$ cd VIDEO_TS/
bash: cd: VIDEO_TS/: Permission denied
```


```
slink@ubuntu:/media/MYDVD12$ sudo cd VIDEO_TS/
[sudo] password for slink:
sudo: cd: command not found
```
aquí em va extranyar que bash no pogués executar la comand cd



així que vaig fer
```
slink@ubuntu:/media/MYDVD12$ sudo -s -H


root@ubuntu:/media/MYDVD12# cd VIDEO_TS/


root@ubuntu:/media/MYDVD12/VIDEO_TS# ls -al
total 4378898
dr--r--r-- 2 slink 4294967295        768 2005-04-13 11:43 .
drwxrwxrwx 4 slink 4294967295        136 2005-04-13 11:26 ..
-r--r--r-- 1 slink 4294967295      12288 2005-04-13 11:43 VIDEO_TS.BUP
-r--r--r-- 1 slink 4294967295      12288 2005-04-13 11:43 VIDEO_TS.IFO
-r--r--r-- 1 slink 4294967295    2254848 2005-04-13 11:26 VIDEO_TS.VOB
-r--r--r-- 1 slink 4294967295      83968 2005-04-13 11:43 VTS_01_0.BUP
-r--r--r-- 1 slink 4294967295      83968 2005-04-13 11:43 VTS_01_0.IFO
-r--r--r-- 1 slink 4294967295  280569856 2005-04-13 11:27 VTS_01_0.VOB
-r--r--r-- 1 slink 4294967295 1073739776 2005-04-13 11:44 VTS_01_1.VOB
-r--r--r-- 1 slink 4294967295 1073739776 2005-04-13 11:44 VTS_01_2.VOB
-r--r--r-- 1 slink 4294967295 1073739776 2005-04-13 11:44 VTS_01_3.VOB
-r--r--r-- 1 slink 4294967295  962013184 2005-04-13 11:43 VTS_01_4.VOB
-r--r--r-- 1 slink 4294967295      18432 2005-04-13 11:43 VTS_02_0.BUP
-r--r--r-- 1 slink 4294967295      18432 2005-04-13 11:43 VTS_02_0.IFO
-r--r--r-- 1 slink 4294967295      38912 2005-04-13 11:43 VTS_02_0.VOB
-r--r--r-- 1 slink 4294967295   17661952 2005-04-13 11:43 VTS_02_1.VOB


root@ubuntu:/media/MYDVD12/VIDEO_TS# nautilus .
Initializing nautilus-share extension
seahorse nautilus module initialized

** (nautilus:14902): WARNING **: Unable to add monitor: L'operació no està implementada

** (totem:14983): WARNING **: Failed to create dbus proxy for org.gnome.SettingsDaemon: Could not get owner of name 'org.gnome.SettingsDaemon': no such name
gnome-video-thumbnailer couldn't process file: 'file:///media/MYDVD12/VIDEO_TS/VTS_01_3.VOB'
Reason: Took too much time to process.
seahorse nautilus module shutdown
```
amb sudo -s -H sí que vaig poder accedir al directori VIDEO_TS, tot i que els permisos de lectura són per a tothom, no?
fent nautilus. vaig accedir al directori i "veure" el contingut del DVD.

en resum: només hi puc accedir sent root. aixó, evidentment, no és normal.

qué creieu que he de fer?

---

