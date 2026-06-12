---
title: "Flash Player"
date: 2009-03-08
forum: General Help
---

### Post by Vrekk on 2009-03-08
Hi
I cant get my Flash Player to work in Firefox.  I have downloaded and install the .deb package right from there site, but it dosnt seen to be working.  Can anyone help?

---

### Post by Chandler258 on 2009-03-08
Ok, this may sound silly. Go into Preferences > Main > Manage Add-ons  and check if it is enabled.

More info about your FireFox installed and enabled plugins can be found if you type about:plugins (about[colon]plugins  ... damn emotes =)) in your address bar. Look there if flash plugin is enabled and associated with certain file types.

One reason for not working, could be that you have mutiple flash players installed on your system, like Gnash or Swfdec. 

Anyhow, check first two options and report back =)

---

### Post by zika on 2009-03-08
if You are on 64-bit machine with 64-bit OS, You might want to try something like:```
sudo apt-get --purge remove flashplugin-nonfree nspluginwrapper
wget http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.22.87.linux-x86_64.so.tar.gz
tar xvf libflashplayer-10.0.22.87.linux-x86_64.so.tar.gz
(create a directory /opt/flash so You can keep it up-to-date)
sudo mv libflashplayer.so /opt/flash/libflashplayer.so
(now we will create links in two directories to the file above)
sudo ln -s /opt/flash/libflashplayer.so /home/Your_username/.mozilla/plugins/
(You might have to create this directory)
sudo ln -s /opt/flash/libflashplayer.so /usr/lib/mozilla/plugins
```adapted to Kubuntu (I am not too familiar with it). before You try that, do```
sudo updatedb
locate libflashplplayer.so
``` so we could see if the above is really needed.
[COLOR=Red]**please be careful, this was checked numerous times but ... it is Your machine ...**[/COLOR] ;)

---

### Post by Vrekk on 2009-03-08
Ok when I go to that menu there isnt an Adobe Flash Player thats there, but there is a shockwave flash player that was disabled.  Now that isnt enabled flash works but VERY slowly.  How do I remove the shockwave one to have the adobe one work?

---

### Post by steveneddy on 2009-03-08
> **Vrekk said:**
>  How do I remove the shockwave one to have the adobe one work?

:-k

---

### Post by perlluver on 2009-03-08
Adobe and Shockwave are the same thing, last time I checked.  Unless you mean something else?  Yes indeed, Shockwave Flash, Adobe Flash Player, under about plugins, one in the same.

---

### Post by Vrekk on 2009-03-08
Well then how can i make it run faster, any thing that uses flash runs very slow and is almost un-useable.

---

