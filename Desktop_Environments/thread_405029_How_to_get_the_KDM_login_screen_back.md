---
title: "How to get the KDM login screen back"
date: 2007-04-09
forum: Desktop Environments
---

### Post by pranav on 2007-04-09
I installed Kubuntu (edgy)

Then i installed gnome from Adept (simply the package gnome)

I chose default desktop environment as gdm (out of curiosity)

Now I get a text based login screen and then i have to type "startx"

And it takes me to Gnome environment directly

If i signout/logout it throws me back to command line login page

I want to be able to see a GUI login screen(doesnt matter which) and select a session-type of my choice and then login 


What should i do?


Also in the Gnome environment... i cant see any option to shutdown or restart my PC.


I am stuck. I tried reboot and shutdown commands in commandline.... however it threw up some very long error message and i couldnt shut the pc

SO i am guessing if i get the kdm login screen back i will be able to shut down from there.

Please help.

---

### Post by teaker1s on 2007-04-09
not sure exactly what has happened, lets try
```
sudo apt-get install kdm
```
```
sudo dpkg-reconfigure kdm
```

failing that unless someone has more info I'd suggest completely removing kdm with synaptic and reinstalling-I've had weird issues with it where run level settings somewhere are messed up

---

### Post by pranav on 2007-04-09
i get the following error upon typing the very 1st line

> E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?


---

### Post by sam81 on 2007-04-09
I'm not sure, but you might try

sudo dpkg-reconfigure kdm

and it might give you the option to choose it as default login manager, otherwise, I've noticed that just uninstalling kdm and then reinstalling it again, prompts you for the choiche of the default login manager

Edit: sorry, I didn't notice it was answered already...

---

### Post by pranav on 2007-04-09
upon doing
> sudo dpkg-reconfigure kdm

i get an error as follows:
> debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process


---

### Post by teaker1s on 2007-04-09
unless you have a package manager running, it sounds like a broken package

[http://ubuntuforums.org/showthread.php?t=404876&highlight=dpkg]("http://ubuntuforums.org/showthread.php?t=404876&highlight=dpkg")

---

