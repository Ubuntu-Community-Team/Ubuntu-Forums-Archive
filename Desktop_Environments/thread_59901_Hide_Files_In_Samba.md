---
title: "Hide Files In Samba"
date: 2005-08-25
forum: Desktop Environments
---

### Post by SpiKeRs on 2005-08-25
I have a shared music folder on my winxp which i can access on linux with samba. However because its a win folder, it displays the album art and ini files etc which I dont want. I have had a look around and found that by putting: 

hide files = /*.jpg/*.ini/

in the smb.conf file it should stop them from appearing. However it doesnt appear to be working. Does anyone have any ideas why?

---

### Post by nad on 2005-08-25
Have you restarted samba?
 /etc/init.d/samba restart

---

### Post by SpiKeRs on 2005-08-26
yes :(

Is  there perhaps a particular place in the conf file that hide files should be placed? I am simply adding it to the bottom of the file, no other changes get made to it

---

### Post by slazh on 2005-08-26
Did you put the "hide files=.." part at the share part?

[data]
path = /home/samba/data
browseable = yes
guest ok = yes
writeable = yes
case sensitive = no
**hide files = /*.java/*README*/**

Something like that for example (source: [http://www.oreilly.com/catalog/samba/chapter/book/ch05_02.html](http://www.oreilly.com/catalog/samba/chapter/book/ch05_02.html))

---

### Post by SpiKeRs on 2005-08-27
This is quite likely not how its meant to be done but I wasnt sure what else to put:

```

[data]
path=192.168.0.1/Shared/Music
browseable = yes
guest ok = yes
writeable = yes
case sensitive = no
hide files = /*.jpg/*.ini/

```

Its still not working, any suggestions?

---

### Post by SpiKeRs on 2005-08-27
This is quite likely not how its meant to be done but I wasnt sure what else to put:

```

[data]
path=192.168.0.1/Shared/Music
browseable = yes
guest ok = yes
writeable = yes
case sensitive = no
hide files = /*.jpg/*.ini/

```

Its still not working, any suggestions?

---

### Post by SpiKeRs on 2005-08-28
This is quite likely not how its meant to be done but I wasnt sure what else to put:

```

[data]
path=192.168.0.1/Shared/Music
browseable = yes
guest ok = yes
writeable = yes
case sensitive = no
hide files = /*.jpg/*.ini/

```

Its still not working, any suggestions?

---

### Post by slazh on 2005-08-28
Are you editing the samba config file on the server, or on your own computer (client)?

As far as I know, you've got to edit the smb.conf file on the server (which runs samba). I'm just wondering, since you have the following entry:
**path=192.168.0.1/Shared/Music**

If your server (with samba) has the IP-adress 192.168.0.1 you should put the full path  to the /Shared/Music directory. For example:
**path=/home/Shared/Music** or where ever the directory Shared/Music is.

So on the server (computer with all the files you want to share) that runs samba, you'll have to enter something like this:

```

[data]
path=/home/Shared/Music
browseable = yes
guest ok = yes
writeable = yes
case sensitive = no
hide files = /*.jpg/*.ini/

```

---

### Post by SpiKeRs on 2005-08-28
the music folder is on my windows based desktop which i am accessing on my ubuntu laptop through a lan, i dunno if that makes any difference?

---

### Post by SpiKeRs on 2005-08-29
have also now tried path=//servername/shared/music but no success. However it must be right because I an access the folder using that path and it shows up in the shared folders program...

---

### Post by nad on 2005-08-29
I'm sorry about the advice in my post (#2), but, the samba configuration directive that you wish to implement will only work on a samba server.

Perhaps you may hide those file types in the MS directories to keep them from showing.

---

