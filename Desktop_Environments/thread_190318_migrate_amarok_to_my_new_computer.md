---
title: "migrate amarok to my new computer"
date: 2006-06-06
forum: Desktop Environments
---

### Post by ThirdWorld on 2006-06-06
Hi, I have Daper drake installed in my old PC. Im going to buy an AMD 64 x2 laptop and im going to do a clean install of Ubuntu (no windows :D  ). I know that i can transfer my evolution settings, contacts and stored email just by copy the .evolution folder to my new home folder. My question is, how can i transfer my playlist and amarok settings to my new system? I expend hours writing tags and organizing my entire collection. 

By the way my .mp3 collection is stored locally in my home folder in one place.

Thanks.

---

### Post by xaverx on 2006-06-06
copy folder .kde/share/apps/amarok and file .kde/share/config/amarok

i recomended rather than amarok very fast alternative [Listen]("http://listengnome.free.fr/")

Ubuntu 6.04 Dapper repository
deb [http://theli.free.fr/packages/dapper/](http://theli.free.fr/packages/dapper/) ./

sudo apt-get update
sudo apt-get install listen

[IMG]http://listengnome.free.fr/img/screenshot/accueil.png[/IMG]

---

### Post by jacksaff on 2006-06-06
Copy all your music files and playlists accross and let amarok re-populate your collection. The tags get saved with the actual music file so you won't lose them. What I can't find out how to do though is to copy data such as playcount and rating. I found the file containing this data but Amarok treats the music as new files and doesn't associate the info with them.

---

### Post by bluenova on 2006-06-06
[QUOTE=jacksaff]Copy all your music files and playlists accross and let amarok re-populate your collection. The tags get saved with the actual music file so you won't lose them. What I can't find out how to do though is to copy data such as playcount and rating. I found the file containing this data but Amarok treats the music as new files and doesn't associate the info with them.[/QUOTE]
That's strange, if everything is in the same place it should be fine. I've just done a clean install, (by backing up my home folder including hidden directories) and my whole desktop was as it was before, and amarok still had all it's data.

---

