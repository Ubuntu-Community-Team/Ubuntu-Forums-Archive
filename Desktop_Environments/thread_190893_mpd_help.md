---
title: "mpd help"
date: 2006-06-06
forum: Desktop Environments
---

### Post by nikodell on 2006-06-06
is there a special trick needed to get mpd working? I am stumped.

---

### Post by eeclark on 2006-06-06
run mpd in your sessions at startup
then use a client like gmpc

---

### Post by nikodell on 2006-06-06
gmpc mpc ampache all work as far as adding to playlist volume deleate playlist what i am getting is 

error
mp3 does not appear to be a mp3 bit stream.

mp3s worked with mpd befor switching from suse to ubuntu

not sure if i am missing some dep or what

---

### Post by nikodell on 2006-06-07
[QUOTE=nikodell]gmpc mpc ampache all work as far as adding to playlist volume deleate playlist what i am getting is 

error
mp3 does not appear to be a mp3 bit stream.

mp3s worked with mpd befor switching from suse to ubuntu

not sure if i am missing some dep or what[/QUOTE]


Ok now i found that I get the erroe only when mpd is started with the init script if i kill and restart as root it is fine. but that sucks for my music server. Also anyone know how to get my sound up in init 3 without gdm or kdm up and running?

---

### Post by mcduck on 2006-06-07
[QUOTE=eeclark]run mpd in your sessions at startup
then use a client like gmpc[/QUOTE]
I think it's actually better to let it run MPD as system service, so it works even if you don't log in to gnome..

Anyway, here's my favourite howto for MPD: [http://www.ubuntuforums.org/showthread.php?t=31763&highlight=mpd+howto]("http://www.ubuntuforums.org/showthread.php?t=31763&highlight=mpd+howto")

---

