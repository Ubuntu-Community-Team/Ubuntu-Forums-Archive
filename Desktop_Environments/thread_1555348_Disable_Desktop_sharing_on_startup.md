---
title: "Disable Desktop sharing on startup"
date: 2010-08-17
forum: Desktop Environments
---

### Post by realmad on 2010-08-17
Hello,

I was experimenting with desktop sharing on my kubuntu and now the 2 windows opens after every login.How to disable it? 

Also whats with the keyring manager? can I configure so that it does not ask password every time I login? It feels like I have gone back a decade in desktop computing dealing with these nagging features.

Thanks in advance.

---

### Post by realmad on 2010-08-18
any one?

---

### Post by realmad on 2010-08-19
any one?

---

### Post by bergfly on 2010-08-19
I share your frustration here, and spent some time trying to work out the password thing. I would assume the reason it is coming up is due to the fact you are on secured wireless. If so what you need to do is create a new profile in Kwallet for local passwords. 

This thread explains it nicely

[http://ubuntuforums.org/showthread.php?t=1268434]("http://ubuntuforums.org/showthread.php?t=1268434")

As far as desktop sharing goes, you need to check a couple places. Firstly open **system settings** and then click on the **advanced tab**. Under there is **autostart**. Check if desktop sharing is included on autostart. 

If it is not there, you might be restoring a saved session at every startup that includes desktop sharing. Still in **system settings** ---> **advanced**, click on **session manager** and see what has been set up there. If in doubt, close down everything and save that session, then use that on next startup... Hope that makes sense, sorry it took so long to respond

---

### Post by bergfly on 2010-08-19
oops - forgot os subscribe to thread in case y0ou need further help.. anyone know how to do this after the fact?

---

