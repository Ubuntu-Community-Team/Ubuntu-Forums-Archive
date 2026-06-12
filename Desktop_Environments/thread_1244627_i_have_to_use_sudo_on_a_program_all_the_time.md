---
title: "i have to use sudo on a program all the time"
date: 2009-08-19
forum: Desktop Environments
---

### Post by andrea000 on 2009-08-19
I downloaded a trial of varicad and when i
go to run it i have to run sudo varicad all
the time i have changed the properties on it
to were i am the owner but i still have to
use sudo how can i get this to work right i
also have to do it on truecrypt and changing
the properties on it messes it up and i have
had to reinstall that one.

---

### Post by Copernicus1234 on 2009-08-19
You can increase the time until you need to type the sudo password again by reading this: [http://alouche.net/blog/2009/05/19/how-to-change-sudo-cache-timeout/](http://alouche.net/blog/2009/05/19/how-to-change-sudo-cache-timeout/)

The program needs root rights if it asks, so your best bet is probably to just increase the timeout so you dont have to type it so often.

---

### Post by doas777 on 2009-08-19
I would just add 'gksu ' to a launcher for your app, so you can doublick it, and put in your password, and go.

---

### Post by andrea000 on 2009-08-19
I have tried adding gksu to a launcher it will not
even start i have to open a terminal and type it in
increasing the time until i need to type the password
in may work i'll try that and see

---

### Post by doas777 on 2009-08-20
ummm, that does not sound right.
a process started with sudo/gksu will have admin rights as long as it is running, and any child processes it spawns will start with those privs as well. 

nothing about a sudo'ed process relies on the timer, that is just for subsequent processes. 

I use truecrypt all the time and you DO NOT NEED TO SUDO IT. it will prompt for it;'s own elevation instructions. Do not take ownership of files unless you know exactly what you are doing. it will seriously break stuff if you change ownership on the wrong thing, and it sounds like that may be the cause of your problems in the first place.

---

### Post by andrea000 on 2009-08-24
> **doas777 said:**
> ummm, that does not sound right.
a process started with sudo/gksu will have admin rights as long as it is running, and any child processes it spawns will start with those privs as well. 

nothing about a sudo'ed process relies on the timer, that is just for subsequent processes. 

I use truecrypt all the time and you DO NOT NEED TO SUDO IT. it will prompt for it;'s own elevation instructions. Do not take ownership of files unless you know exactly what you are doing. it will seriously break stuff if you change ownership on the wrong thing, and it sounds like that may be the cause of your problems in the first place.
ok i have it now i went into nautilus and changed the
ownership back to the way it was now truecrypt works
with out gksu but varicad will not.[Here]("http://www.varicad.com/en/home/") is the web
address if you would like to look at there manual why
it's acting that way

---

