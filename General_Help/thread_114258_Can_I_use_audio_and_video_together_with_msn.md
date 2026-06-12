---
title: "Can I use audio and video together with msn?"
date: 2006-01-08
forum: General Help
---

### Post by lex on 2006-01-08
I tried amsn but it seems to be only video,(or do i need to do something to it?), and very slow and choppy. Do i need to set it up some how? Or is there another program that can do both at the same time?
Thanks
Lex

---

### Post by cb951303 on 2006-01-08
if you use kde kopete has both also gaim supports video/audio from version 2.0(which is still beta :D )

---

### Post by lex on 2006-01-08
[QUOTE=cb951303]if you use kde kopete has both also gaim supports video/audio from version 2.0(which is still beta :D )[/QUOTE]


Can I use kde with ubuntu? (Im very new.) I dont have to have kubuntu?
Thanks

---

### Post by Nikusan on 2006-01-08
Simply search for kopete using synaptic. There will be some dependencies, but it is all handled for you.

---

### Post by lex on 2006-01-08
[QUOTE=Nikusan]Simply search for kopete using synaptic. There will be some dependencies, but it is all handled for you.[/QUOTE]


ok, ill do that.
thanks

---

### Post by lex on 2006-01-08
in installed kopete. I cant see how do use web cam. I tried to do this in terminal "apt-get -f install kopete". I got this message, "[COLOR="Magenta"]lex@ubuntu:~$ apt-get -f install kopete
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory"[/COLOR].
Any ideas?

---

### Post by nerval on 2006-01-08
"sudo apt-get install kopete"

then it asks your password; then u write it; so you have the permission :)

---

### Post by Nikusan on 2006-01-08
try
```

sudo apt-get install kopete

```
when prompted for a password enter your user password. Also, make sure any apt front-ends are closed before you do this (eg Synaptic, Update manger).

---

### Post by lex on 2006-01-08
[QUOTE=Nikusan]try
```

sudo apt-get install kopete

```
when prompted for a password enter your user password. Also, make sure any apt front-ends are closed before you do this (eg Synaptic, Update manger).[/QUOTE]


Sorry I didn't make my self very clear. I installed kopete though Synaptic, then I tried "apt-get -f install kopete", which i read somewhere else thinking that it would do something so i could use my web cam because i read this in another post "[COLOR="Magenta"]Kopete doesnt accept webcam support by default install: 

Code:

apt-get -f install kopete

is there a easy way to make it ?[/COLOR]"
obviously  i was mistaken.
So how do i activate web cam abilities?
Thanks

---

### Post by lex on 2006-01-08
I need to get version 2 beta, to be able to use web cam correct. I think the version i got through synaptic is 0.10.4, when i look at help about kopete.
So how do i get version 2 beta? I tried System - Tools - Update Manager. But there was nothing in there.
Thanks
Lex

---

### Post by cb951303 on 2006-01-11
[QUOTE=lex]I need to get version 2 beta, to be able to use web cam correct. I think the version i got through synaptic is 0.10.4, when i look at help about kopete.
So how do i get version 2 beta? I tried System - Tools - Update Manager. But there was nothing in there.
Thanks
Lex[/QUOTE]
LEx I think you better wait 1 or 2 week for the gaim 2.0 , it's simply better then kopete ;)

---

### Post by az on 2006-01-11
[QUOTE=cb951303]LEx I think you better wait 1 or 2 week for the gaim 2.0 , it's simply better then kopete ;)[/QUOTE]


Er, the Gaim FAq says that webcam support is not here yet:
"Will you support features such as voice chat, internet phones, or video chat? 
Merging the gaim-vv code will take time, and we are not sure when it will be ready. Even then, there will remain work to be done before voice chat, video sharing, or internet phones will work on all protocols. "

Are you saying that gaim2 beta1 does vieo and voice chat?

As for Kopete, has anyone installed the version that has webcam support, and where do you get it for ubuntu?

The backported version desctiption ways nothing about webcams:
[http://packages.ubuntu.com/breezy/kde/kopete](http://packages.ubuntu.com/breezy/kde/kopete)

---

### Post by cb951303 on 2006-01-13
[QUOTE=azz]Er, the Gaim FAq says that webcam support is not here yet:
"Will you support features such as voice chat, internet phones, or video chat? 
Merging the gaim-vv code will take time, and we are not sure when it will be ready. Even then, there will remain work to be done before voice chat, video sharing, or internet phones will work on all protocols. "

Are you saying that gaim2 beta1 does vieo and voice chat?

As for Kopete, has anyone installed the version that has webcam support, and where do you get it for ubuntu?

The backported version desctiption ways nothing about webcams:
[http://packages.ubuntu.com/breezy/kde/kopete](http://packages.ubuntu.com/breezy/kde/kopete)[/QUOTE]
yes if you look at changelog tou will see that gaim-vv is merged into gaim with version 2.0. As I said, wait for the 2.0 release. Gaim's developpers has much more experience then kopete's :)

---

### Post by Neo Ex on 2006-01-13
I don't know if Kopete webcam support is good, but Kopete 0.11 has webcam support.
Add the KDE 3.5 Kubuntu repositories to get it: [http://kubuntu.org/announcements/kde-35.php](http://kubuntu.org/announcements/kde-35.php)

---

### Post by Jingo on 2006-01-13
I have installed gaim2 beta. Found in another thread.

Which protocols should support webcam? How do I enable it?

It seems it was compiled with "./configure --enable-vv" !

---

### Post by chele on 2006-01-14
[quote=azz]As for Kopete, has anyone installed the version that has webcam support, and where do you get it for ubuntu?[/quote] #kubuntu 3.5 backports
deb [http://kubuntu.org/packages/kde35]("http://kubuntu.org/packages/kde35") breezy main

---

