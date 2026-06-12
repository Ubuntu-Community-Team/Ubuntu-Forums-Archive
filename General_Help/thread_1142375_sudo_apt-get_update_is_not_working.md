---
title: "sudo apt-get update is not working"
date: 2009-04-29
forum: General Help
---

### Post by ditlhakem on 2009-04-29
i am new to ubuntu. i wanted to update and also instal LAMP package my biggest problem is dat when i run ***sudo apt-get update*** gives the following proplem  "sniped of it"
[B][I]
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/i18n/Translation-en_BW.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/i18n/Translation-en_BW.bz2)  Unable to connect to archive.ubuntu.com http: [IP: 91.189.92.46 80]

[/I][/B]i have also done the following advice from a frind 

[LIST=1]
[*]open the terminal and issue the command ***sudo /etc/apt/sources.list***
[*]It opens a file in gedit (i.e. notepad) then look for URL's which start with bw. e.g.                                                  ***deb [http://bw.archive.ubuntu.com/ubuntu/](http://bw.archive.ubuntu.com/ubuntu/) hardy main restricted*** Simply remove the bw. so that it remains as ***deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main restricted*** for all of them.
[*]Save the file and issue the command ***sudo apt-get update*** form the terminal
[*]If it does the same thing, issue command on line 1 above and this time change all the URL's to have us. at the begining after every http:// e.g. ***deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted*** and try to issue the command ***sudo apt-get update*** again .
[/LIST]
but it still failed to connect

---

### Post by Bindsa on 2009-04-29
You sure that you are connected to the internet? Also check if your router configuration is OK, I myself found it useful to forward some ports to my computer.

---

### Post by ditlhakem on 2009-04-29
[SIZE=4]i am sure dat my internet is working cuz am using the same laptop to open some website without any problem. am not sure about "check if your router configuration is OK" maybe dats where i need help[/SIZE].

---

### Post by bumanie on 2009-04-29
Tut-tut. No need to be rude. Some people have more than one computer or post about an issue from a work computer - the above post is not a silly question to ask when such is taken into account. Try > sudo apt-get update && sudo apt-get upgrade

---

