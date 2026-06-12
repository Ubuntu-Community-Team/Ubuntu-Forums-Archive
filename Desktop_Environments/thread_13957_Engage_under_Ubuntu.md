---
title: "Engage under Ubuntu"
date: 2005-02-03
forum: Desktop Environments
---

### Post by M-Rick on 2005-02-03
Is it possible to use engage under Ubuntu ?

If yes, what must i do ?

---

### Post by roberTO on 2005-02-04
[QUOTE=M-Rick]Is it possible to use engage under Ubuntu ?

If yes, what must i do ?[/QUOTE]

Yes!!!

add this line to apt sources.list:
deb [http://j.portalier.free.fr/debian/](http://j.portalier.free.fr/debian/) testing main

apt-get update && apt-get install engage..........

See this screen...

[BIGGER!](http://www.users.monornet.hu/linux/ubuntu/engage.jpg) 

[IMG]http://www.users.monornet.hu/linux/ubuntu/engage_thumb.jpg[/IMG]

---

### Post by M-Rick on 2005-02-04
But no PPC version :( only x86

---

### Post by roberTO on 2005-02-04
Opps...
Sorry i not read ful post...
Only way...
CVS!

I upload e17 cvs script my webpage.
Download:
[e17-cvs.zip](http://www.users.monornet.hu/linux/ubuntu/e17-cvs.zip) 

and build order:

[http://www.enlightenment.org/pages/cvsnotes.html](http://www.enlightenment.org/pages/cvsnotes.html)

bye!

---

### Post by jdodson on 2005-02-04
what is engage?

---

### Post by llamakc on 2005-02-05
The Enlightenment Project's OSX Dock-like taskbar. Once E17 (if ever) is released you'll hear much, much more about it. I like Engage much more than the App Launcher for GDesklets.

---

### Post by stwog on 2005-02-05
[QUOTE=llamakc]The Enlightenment Project's OSX Dock-like taskbar. Once E17 (if ever) is released you'll hear much, much more about it. I like Engage much more than the App Launcher for GDesklets.[/QUOTE]
 Cool, so I installed it, but now how do I use and configure it? I can't find any documentation anywhere... 

Simon

---

### Post by Titeuf on 2005-02-05
[QUOTE=stwog]Cool, so I installed it, but now how do I use and configure it? I can't find any documentation anywhere... 

Simon[/QUOTE]
There is excellent documentation about E17 and engage [here](http://lude.net/edocs/engage.htm)

---

### Post by skauch on 2005-02-17
Is it possible to use engage under Warty ? \\:D/ 
I can't install in Warty  ](*,) 
In Synaptic:

libecore1 but it is not going to be installed
libedje0 but it is not going to be installed
libemotion0 but it is not going to be installed
libesmart0 but it is not going to be installed
libetox0 but it is not going to be installed
libevas2 but it is not going to be installed
libewl0 but it is not going to be installed
libimlib2 but it is not going to be installed
libpng12-0 but 1.2.5.0-7ubuntu1 is to be installed

---

### Post by Jad on 2005-02-18
hmm is it KDE based theme?

---

### Post by EndersGame on 2005-02-18
Does Engage require Enlightment or can you use the toolbar in GNOME?

---

### Post by macewan on 2005-02-18
per roberTO

wget http://www.users.monornet.hu/linux/ubuntu/e17-cvs.zip

instructions
[http://www.enlightenment.org/pages/cvsnotes.html](http://www.enlightenment.org/pages/cvsnotes.html)

for each you will ./autogen.sh; make; sudo make install

I got as far as esmart and then it barfs.

---

### Post by Dullin on 2005-03-06
[QUOTE=skauch]Is it possible to use engage under Warty ? \\:D/ 
I can't install in Warty  ](*,) 
In Synaptic:

libecore1 but it is not going to be installed
libedje0 but it is not going to be installed
libemotion0 but it is not going to be installed
libesmart0 but it is not going to be installed
libetox0 but it is not going to be installed
libevas2 but it is not going to be installed
libewl0 but it is not going to be installed
libimlib2 but it is not going to be installed
libpng12-0 but 1.2.5.0-7ubuntu1 is to be installed[/QUOTE]


Okay, after some hard work in synaptic (I now hate that little bugger). I was able tu run it and here's how to do it.

The problem resides in an outdated version of libpng12-0. Unfortunatly, the warty deb tree doesn't contain the appropriate version and we need to get it from hoary.

The first thing is to had this line in /etc/apt/sources.list and add
```
deb http://archive.ubuntu.com/ubuntu/ hoary main restricted universe multiverse
```

You then need to refresh your packages in synaptic (or do a sudo apt-get update)

After that, go back in synaptic and search for libpng12-0 and mark it as an upgrade.

Apply.


Go and remove the line you added in sources.list

Another sudo apt-get update

Get back in synaptic and search for engage

Install

Enjoy

---

### Post by doobs on 2005-03-07
Yeah !

great ! I'll try to add engage tonight to  my warty !

Thanks for the tip !

Edit : Hey !! It works !! Just have to configure now...
note : you could install "examine", it seems to be usefull to configure engage

---

### Post by lizardking on 2005-03-07
someone can help me with engage configuration??? i doon't understand how to set the icons.

i'm with ubuntu warty..

bye

---

### Post by jzke on 2005-08-18
Is it possible to install a stable version in Hoary? 

If I install it from Synaptic, and run it from the terminal it shows up as a grey bar down the bottom, and some buggy images appear and my whole system becomes very jumpy and unstable! Any ideas?

---

### Post by drummer on 2005-08-18
[QUOTE=EndersGame]Does Engage require Enlightment or can you use the toolbar in GNOME?[/QUOTE]
 I have e17 installed and was playing around with it a while back, and had engage in my gnome desktop by adding it to the list of startup commands in Preferences > Session.
This is a pic of my desktop as it was (has recently changed, now that I have a bigger, flat screen :D ):
[http://ubuntuforums.org/gallery/showimage.php?i=409&original=1&c=2](http://ubuntuforums.org/gallery/showimage.php?i=409&original=1&c=2)

---

### Post by M-Rick on 2005-08-18
is it possible to have a transparent dock ?

---

### Post by drummer on 2005-08-18
[QUOTE=M-Rick]is it possible to have a transparent dock ?[/QUOTE]
 Yes, but that didn't work too well for me. When the actual panel is transparent, it is only 'fake' transparency so grabs a shot of the desktop and put's that behind it (like transparency in gnome-terminal). It also had a whole block of the grabbed desktop along the bottom, blocking everything else, so didn't look too nice. It works nicer in e17, but then again it wasn't exactly designed to run from within gnome.

The command I ran when using engage was this:
engage -m 0 -R 0 -T 0 -g 0 -G 0 -i 1 -l 1 -A 1

---

### Post by jzke on 2005-08-25
[QUOTE=drummer]Yes, but that didn't work too well for me. When the actual panel is transparent, it is only 'fake' transparency so grabs a shot of the desktop and put's that behind it (like transparency in gnome-terminal). It also had a whole block of the grabbed desktop along the bottom, blocking everything else, so didn't look too nice. It works nicer in e17, but then again it wasn't exactly designed to run from within gnome.

The command I ran when using engage was this:
engage -m 0 -R 0 -T 0 -g 0 -G 0 -i 1 -l 1 -A 1[/QUOTE]
 So how did you get it to run under Hoary?

---

### Post by drummer on 2005-08-25
[QUOTE=jzke]So how did you get it to run under Hoary?[/QUOTE]
 I built the whole e17 desktop environment from cvs and installed engage from cvs as well. I previously tried to install engage from .debs but it was quite a headache. There are a few howtos on e17 in the forums, both installing from cvs and from repos, you basically need most of e17 to run engage (many of the enlightenment graphics libraries) so you may as well install the e17 desktop as well.. it's fun to play around with too :)

[http://ubuntuforums.org/showthread.php?t=46105&highlight=e17+howto](http://ubuntuforums.org/showthread.php?t=46105&highlight=e17+howto)
[http://ubuntuforums.org/showthread.php?t=59568&highlight=e17+howto](http://ubuntuforums.org/showthread.php?t=59568&highlight=e17+howto)
[http://ubuntuforums.org/showthread.php?t=30525&highlight=e17+howto](http://ubuntuforums.org/showthread.php?t=30525&highlight=e17+howto)

---

### Post by ramasdf123 on 2006-09-04
is this still possible and if it is, how do i install it?

---

