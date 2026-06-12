---
title: "sudo: gedit: command not found"
date: 2005-05-11
forum: Desktop Environments
---

### Post by ntrsfrml on 2005-05-11
Hey guys.. I just wanted to try Kubuntu..so installed it over my Ubuntu install.. I did play a lot with Ubuntu and everything seemed easy(THanks to Ubuntu Starter Guide \\:D//  ) ANyways... i have Kubuntu installed and i was trying to add some extra repositories.. 

I'm getting the following error with all gedit commands..

```
manu15@MSHOME:~$ sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
Password:
manu15@MSHOME:~$ sudo gedit /etc/apt/sources.list
sudo: gedit: command not found
manu15@MSHOME:~$

```

Is Gedit a Gnome command which is not accepted in KDE? Is there is an easy guide to Kubuntu? 

Also how can I install Firefox on Kubuntu?

many thanks :)

PS: the GUI looks sweet in Kubuntu

---

### Post by Kurse on 2005-05-11
Yes, gedit is a Gnome command. It would work if you had it and the Gnome libraries installed. Try kedit instead.

Kubuntu is simply Ubuntu linux with KDE, instead of Gnome.  Any KDE manual will help you, as will Google.

---

### Post by ntrsfrml on 2005-05-11
[QUOTE=Kurse]Yes, gedit is a Gnome command. It would work if you had it and the Gnome libraries installed. Try kedit instead.

Kubuntu is simply Ubuntu linux with KDE, instead of Gnome.  Any KDE manual will help you, as will Google.[/QUOTE]

I tried that.. same error :(

```
manu15@MSHOME:~$ sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
manu15@MSHOME:~$ sudo kedit /etc/apt/sources.list
sudo: kedit: command not found
manu15@MSHOME:~$


```

---

### Post by lt_kije on 2005-05-11
To check to see if a command will work, try
```
$ which COMMAND
```

This will search your path for the command; if it finds it, it will tell you where on your system it is. If neither gedit or kedit are on your system, try any of these:
*kate
*nano
*vim

The last two are command line editors which might take some getting used to. That said, they're powerful (especially vim) and found on most Linux/Unix systems.

To install any of those apps (assuming they don't exist on your system already), use Synaptic (GNOME), Kynaptic (KDE), or apt-get.
```
$ sudo apt-get install mozilla-firefox vim nano gedit kate
```

That would install all of the apps that've been mentioned so far. If you only need Firefox, don't include the others on the command line.

Good luck,

lt_kije

---

### Post by Kurse on 2005-05-11
[QUOTE=ntrsfrml]I tried that.. same error :(

```
manu15@MSHOME:~$ sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
manu15@MSHOME:~$ sudo kedit /etc/apt/sources.list
sudo: kedit: command not found
manu15@MSHOME:~$


```[/QUOTE]

apt-get install kedit

---

### Post by fromoze on 2005-05-12
Don't install kedit; just use kate (kde advanced text editor) is the remplacement of kedit.

I would be nice to make a kubuntu-guide... I've not time these days but I would help if someones is doing it.

---

### Post by topus on 2005-05-12
[QUOTE=ntrsfrml]I tried that.. same error :(
[/code][/QUOTE]

kedit is not installed by default.   [-X  
use kate or kwrite.

ciao
paolo :-P

---

### Post by booster on 2005-05-12
tried kate, no way, althought is installed;
then tried kwrite, works but gives me some errors upon launching.
this is the output, notice I tried twice to rule out a first time thing.

> leo@lianlinux:~$ sudo kwrite /etc/X11/xorg.conf
Password:
Error: "/var/tmp/kdecache-leo" is owned by uid 1000 instead of uid 0.
Link points to "/var/tmp/kdecache-root"
Error: "/tmp/kde-leo" is owned by uid 1000 instead of uid 0.
Link points to "/tmp/kde-root"
leo@lianlinux:~$ sudo kwrite /etc/X11/xorg.conf
Error: "/var/tmp/kdecache-leo" is owned by uid 1000 instead of uid 0.
Link points to "/var/tmp/kdecache-root"
Error: "/tmp/kde-leo" is owned by uid 1000 instead of uid 0.
Link points to "/tmp/kde-root"
leo@lianlinux:~$

what finally works best for me is gedit, then I can follow the ubuntu guides transparantly even though I use kubuntu. KDE3.4

> sudo apt-get install gedit

then for instance:
> sudo gedit /etc/X11/"whateverfile"

---

### Post by wwwolf on 2005-05-12
[QUOTE=fromoze]Don't install kedit; just use kate (kde advanced text editor) is the remplacement of kedit.

I would be nice to make a kubuntu-guide... I've not time these days but I would help if someones is doing it.[/QUOTE]

kate is great for user stuff but it will spit up if you try to 'sudo kate'
when editing with root permissions, it is better to use nano (sudo nano).

---

