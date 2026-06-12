---
title: "Need a good IM client for an internet cafe"
date: 2008-12-21
forum: General Help
---

### Post by fallingleaf on 2008-12-21
I run an internet cafe with some older machines running Windows XP.  I'm hoping I can speed things up a bit (and save myself virus headaches) by converting to (X)Ubuntu.  I've run Ubuntu exclusively on my own machine since 6.06.  My problem is that all the IM clients I see use a method where you have to create an account and then login.  This contrasts to most Windows clients which just open to a window asking for username and password.  Does anyone know a good app that works with all the popular messenging services and uses that kind of UI.  Or is there some configuration option or plugin I'm missing in Pidgin, etc.?

---

### Post by cb951303 on 2008-12-21
> **fallingleaf said:**
> I run an internet cafe with some older machines running Windows XP.  I'm hoping I can speed things up a bit (and save myself virus headaches) by converting to (X)Ubuntu.  I've run Ubuntu exclusively on my own machine since 6.06.  My problem is that all the IM clients I see use a method where you have to create an account and then login.  This contrasts to most Windows clients which just open to a window asking for username and password.  Does anyone know a good app that works with all the popular messenging services and uses that kind of UI.  Or is there some configuration option or plugin I'm missing in Pidgin, etc.?

there is emesene which exactly as you want but its only for msn.

---

### Post by 2hot6ft2 on 2008-12-21
maybe kopete

---

### Post by fallingleaf on 2008-12-21
> **2hot6ft2 said:**
> maybe kopete

I've tried Pidgin, Kopete, and Ayttm.  They all use the same login method.

---

### Post by Darth_tater on 2008-12-21
meebo

look at meebo.com.  i know its not an application, but i dont know of any multiprotocol IM application that will work without first creating an account.  only the single protocol applications like AIM, YIM, MSN, SKYPE will allow you to just sign on w/o an account.

best of luck

---

### Post by fallingleaf on 2008-12-21
> **Darth_tater said:**
> meebo

look at meebo.com.  i know its not an application, but i dont know of any multiprotocol IM application that will work without first creating an account.  only the single protocol applications like AIM, YIM, MSN, SKYPE will allow you to just sign on w/o an account.

best of luck

Actually, that's not a bad idea.  I'll play around with it a bit. I could just put an icon on the desktop, or maybe one for each protocol, that's really just a bookmark to Meebo.

---

### Post by ibuclaw on 2008-12-21
Two ideas on the table:

1) 
```
sudo apt-get install amsn
```
2)
```
echo "deb http://ppa.launchpad.net/galaxium/ubuntu hardy main" | sudo tee /etc/apt/sources.list.d/galaxium.list
sudo apt-get update && sudo apt-get install galaxium

```

Also, you may be interested in an app called **prism**

It's an web browser wrapper that makes sites (such as facebook, myspace, etc) look and feel like an application.

Regards
Iain

---

