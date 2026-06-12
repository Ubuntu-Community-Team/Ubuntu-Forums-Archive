---
title: "Howto play mp3"
date: 2005-12-03
forum: Desktop Environments
---

### Post by CKCK on 2005-12-03
Want to play mp3. But no decoders/plugins are found.
So I tried:
apt-cache search gstreamer

Same problem, on the forum someone said:
apt-cache search gstreamer0.8-plugins

But THAT is not an issue I get:
  Some packages could not be installed. This may mean that you have
  requested an impossible situation or if you are using the unstable
  distribution that some required packages have not yet been created
  or been moved out of Incoming.

So what now, plug-ins can't be installed and nor Google nor Ubuntu seems to 
have the solution. Any ideas??

---

### Post by Wolki on 2005-12-03
[QUOTE=CKCK]
But THAT is not an issue I get:
  Some packages could not be installed. This may mean that you have
  requested an impossible situation or if you are using the unstable
  distribution that some required packages have not yet been created
  or been moved out of Incoming.
[/QUOTE]

Do you have universe and multiverse enabled? Look here for how to do it: 
[https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)

---

### Post by CKCK on 2005-12-04
[QUOTE=Wolki]Do you have universe and multiverse enabled? Look here for how to do it: 
[https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)[/QUOTE]

Yes I followed the link (already did), but now I checked [COLOR="Red"]all[/COLOR] 
checkboxes for Ubuntu 5.10. Now all lib could be found, dependicies are solved
by downloading the needed files. Although the default player Totem did **not** recognize mp3 files.
So I tried:
1. sudo apt-get install mpg123   --> could not play mp3's
2. sudo apt-get install xmms    --> GREAT, worked, plays all you want!

Goodluck witch Ubuntu.

---

### Post by nemik on 2005-12-04
i think that is a HUGE deficiency in ubuntu. installing it, putting in an MP3 CD, and then on the first click not being able to play the most popular format is unacceptable. that really should be fixed.

---

### Post by bored2k on 2005-12-04
[QUOTE=CKCK]Yes I followed the link (already did), but now I checked [COLOR="Red"]all[/COLOR] 
checkboxes for Ubuntu 5.10. Now all lib could be found, dependicies are solved
by downloading the needed files. Although the default player Totem did **not** recognize mp3 files.
So I tried:
1. sudo apt-get install mpg123   --> could not play mp3's
2. sudo apt-get install xmms    --> GREAT, worked, plays all you want!

Goodluck witch Ubuntu.[/QUOTE]
Install mpg123-esd

---

### Post by bored2k on 2005-12-04
[QUOTE=nemik]i think that is a HUGE deficiency in ubuntu. installing it, putting in an MP3 CD, and then on the first click not being able to play the most popular format is unacceptable. that really should be fixed.[/QUOTE]
Ubuntu is a free distribution. Propietary codecs are bad and controversial juju. Ubuntu wants to stay free. Besides, even Windows knows this and doesnt include them by default-

---

### Post by aysiu on 2005-12-04
[QUOTE=nemik]i think that is a HUGE deficiency in ubuntu. installing it, putting in an MP3 CD, and then on the first click not being able to play the most popular format is unacceptable. that really should be fixed.[/QUOTE] No, it's not a deficiency. It's purposely done that way.

If you don't have the time/energy to manually install all the proprietary codecs you want, you should consider a couple of other options:

1. Mepis, Blag, or Linspire--these Linux distributions include a variety of proprietary codecs in them because they are not ideologically dedicated to supporting only free software out of the box.

2. [Automatix for Ubuntu](http://ubuntuforums.org/showthread.php?t=66563), which will do (almost like magic) a lot of the typical work needed for proprietary codecs and other popular application support options for you.

---

### Post by az on 2005-12-04
[QUOTE=nemik]i think that is a HUGE deficiency in ubuntu. installing it, putting in an MP3 CD, and then on the first click not being able to play the most popular format is unacceptable. that really should be fixed.[/QUOTE]

Did you pay the licence fees imposed by the owners of the mp3 codec?

---

### Post by Wolki on 2005-12-04
[QUOTE=CKCK]Although the default player Totem did **not** recognize mp3 files.[/quote]

This should not happen, my Totem plays mp3s perfectly. Maybe you need to execute "gst-register-0.8".

[QUOTE=aysiu]2. Automatix for Ubuntu, which will do (almost like magic) a lot of the typical work needed for proprietary codecs and other popular application support options for you.[/QUOTE]

There's also EasyUbuntu, which, while it doesn't do as much as Automatix and isn't as configurable, doesn't require setting a root password. It's pretty easy, too.

---

### Post by dschaller on 2005-12-04
I got totem to play mp3 just by installing the plugins for the gstreamer backend. Using Synaptic Package Manager, I installed the gstreamer0.8-plugins metapackage. If Synaptic can't find the package, then you might need to make sure it's looking at the correct repositories by checking /etc/apt/sources.list

---

