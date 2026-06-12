---
title: "help on editing start up services"
date: 2005-01-07
forum: Desktop Environments
---

### Post by earobinson on 2005-01-07
is there a program that i can install that will let me edit the start up services in a gui? if not is there a good turorial for doing it?

---

### Post by tiiim on 2005-01-07
cant remember where but i doupt there be a gui i think its prob only mandrake that may do a gui for that.

If your talking of start up servers for gnome that one thing but if your talking about bootup services then

there be in the /etc/rcx.d

where x is a number not sure which number to edit in Ubuntu.

another forum was [http://www.linuxquestions.org/questions/history/269587](http://www.linuxquestions.org/questions/history/269587)

which had the way of taking things away

also man update-rc.d has info. im assuming you remove the files in folder but i may be completely wrong.

also you have to look . init.d around there. but i personally think someone who knows more about Ubuntu should post here. OI PEOPLE POST NOW!

---

### Post by earobinson on 2005-01-07
FC3 also has a services editor realy so no easy way to do this in ubuntu i real need a good tutorial then that starts from scratch

---

### Post by zeroK on 2005-01-07
[QUOTE=earobinson]is there a program that i can install that will let me edit the start up services in a gui? if not is there a good turorial for doing it?[/QUOTE]
 I'm not sure, but perhaps the sysv* packages offer something for you :-)

---

### Post by earobinson on 2005-01-12
[QUOTE=zeroK]I'm not sure, but perhaps the sysv* packages offer something for you :-)[/QUOTE]
 not that i can see

---

### Post by jetta92 on 2005-01-13
very simple way of doing this .....

sudo apt-get install rcconf 

then sudo rcconf 

uncheck all unwanted services .... It's not a gui but it is done in the terminal also what doesn't get removed through there just do  ...  update-rc.d -f <servicename> remove and it will be gone

 :lol:

---

### Post by JackDog on 2005-01-13
This would be a very nice feature to have in gnome. Does anyone know of a gnome project to create a service editor? I know KDE has one as well as most major commercial distros...

---

### Post by earobinson on 2005-01-13
[QUOTE=jetta92]very simple way of doing this .....

sudo apt-get install rcconf 

then sudo rcconf 

uncheck all unwanted services .... It's not a gui but it is done in the terminal also what doesn't get removed through there just do  ...  update-rc.d -f <servicename> remove and it will be gone

 :lol:[/QUOTE]
 rcconf is usefull but do i just have to google each service to see if i want to use it or not?

---

### Post by kozuch on 2005-01-13
Sorry for Spanish, but what about this:

jan@Ubuntu211:~ $ sudo apt-get install rcconf
Password:
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias... Hecho
E: No se pudo encontrar el paquete rcconf
jan@Ubuntu211:~ $ sudo rcconf
sudo: rcconf: command not found

---

### Post by jetta92 on 2005-01-13
well what services do you need to know about let me know what you need to know about ....  Also you don't want to disable things like alsa, bootmisc.sh, bootclean.sh, ( you know ) .... bootclean.sh is really a useful script because it cleans out all the stale locks, /tmp files, lost&found files and a bunch of other crap ... Let me know ...

rcconf BTW is the debian tool for services config....

---

### Post by jetta92 on 2005-01-13
Kozuch.... Make sure you have the universe repository enabled then run ...

sudo apt-get update && sudo apt-get install rcconf

---

### Post by duff on 2005-01-13
Why doesn't Ubunu include the `boot` and `services` components that come with Gnome System Tools?  I used to use those on my brief stint with Debian.

---

### Post by jetta92 on 2005-01-13
Regular Debian Sarge includes boot but not services if memory serves right .... I haven't used standard debian in quite sometime I've used Ubuntu and Libranet for awhile now but last I remember Sarge only included boot and not services.... The rcconf tool and update-rc.d work just as well once you learn how to use them ....  ;-)

---

### Post by danip on 2005-01-13
Ubuntu comes with a program to edit this.

computer>desktop preferences>sessions

---

### Post by jetta92 on 2005-01-14
Sessions is not quite the same,  that only disables a few services for the current session what they wanna do is turn off major services like ssh, inetd, proftpd, samba, stuff like that ... Sessions tool won't do that

---

### Post by alainhenry on 2005-01-14
I saw a mention of rcconfig in another forum.  Is this the same as rcconf, or another program with similar capacilities ?  
Alain

---

### Post by jetta92 on 2005-01-14
Yeah samething pretty much rcconf, rcconfig.... same thing  =D>

---

### Post by GilGalad on 2005-01-21
[QUOTE=earobinson]rcconf is usefull but do i just have to google each service to see if i want to use it or not?[/QUOTE]

As root you can type:

/usr/sbin/update-rcconf-guide

When you run rcconf you will have a summary of what each service is about.

Other tools to edit services are:

sysvconfig
sysv-rc-conf

Cheers,

   Eddie.

---

### Post by MrTrumpets on 2005-01-21
I've also been looking for something similar...
I use a Linksys wireless PCI card and have to run the following commands EACH TIME I boot..


sudo modprobe ndiswrapper
sudo ifup wlan0



That's the only way it will get an IP address..  Will this rcconf let me add these commands upon bootup?

---

### Post by piedamaro on 2005-01-21
Put those commands in /etc/init.d/bootmisc.sh

---

