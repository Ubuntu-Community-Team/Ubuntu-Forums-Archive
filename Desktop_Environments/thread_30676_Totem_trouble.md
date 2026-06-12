---
title: "Totem trouble"
date: 2005-04-29
forum: Desktop Environments
---

### Post by ZC3rr0r on 2005-04-29
Yep, you guessed it, Totem is doing nothing but spawning errors.
I wanted to play mp3's so I looked it up in the wiki, and I was told to download gstreamer0.8-mad. This had worked before on 4.10 so I expected no problems.I was wrong ;) because totem then told me: unknow error.

The same happens when I try to play DVD's, either that, or it returns a blank screen :(

Any good ideas on these problems?

---

### Post by bored2k on 2005-04-29
[http://ubuntuguide.org/#codecs](http://ubuntuguide.org/#codecs)

---

### Post by ZC3rr0r on 2005-04-29
Thanx alot,with that fixed it wanted to play a dvd. The lagging at first was staggering, untill I remembered I still had to set the dvd-player to DMA, after that everything was fine,except for the fact that the sound was lagging behind the images. Is this just becuase of the alsa or oss, or can it be fixed?

---

### Post by bored2k on 2005-04-29
[QUOTE=ZC3rr0r]Thanx alot,with that fixed it wanted to play a dvd. The lagging at first was staggering, untill I remembered I still had to set the dvd-player to DMA, after that everything was fine,except for the fact that the sound was lagging behind the images. Is this just becuase of the alsa or oss, or can it be fixed?[/QUOTE]
 Try opening your dvd's with VLC or Xine or MPlayer .. I'd suggest vlc

---

### Post by ZC3rr0r on 2005-04-30
I can install neither of them, even though i've added all the marrilat repositories,as well as the ubuntu ones in the tutorial page. What repository do I need to add to get these packages?

---

### Post by ZC3rr0r on 2005-05-01
Please some help? if I want to install vlc,xine or Mplayer, it starts whining over some packages,the most consistant one being libmodplug0 which isn't installable form any of my repositories. It also says it needs wxvlc (the frontend) but it says it will not be installed. How do i fix this? Does anyone know a repository which holds these files?

---

### Post by tread on 2005-05-01
I uncommented all the other repos in my /etc/apt/sources.list, and added these:

# added by sam
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) stable main
deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) unstable main
deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) testing main

I don't know which one provided wxvlc, but its there. Incidentally, search for wxvlc and not gvlc or something similar.

---

### Post by ZC3rr0r on 2005-05-02
Those are exactly the ones that I use, but I get some bla bla about libmodplug0 which it can't find but does require. And best of all, vlc says it nees wxvlc, and will not install till wxvlc is installed, and wxvlc says the same about vlc??? Hoe on earth do I get vlc working? Can i just get the debian packages off vlc's site?

---

### Post by tread on 2005-05-02
Strange .. doesnt synaptic offer to install the dependencies for you? 

Also, do you have any other repos in your sources.list file, which might be providing a different version of a required library and hence breaking the install?

---

### Post by ZC3rr0r on 2005-05-02
Synaptic (or apt-get for the matter) tries to resolve the dependencies, and comes up with the libmodplug0 package it wants to install, but can't find anywhere. I just want a repository which holds all the nececary files. My repo list looks like this: 
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) stable main
deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) unstable main
deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) testing main

Any ideas?

---

### Post by ZC3rr0r on 2005-05-02
This is the exact error as replied by apt:

sudo apt-get install vlc
Pakketlijsten worden ingelezen... Klaar
Boom van vereisten wordt opgebouwd... Klaar
Sommige pakketten konden niet geïnstalleerd worden. Dit kan betekenen dat u
een onmogelijke situatie gevraagd hebt of dat u de 'unstable'-distributie
gebruikt en sommige benodigde pakketten nog vastzitten in 'incoming'.

Aangezien u slechts een enkele opdracht gegeven hebt is het zeer
waarschijnlijk dat het pakket gewoon niet installeerbaar is. U kunt dan
best een foutrapport indienen voor dit pakket.
De volgende informatie helpt u mogelijk verder:

De volgende pakketten hebben niet-voldane vereisten:
  vlc: Vereisten: libmodplug0 (>= 1:0.7-1) maar het is niet installeerbaar
E: Niet-werkende pakketten:

Sorry if this is not readable,it is in dutch. Basicly it tells me I need to intsall libmodplug0 but it can't find it on the repositories it has in his listing.

---

