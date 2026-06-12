---
title: "Kubuntu took over my ubuntu"
date: 2007-07-20
forum: Desktop Environments
---

### Post by Chymera on 2007-07-20
The fact is i was tired of all the ppl saying kde sucks just because they never tried anything except gnome. So i decided to try out kdm on ubuntu. I installed all the stuff via 

>  sudo apt-get install kubuntu-desktop

shut the comp down and logged in with a kubuntu session. Long story short, KDE works smoother, my favourite music player of all time (amarok) works a lot better than in gnome (yes, i know its obvious since it was made for kde) and konqueror loads a lot faster than mozilla does in gnome. Still I find the KDM very "rusty" in apparence, and very user unfriendly in the way the panels are managed, its also jammed with a lot of options you never really use (or at least i would never use), and effects which get in the way and which are hard to disable. Its obvious that a lot more effort is being put into gnome than into kde.

So i decided that although kde has a lot of advantages i would still like gnome better. Now the tricky part. I have a lot of Kstuff that kame with the instalation of kubuntu-desktop and which i will have no use for in the future. I hoped that once i select the kubuntu desktop in synaptic for uninstall everything that came with it would go away with it. WRONG! 

Even worse than that, the loading screen was changed to Kubuntu, and the homepage of mozilla now has the Kubuntu logo on it, instead of plain old Ubuntu.

Is there any way that i can revert to the previous non-kubuntu setup without loosing kde applications i had installed previously (eg amarok) ore deletting any kde libraries which are vital to running apps like amarok under gnome?

---

### Post by maybeway36 on 2007-07-20
Just type:
```
sudo dpkg-reconfigure gdm
```
and choose "gdm" from the list.

---

### Post by iamhugeinjapan on 2007-07-20
The above will only replace the login window, not the whole environment.  Here is the site with very easy instructions to do what you want:

[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

edit: Unless you look through the command line list carefully, you will need to reinstall amarok and the required kde-libs, but hopefully they are cached in your apt cache so they wont have to redownload.

---

### Post by lunamystry on 2007-07-20
> **maybeway36 said:**
> Just type:
```
sudo dpkg-reconfigure gdm
```
and choose "gdm" from the list.

well i also wante to try KDE and installed it using the install kubuntu-desktop command, Now I cant play music or videos, any multimedia thing the window just goes gray and nothing happens. i used the command above but i still get kubuntu on my boot screen. 

I was tring to impress one of my female neighbourd with my linux PC when this happened by the way. :mad:

---

### Post by Chymera on 2007-07-21
Yep, i found that site on my own later last night, but was too tired to post myself. For anyone experiencing the same problem, look carefully through the list if you have stuff like amarok or kaffeine since it will erase EVERY kde thing you have on your machine including some xine codec stuff.

However if you want to try kubuntu; install it via "sudo aptitude" since you will be able to remove EXACTLY what you installed should you decide you wont have any use for kde afterwards :)

to lunamystry: i got a similar problem problem yesterday, but only when i logged into different sessions without rebooting (eg. login in gnome, logoff, login in kde - instead of login in gnome, reboot, login in kde)

---

### Post by maybeway36 on 2007-07-21
I suppose you could follow the steps on that link, then use aptitude to reinstall kubuntu. 
You'll have to compile and use usplash-switcher to get the ubuntu boot screen back:
[http://blogs.ubuntu-nl.org/dennis/2006/09/13/more-fun-with-usplash/]("http://blogs.ubuntu-nl.org/dennis/2006/09/13/more-fun-with-usplash/")
First install usplash-dev:
```
sudo apt-get install usplash-dev
```
Then compile the program:
```
gcc -o usplash-switcher usplash-switcher.c `pkg-config --libs --cflags gtk+-2.0` -lusplash
```
Then run it.
```
sudo ./usplash-switcher
```

---

### Post by Yellow Onion on 2007-08-05
```
apt-get remove kubuntu
apt-get autoremove 
```
mite be easier

[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

is terrible
it restores back to default ubuntu
removes basically ever package and then requires you to download them all again
prehaps you should look through the dependent of kubuntu-desktop and remove the one's you don't want

---

### Post by Happy_Man on 2007-08-05
@ OP

A-HEM....

I just noticed your statement: > Its obvious that a lot more effort is being put into gnome than into kde.

My good man, you couldn't be more wrong. KDE and GNOME are both being very actively developed. KDE may be even more so at this point due to the upcoming KDE 4 release. The reason they are both so different is due to their different philosophies. KDE aims to be as complete as possible and have every feature easily accessible, even if they might be useless to a lot of people. GNOME, on the other hand, aims to be powerful, while at the same time adhering to KISS. Thus, GNOME hides a lot of its more powerful features, things which KDE tries to make easily accessible. 

So, some people say KDE is too complicated, and other people say GNOME treats its users like idiots, and others say both of these things and use another desktop environment entirely! :p It's all a matter of personal preference. Take me, for example. I used to use GNOME, but eventually moved to KDE because it suited my needs better. So just use whatever fits best for you.

---

### Post by Yellow Onion on 2007-08-05
if that doesn't work try
```
sudo apt-get remove  adept arts hwdb-client-kde k3b kde-guidance kde-style-polyester kde-systemsettings kdenetwork-filesharing kdepasswd kdm keep kio-apt kio-locate kmplayer-konq-plugins konversation ksplash-engine-moodin ksystemlog ktorrent kubuntu-artwork-usplash kubuntu-default-settings language-selector-qt libqt-perl qca-tls software-properties-kde
sudo apt-get autoremove
```

*EDIT*
doesn't work yet sorry

---

