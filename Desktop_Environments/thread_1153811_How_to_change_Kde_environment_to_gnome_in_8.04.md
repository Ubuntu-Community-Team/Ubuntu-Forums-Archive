---
title: "How to change Kde environment to gnome in 8.04?"
date: 2009-05-09
forum: Desktop Environments
---

### Post by somepalli on 2009-05-09
[COLOR="Green"]In my Ubuntu i got default environment is GNOME but i installed KDE also.

when i am installing some software My package manager broken ,

then i fixed my broken packages but i lost GNOME my environment. 
[/COLOR]
[COLOR="Red"]Now i am would like change to KDE and another issue i lost my login manager.[/COLOR] 

[COLOR="Green"]now i am login through only command prompt like following[/COLOR]

[COLOR="Red"]when i am using startx its not able to start desktop environment. 

i have start using sudo like #sudo startx
[/COLOR]

Thanx in advance

---

### Post by Triptol on 2009-05-09
When you are on your command prompt try the following:

```
sudo aptitude purge gdm kdm
```

This will remove the kde and gnome login manager from your system. Then try the following:

```
sudo aptitude install ubuntu-desktop
```

or 

```
sudo aptitude install kubuntu-desktop
```

The first one will install the gnome desktop, the latter the kde desktop. You need, a working internet connection to get this running, or a (k)ubuntu installation CD/DVD.

---

### Post by somepalli on 2009-05-11
I installed Gnome using
sudo aptitute install gnome-desktop
but i didn't get gnome desktop environment.Now it is KDE only. how i can bring GNOME environment..

---

### Post by andrea000 on 2009-05-11
sudo aptitude remove kubuntu-desktop should, in theory, get rid of it. 
If you uninstall kdelibs-bin or kdelibs-data or kdelibs4c2 it will uninstall
almost every KDE program. After uninstalled them, search in Synaptic for 'kde
and uninstall the other packages that have not been un installed.

---

### Post by micio on 2009-05-11
Try to explain better the step in which you are.

Have you installed gnome?

Have you already installed xorg-xserver and kdm/gdm in your system?

Have you tried to run "sudo /etc/init.d/g(k)dm start" ?

When starts kdm or gdm, click on "session" then you can choose the environment selecting GNOME.

---

### Post by somepalli on 2009-05-12
I installed  gnome-desktop to get gnome environment with the following command
[COLOR="Green"][SIZE="4"]sudo aptitute install gnome-desktop[/SIZE][/COLOR]
then i given startx

---

### Post by micio on 2009-05-12
Instead of 

```
startx
```

try this command

```
sudo /etc/init.d/gdm restart
```

---

### Post by somepalli on 2009-05-23
Thank you for your sugestions.........

---

### Post by Tibuda on 2009-05-23
> **andrea000 said:**
> sudo aptitude remove kubuntu-desktop should, in theory, get rid of it. 
If you uninstall kdelibs-bin or kdelibs-data or kdelibs4c2 it will uninstall
almost every KDE program. After uninstalled them, search in Synaptic for 'kde
and uninstall the other packages that have not been un installed.

See this:
[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

---

