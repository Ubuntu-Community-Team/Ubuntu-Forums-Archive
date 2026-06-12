---
title: "Configuring Samba"
date: 2006-06-04
forum: Desktop Environments
---

### Post by Lomz on 2006-06-04
Good afternoon

I try to get SAMBA to share the folders I like it to share, the way i want it to do it.
I want some folders to be shared to everyone, but other folders to be shared with password and username.
I am a real noob at this.

I have made a link to my smb.conf file [Here]("http://www.vindstille.net/smb.conf.txt") so that you can read all of it.
But i have qouted the things I believe is essential:
> security = user
guest account = nobody
invalid users = root
The folders to be shared:
> 
Public:
[MP3 del2]
path = /home/lomz/dokumenter/My Music
available = yes
browseable = yes
public = yes
writable = no

[MP3]
path = /home/lomz/mp3
available = yes
browseable = yes
public = yes
writable = no

[Download]
path = /home/lomz/dokumenter/Download
comment = Downloadmappen
available = yes
browseable = yes
public = yes
writable = yes

Restricted:
[Bilder]
path = /home/lomz/dokumenter/Bilder
comment = Bildesamlingen
available = yes
browseable = yes
public = yes
writable = no

[Kreativt]
path = /home/lomz/dokumenter/Kreativt
comment = Kreative arbeider som blant annet WEBS
available = yes
browseable = yes
public = yes
writable = yes

What do I do wrong?
What should i do to make this work the way it to.
I have  made 2 users for Samba.
Nobody (guestaccount) and Lomz (mainaccount)

---

