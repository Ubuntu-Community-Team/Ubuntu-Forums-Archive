---
title: "Confusing situation!! Any creative idea's?? Regarding directory accesed by 2 services"
date: 2009-03-24
forum: General Help
---

### Post by Deathray on 2009-03-24
I have a directory called /ftp/upload and /ftp/download
upload has 777 so any anonymous user can upload into this directory (but not delete or rename) and /ftp/download where people can nothing else than download the files in that folder. NOW, here comes the confusing part! I ALSO have torrentflux, and I wish it would place new files in /ftp/download but in the settings page of torrentflux it says:> 
Path
Define the PATH where the downloads will go
(make sure it ends with a / [slash]). It must be [SIZE="5"]chmod'd to 777[/SIZE]: 
I cant chmod it to 777 because then anonymous ftp users will be able to upload to that directory. What do I do !?!?

---

### Post by Deathray on 2009-03-24
Okay I think I have an idea, I do 755 on the download folder but do chown on the download folder to the user which torrentflux is running under. Is that possible, if so, how? What user does apache run under so I can test it out myself :) ?

---

### Post by Deathray on 2009-03-24
I'm impressed by myself hehe :D
All I did was change the upload directory back to 755 and then chown www-data download/
That enabled torrentflux to write to this directory but not FTP users! :D

---

