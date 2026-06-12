---
title: "What are you guys using to burn multisession CD/DVD?"
date: 2006-06-25
forum: Desktop Environments
---

### Post by kpkeerthi on 2006-06-25
Is there a K3B clone for GNOME that I can use to burn data CD/DVD in multiple sessions? I tried nautilus and apparently it doesn't seem to support multiple sessions. And the gnome baker, though it has the feature, it simply won't work. Any suggestions? Thanks.

---

### Post by temis01 on 2006-06-26
K3B is a multiplateform software, it works great under gnome !

---

### Post by kpkeerthi on 2006-06-26
Yeah but... mmm... ok... here is why i'm hesitant about installing k3b in GNOME:
> 
[22:34:10-bash]~$ sudo aptitude -s install k3b
Password:
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done

[B]The following NEW packages will be installed:
  k3b kamera kcontrol kdebase-bin kdebase-kio-plugins kdelibs-bin
  kdelibs4c2a kdemultimedia-kio-plugins kdesktop kicker libavahi-qt3-1
  libdbus-qt-1-1c2 libflac++5c2 libk3b2 libkcddb1 libkonq4 libopenexr2c2a
  libpcre3
[/B]0 packages upgraded, 18 newly installed, 1 to remove and 0 not upgraded.
Need to get 15.2MB/28.1MB of archives. After unpacking **69.0MB** will be used.


---

### Post by amunimanghi on 2006-06-26
You could try [gnomebaker.]("gnomebaker.sourceforge.net/") ```
 sudo apt-get install gnomebaker
```

[IMG]http://www.biddell.co.uk/images/gnomebaker/gb02_01.jpg[/IMG]

---

### Post by kpkeerthi on 2006-06-26
Thanks. But if you read my first post... I'm having an annoying problem with gnome-baker not doing a multi-session burns the way it should. It supports but doesn't work. And thats the reason I'm looking for a good burner like k3b. I liked it but I do not want to install a whole lotta packages in GNOME just for k3b. I do not have KDE installed at the moment.

---

### Post by ayoli on 2006-06-26
i use graveman wich is apt-getable, but i havent yet tried multisession burning with it.
regards.

---

### Post by theslut on 2006-06-26
Bonfire is a decent gnome based burning app. i think it does multiple seesions but not sure.

---

### Post by ayoli on 2006-06-26
[QUOTE=theslut]Bonfire is a decent gnome based burning app. i think it does multiple seesions but not sure.[/QUOTE]
bonfire seems to be based on libnautilus-burn and kpkeerthi said above that natilus-burn apprently doesnt work for multi session.
however, bonfire has a nice gui.

---

### Post by matrooswolf on 2006-06-26
[QUOTE=kpkeerthi]Yeah but... mmm... ok... here is why i'm hesitant about installing k3b in GNOME:[/QUOTE]
Don't be afraid, I am using K3b under gnome all the time, works great (better than nero, thinking about it, isn't there a nero for linux version also?)
(but forget I ever said that, give K3b a try ;))

I use Amarok as a musicplayer and it is well integrated with K3b (everything under gnome ...)

---

### Post by ayoli on 2006-06-26
[QUOTE=matrooswolf]Don't be afraid, I am using K3b under gnome all the time, works great (better than nero, thinking about it, isn't there a nero for linux version also?)
(but forget I ever said that, give K3b a try ;))

I use Amarok as a musicplayer and it is well integrated with K3b (everything under gnome ...)[/QUOTE]
he maybe just don't want to have all extra libs installed since it gonna use 69Mb of space.

---

### Post by matrooswolf on 2006-06-26
[QUOTE=ayoli]he maybe just don't want to have all extra libs installed since it gonna use 69Mb of space.[/QUOTE]
Yes could be, didn't think about that, if space is the issue ...

---

### Post by amunimanghi on 2006-06-26
Sorry bout that. I didn't see that you tried gnomebaker. :-p

---

### Post by krye on 2006-06-26
If I were you I'd give **bonfire** a try. I don't have a dvd recorder, but multisession works just fine on CD's.

Also, I find the interface just as usable as that of k3b.

---

### Post by Rouquier on 2006-07-08
Hi,

I'm bonfire author and I can confirm that bonfire does multisession for both CD and DVD.
NOTE: nautilus-cd-burner is not used for burning, bonfire relies on its own library.

---

### Post by drakeoutlaw on 2006-07-28
xcd-roast is the short simple answer to your problems. It will do multisession and it does not require kdelibs.

---

### Post by NZ-Wanderer on 2006-07-28
Hope you don't mind me poking my nose in here, but how do you get Bonfire?? - I looked for it in synaptic, but it doesn't seem to be there (and I not very good at installing Linux stuff from the web.,..)

---

### Post by missmoondog on 2006-07-28
graveman doesn't do multi session burns either. always wants to format the cd, although the option is there. 

does k3b do multi session correctly. i recently switched from ubuntu/graveman to kubuntu/k3b and haven't tried doing a multi session cd yet.

---

### Post by visvak on 2006-07-28
try neroLINUX. works well apparently.

never had any probs with GnomeBaker

---

### Post by tturrisi on 2006-07-28
you can do multisession from the commandline:
[http://www-128.ibm.com/developerworks/linux/library/l-cdburn.html](http://www-128.ibm.com/developerworks/linux/library/l-cdburn.html)

---

### Post by flamarro on 2006-08-01
> **NZ-Wanderer said:**
> Hope you don't mind me poking my nose in here, but how do you get Bonfire?? - I looked for it in synaptic, but it doesn't seem to be there (and I not very good at installing Linux stuff from the web.,..)

really, try bonfire, it was one thing that was giving me some itchings too. I tryed and works like a charm. Look at [here]("http://www.ubuntuforums.org/showthread.php?t=175536&page=11&highlight=bonfire") and to this day at the bottom there's just what you want

---

