---
title: "I get warning about not running as root"
date: 2006-08-09
forum: Desktop Environments
---

### Post by jis on 2006-08-09
It is like this :
"Not runing as root

The application will run in read-only mode. You will not be able to change the package database."

It is odd that the dialog does not tell which application it means. (I had two terminals, Gain and gFTP open.) I got this warning dialog right after starting to use Xubuntu today.

---

### Post by kaffelars on 2006-08-09
I know that Synaptic gives this error if you run it as a regular user. I guess the update manager will do the same, as it uses the package database, but not any the apps you mention..

Could it be something you run in the background?

---

### Post by jis on 2006-08-09
I did not close Synaptic earlier when I shut down, so Xubuntu was trying to run Synaptic (and ran it after I closed the previously mentioned dialog box). I think the OS should tell what application it is telling about and give possibility to authenticate.

---

### Post by kaffelars on 2006-08-10
Good point :) 
I've gotten that error a few times, but that's my own fault. I have tried to start Synaptic while running apt from the command line ;)

---

