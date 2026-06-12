---
title: "bypass login screen"
date: 2011-10-26
forum: Desktop Environments
---

### Post by yoramdavid on 2011-10-26
I am not sure which I am running, since I have both gnome and  gnome-fallback installed.

I had no xserver and no loginUI screen until I uninstalled LightDM and installed GDM.

I want to bypass the login screen when I boot up my computer so it boots directly into the desktop.
I managed to disable it asking the passowrd when starting in the user and groups application.

How do I do it, please?

---

### Post by amjjawad on 2011-10-26
Any idea what system are you using? 

```
lsb_release -a
```

---

### Post by yoramdavid on 2011-10-26
> **amjjawad said:**
> Any idea what system are you using? 

```
lsb_release -a
```

LSB Version:	core-2.0-amd64:core-2.0-noarch:core-3.0-amd64:core-3.0-noarch:core-3.1-amd64:core-3.1-noarch:core-3.2-amd64:core-3.2-noarch:core-4.0-amd64:core-4.0-noarch
Distributor ID:	Ubuntu
Description:	Ubuntu 11.10
Release:	11.10
Codename:	oneiric

---

### Post by amjjawad on 2011-10-26
My guess is you have Ubuntu NOT Lubuntu as your prefix says and you uninstalled its default login manager and installed GDM, right?

---

### Post by yoramdavid on 2011-10-26
> **amjjawad said:**
> My guess is you have Ubuntu NOT Lubuntu as your prefix says and you uninstalled its default login manager and installed GDM, right?

I am sorry about Lubuntu, I misschoosed. I have Ubuntu indeed. I tried to change the prefix, but could not.
Yes, I uninstalled its default login manager because I had problems with it. I do not mind either of them, but GDM works.
That is right.

---

### Post by amjjawad on 2011-10-26
> **yoramdavid said:**
> I am sorry about Lubuntu, I misschoosed. I have Ubuntu indeed. I tried to change the prefix, but could not.
Yes, I uninstalled its default login manager because I had problems with it. I do not mind either of them, but GDM works.
That is right.

Well, it's ok but I usually search for Lubuntu Threads and jump in. I'm a member of Lubuntu and it's my job.

Anyway, I'll try to help so never mind :)

I need to do some search for that.

[http://projects.gnome.org/gdm//index.html](http://projects.gnome.org/gdm//index.html)
[http://en.wikipedia.org/wiki/GNOME_Display_Manager](http://en.wikipedia.org/wiki/GNOME_Display_Manager)

You can do that too: [www.googlubuntu.com](www.googlubuntu.com)

---

### Post by sffvba[e0rt on 2011-10-26
*Prefix changed to **Ubuntu**.*

@OP, you can change the prefix AFAIK, edit your opening post next time and select "Advanced".


404

---

### Post by yoramdavid on 2011-10-26
> **amjjawad said:**
> Well, it's ok but I usually search for Lubuntu Threads and jump in. I'm a member of Lubuntu and it's my job.

Anyway, I'll try to help so never mind :)

I need to do some search for that.

[http://projects.gnome.org/gdm//index.html](http://projects.gnome.org/gdm//index.html)
[http://en.wikipedia.org/wiki/GNOME_Display_Manager](http://en.wikipedia.org/wiki/GNOME_Display_Manager)

You can do that too: [www.googlubuntu.com](www.googlubuntu.com)

Thank you.
All I find is that under System &#8594; Administration &#8594; Login Screen I could change those settings, but there is no such program installed.

---

### Post by yoramdavid on 2011-10-26
> **not found said:**
> *Prefix changed to **Ubuntu**.*

@OP, you can change the prefix AFAIK, edit your opening post next time and select "Advanced".


404

I did try to edit in "Advanced"... did not find the option there either, perhaps I did not look well enough.

---

### Post by amjjawad on 2011-10-26
> **not found said:**
> *Prefix changed to **Ubuntu**.*

@OP, you can change the prefix AFAIK, edit your opening post next time and select "Advanced".


404

Actually we don't have that access, only you guys have it :)

---

### Post by yoramdavid on 2011-10-29
Any help would be appreciated, I am still stuck with the problem.
Thanks.

---

### Post by yoramdavid on 2011-10-29
Any help would be appreciated, I am still stuck with the problem.
Thanks.

---

### Post by amjjawad on 2011-10-30
I'm trying to search for an answer and I found this link:

[http://www.webupd8.org/2011/07/how-to-switch-between-gdm-lightdm-or.html](http://www.webupd8.org/2011/07/how-to-switch-between-gdm-lightdm-or.html)

I have reached page 8 and still can't find anything that explains clearly how to replace LightDM with GDM!!!!!

---

### Post by yoramdavid on 2011-10-30
> **amjjawad said:**
> I'm trying to search for an answer and I found this link:

[http://www.webupd8.org/2011/07/how-to-switch-between-gdm-lightdm-or.html](http://www.webupd8.org/2011/07/how-to-switch-between-gdm-lightdm-or.html)

I have reached page 8 and still can't find anything that explains clearly how to replace LightDM with GDM!!!!!

I tried slim and it asks for username and password.
I re-installed lightdm-gtk-greeter and tried it and same problem as before, following these commands:
before logging in, press CTRL + ALT + F1 (for Virtualbox, press RIGHT CTRL + F1), log in to the console and run the following commands:
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install lightdm-gtk-greeter
sudo service lightdm restart
```
I get an error after:
```
sudo service lightdm restart
Unkown instance: 
```

---

### Post by amjjawad on 2011-10-31
I'm sorry but I'm really out of ideas :(
I've never tired that myself and currently, I'm using Lubuntu and not using Ubuntu any more. Is there any reason why you want to replace your login manager?

Perhaps it's not just to install another login manager and remove the other, it might require some other steps.

---

### Post by yoramdavid on 2011-10-31
> **amjjawad said:**
> I'm sorry but I'm really out of ideas :(
I've never tired that myself and currently, I'm using Lubuntu and not using Ubuntu any more. Is there any reason why you want to replace your login manager?

Perhaps it's not just to install another login manager and remove the other, it might require some other steps.

Yes, as I said in the first post, I had no xserver and no loginUI screen until I uninstalled LightDM and replaced it with GDM.
Thanks any way.

---

### Post by yoramdavid on 2011-10-31
Today it started again with "caught error 15" on shut down, and would not show the login screen.
What did I do? I found a setting under "user accounts" in the "system settings" (gnome-control-center --overview) program wher I could choose to automatically login and that seems to annoy the login manager.
I had to disable it.
The only thing I can do is disable GDM from asking the password at the login screen under "user definitions" (another program "user-admin").
Works only with GDM.

---

