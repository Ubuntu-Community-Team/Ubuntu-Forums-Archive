---
title: "change default programs"
date: 2009-02-21
forum: General Help
---

### Post by theRightNee on 2009-02-21
hey all,

i cannot seem to get firefox to detect Deluge as my default for .torrent files, and it is kind of a bother having to download all the torrent files to my desktop and then open it from thunar...so how do i set it so that firefox will open it with deluge by default...also, i couldn't find the launcher file for deluge to link to when firefox gives me the option to choose a program

much thanks in advance

---

### Post by adult swim on 2009-02-21
in the firefox menu bar click on 
edit>preferences
click on the applications tab and look for 'bittorrent seed file' 
click on the options box and select 'use other' 
then browse to /usr/bin/deluge and select it

---

### Post by theRightNee on 2009-02-21
thank you so much! all i needed was the directory of the launcher file!

edit:
ok..so i guess it was only a temporary fix, problem now is that under applications there is no line for a bittorent seed file..

---

### Post by Incense on 2009-02-21
I'm not 100% on how to solve your problem, but I just thought you may like to know about the fantastic whereis command to show you were your program binaries are hiding. Just open up your terminal and type

```
where is program-name
```

IE

```
whereis firefox
firefox: /usr/bin/firefox /usr/lib/firefox /usr/share/firefox

```

That may help you in the future. I use transmission for my BT needs. Good luck.

---

