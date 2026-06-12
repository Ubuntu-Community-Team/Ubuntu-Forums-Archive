---
title: "network servers dissapear"
date: 2006-01-17
forum: Desktop Environments
---

### Post by Herios on 2006-01-17
just installed ubuntu, network servors show sometimes not there others.
even during the same session.?

any help/advice much appreciated

thanx

---

### Post by Koybe on 2006-01-17
I think you'll need to give more information. What can we answer to this? What are you using? What are you trying to do?

---

### Post by Herios on 2006-01-17
figured but wasn't sure what info to give.

i have samba-common package only. right now just trying to grab files off windows computer on my network. have been succesful but somtimes the servers don't show up , sometimes they do.

don't know much about how the network was setup though, the file share i can access comes of what looks like a server icon but not sure why it doesn,t come up in the windows network.

new to ubuntu if ya havn't guessed, sorry if i should have posted in the newbie section

---

### Post by Koybe on 2006-01-17
No problem. I can't really tell you as I'm not using the network browser. But you can open any nautilus window, hit CTRL+L (Menu Go to ->> and i don't know as i don't have it in english right now). Then you can acces your windows share by using smb://server/share or simply smb://server which will show you all the shares.

You can also install the smbclient package, it will provide you with some usefull command in case of... ;)

---

### Post by prammy on 2006-01-17
Make sure winbind is running.
```

sudo apt-get install winbind
/etc/init.d/winbind start
```

---

### Post by Herios on 2006-01-17
thanks about the info about smb://  will be useful. i think i will eventually install smb package.:) 

on the other note, in synaptic it says windbind is for nt servers. i'm pretty sure i'm dealing with xp. don't have it installed but not sure if it will help.

i can see the other computers again and now there coming up on there own and in the windows network icon. its like there playing a shell game with me. maybe i shouldn't use nautilis file manager for this but would be nice:confused:

---

### Post by Herios on 2006-01-17
can't believe it took me 44 minutes to respond. getting late over here.

gotta go

all the input is muchly appreciated, be back tomorow.

---

### Post by Koybe on 2006-01-17
No, you do not need winbind for sharing files. Just go on with these informations then ask for more specific questions if you have some.

You can also found some information on the [wiki](https://wiki.ubuntu.com/SettingUpSamba).

---

