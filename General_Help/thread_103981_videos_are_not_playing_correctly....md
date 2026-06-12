---
title: "videos are not playing correctly..."
date: 2005-12-15
forum: General Help
---

### Post by taseal on 2005-12-15
I'm trying to play a wmv video, and I get sound but no video... 

I have installed the codecs... 

i'm trying to use totem btw...

anyone know why?

I had a similar problem on my desktop.... it would play the video too fast and sound at normal rate, so things would be out of synch

---

### Post by frodon on 2005-12-15
Do you have the same problems with VLC ?

By the way, if you use totem with gstreamer (default) i advice you to change for xine, just install the totem-xine package to do that.

---

### Post by taseal on 2005-12-15
[QUOTE=frodon]Do you have the same problems with VLC ?

By the way, if you use totem with gstreamer (default) i advice you to change for xine, just install the totem-xine package to do that.[/QUOTE]

what is vlc? 

where do i change what engine I use it with on totem? and what would I write in terminal for tat?

apt-get totem-xine?

sorry i'm new with linux :(

---

### Post by taseal on 2005-12-15
ah ok, I figured out how to install the package thingy.......

---

### Post by taseal on 2005-12-15
ok now it wont even play with just sound... I get the error

totem could not play the file
video codec 'MS WMV 9(win 32) is not handled. you might need to install additional plugins...

what now?

---

### Post by frodon on 2005-12-15
The easiest way in ubuntu to install software is to use synaptic : [https://wiki.ubuntu.com/SynapticHowto?](https://wiki.ubuntu.com/SynapticHowto?)
However you could install totem-xine with this command line : ```
sudo apt-get install totem-xine
```
vlc is another player, you will find it in synaptic.
If you didn't set your repositories yet (it's where apt-get commands and synaptic look for packages) i advice you to follow this guide : [http://www.ubuntuforums.org/showthread.php?t=76132&highlight=backport](http://www.ubuntuforums.org/showthread.php?t=76132&highlight=backport)

---

### Post by frodon on 2005-12-15
ok, you're quick to answer ;)

I think if you are a newbie and if you have never done anything on your ubuntu box you should run automatix : [http://ubuntuforums.org/showthread.php?t=66563](http://ubuntuforums.org/showthread.php?t=66563)
Automatix will install for you all the codecs and many other cool stuff, so have a look to the link i gave and let me know if you still have some issues.

Good luck.

---

### Post by taseal on 2005-12-15
[QUOTE=frodon]The easiest way in ubuntu to install software is to use synaptic : [https://wiki.ubuntu.com/SynapticHowto?](https://wiki.ubuntu.com/SynapticHowto?)
However you could install totem-xine with this command line : ```
sudo apt-get install totem-xine
```
vlc is another player, you will find it in synaptic.
If you didn't set your repositories yet (it's where apt-get commands and synaptic look for packages) i advice you to follow this guide : [http://www.ubuntuforums.org/showthread.php?t=76132&highlight=backport](http://www.ubuntuforums.org/showthread.php?t=76132&highlight=backport)[/QUOTE]
yup I figured it out, thx :)

but with totem-xine it gives me that error I mentioned above... will not even play with just sound

---

### Post by taseal on 2005-12-15
I mostly all the goodies installed, including the codecs, but i'll give automatix a shot :)

---

### Post by taseal on 2005-12-15
Just did automix, but I had most of the stuff already installed...

videos are still nogo... 

:(

---

### Post by frodon on 2005-12-15
Did you install w32codecs ? : [http://ubuntuforums.org/showthread.php?t=81577](http://ubuntuforums.org/showthread.php?t=81577)

---

### Post by taseal on 2005-12-15
lol, i thought I did, but apparently not....

well its installing it now...

automix should have installed it though, i wonder why it didnt...

---

