---
title: "Problem Playing MP3s"
date: 2005-11-26
forum: Desktop Environments
---

### Post by bigmikeherrmann on 2005-11-26
I am having problems playing MP3s that are on my hard drive. I tried just clicking them but then it takes me to Totom movie player and it says no decoders can be found. where can i get these decoders

---

### Post by 0okami on 2005-11-26
[QUOTE=bigmikeherrmann]I am having problems playing MP3s that are on my hard drive. I tried just clicking them but then it takes me to Totom movie player and it says no decoders can be found. where can i get these decoders[/QUOTE]

you need proper plugins to play MP3. 
try this in a terminal: 

sudo apt-get install gstreamer0.8-mad
Please reply so we know if this solved your issue or not.

---

### Post by syklitengutt on 2005-11-26
or go to this site and do as folowing:
[http://www.ubuntuguide.org/#codecs]("http://www.ubuntuguide.org/#codecs")

---

### Post by bigmikeherrmann on 2005-11-26
I Get This messege saying that it cant be found


ubuntu@your-i0mmef9hzg:~$ sudo apt-get install gstreamer0.8-plugins
Reading package lists... Done
Building dependency tree... Done
Package gstreamer0.8-plugins is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package gstreamer0.8-plugins has no installation candidate

---

### Post by tommythecat on 2005-11-26
I had the same problem and found that all I needed to do was install all of the xmms components and then I installed amarok (which is a great player)

sudo apt-get install xmms*

then 

sudo apt-get install amarok*


Then once in amarok I had to import my songs and chose xineas the engine and now all my mp3s play great and I have a great player app.

---

### Post by bigmikeherrmann on 2005-11-26
K thanx ill try that

---

### Post by 0okami on 2005-11-26
[QUOTE=bigmikeherrmann]I Get This messege saying that it cant be found


ubuntu@your-i0mmef9hzg:~$ sudo apt-get install gstreamer0.8-plugins
Reading package lists... Done
Building dependency tree... Done
Package gstreamer0.8-plugins is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package gstreamer0.8-plugins has no installation candidate[/QUOTE]


I didnt say: gstreamer0.8-plugins
ubuntu@your-i0mmef9hzg:~$ sudo apt-get install gstreamer0.8-plugins

it should be: gstreamer0.8-mad
ubuntu@your-i0mmef9hzg:~$ sudo apt-get install gstreamer0.8-mad


However, i now remember having mp3 support before I did this... So now that I think about it, this will allow you be able to record Mp3 To CDA in k3b and gnomebaker... not quite what your looking for but its a try. 

Im not at my machine now, but wheen I get home, i'll be able to tell you for certain. Someone might be able to help you before i get home.

---

### Post by RAOF on 2005-11-26
MP3 playback (along with all the other patent-encumbered media codecs) is not installed out of the box in Ubuntu.  However, it is very easy to install them.  Just follow [this guide]("http://help.ubuntu.com/starterguide/C/ch03.html#sect-music-and-movies").

---

### Post by eazolan on 2005-11-27
Thanks!

I was having a bizzare problem where I could play MP3s in my user account, but not the original account I created when installing ubuntu.

Installing gstreamer fixed it. :KS

---

