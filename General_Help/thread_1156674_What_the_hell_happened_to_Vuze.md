---
title: "What the hell happened to Vuze?"
date: 2009-05-12
forum: General Help
---

### Post by Maheriano on 2009-05-12
I updated to 9.04 and now when I run Vuze, there's no way to search for anything. It looks terrible now, what happened to the nice dashboard? How do I search for stuff? What the hell happened?

---

### Post by Maheriano on 2009-05-13
Nobody knows? I can't use this thing until I figure out what happened.

---

### Post by Maheriano on 2009-05-15
Seriously, nobody else uses Vuze? This is my screen, how do you download things with this? There is no section to search for torrents, I literally cannot figure out how to download anything.

[IMG]http://www.danmaher.com/images/Screenshot-Vuze.jpg[/IMG]

---

### Post by fung on 2009-05-18
If by "nice dashboard" you meant [http://cache1.vuze.com/cdnassets/4/1282b10b0cfaf8cad464de5b72da4471/img/home/main_screens.jpg](http://cache1.vuze.com/cdnassets/4/1282b10b0cfaf8cad464de5b72da4471/img/home/main_screens.jpg), I HATED that. anyway try going to tools -> options -> interface -> start -> display vuze UI chooser. change it to your ugly one and try restarting.

btw in this classic UI, you can click that folder icon on the top left to open torrents. and to filter or "search" your torrents just click in either your download or upload pane and start typing.

---

### Post by nayab on 2009-05-20
You guys are lucky. I went up to 9.04 and now Vuze does not work.:cry:

Removed it From Synaptic. Put it in again. Still no joy. Now I have to boot back to XP just to run Vuze.

---

### Post by ActiveFrost on 2009-05-20
With or without dashboard - since it's based on Java, my 9.04 can't handle it ( I barely can use my PC while downloading something ).
Conclusion - Transmission BitTorent client is one of the best apps on Ubuntu :D

---

### Post by SuperSonic4 on 2009-05-20
Deluge is my favourite client

---

### Post by Soul-Sing on 2009-05-20
Vuze is really over the top....

---

### Post by Maheriano on 2009-05-21
> **ActiveFrost said:**
> With or without dashboard - since it's based on Java, my 9.04 can't handle it ( I barely can use my PC while downloading something ).
Conclusion - Transmission BitTorent client is one of the best apps on Ubuntu :D

What do you mean by can't handle it? Could Java be to blame for it changing so much on me?

I haven't yet tried the solution posted above, haven't gotten a chance. I will.

---

### Post by SuperSonic4 on 2009-05-21
> **Maheriano said:**
> What do you mean by can't handle it? Could Java be to blame for it changing so much on me?

I haven't yet tried the solution posted above, haven't gotten a chance. I will.

Java is notorious for being a resource hog and usually with good reason. It could also be a change upstream which was sent to the repo

---

### Post by Mirge on 2009-05-21
KTorrent works fine for me..

---

### Post by Maheriano on 2009-05-21
> **fung said:**
> If by "nice dashboard" you meant [http://cache1.vuze.com/cdnassets/4/1282b10b0cfaf8cad464de5b72da4471/img/home/main_screens.jpg](http://cache1.vuze.com/cdnassets/4/1282b10b0cfaf8cad464de5b72da4471/img/home/main_screens.jpg), I HATED that. anyway try going to tools -> options -> interface -> start -> display vuze UI chooser. change it to your ugly one and try restarting.

btw in this classic UI, you can click that folder icon on the top left to open torrents. and to filter or "search" your torrents just click in either your download or upload pane and start typing.

This fixed it, thanks! I had to install the Sun JDK first though, it wouldn't run without it.

---

### Post by cdude on 2009-05-22
> **nayab said:**
> You guys are lucky. I went up to 9.04 and now Vuze does not work.:cry:

Removed it From Synaptic. Put it in again. Still no joy. Now I have to boot back to XP just to run Vuze.

try installing the getdeb package of [_Vuze_]("http://www.getdeb.net/app/Vuze")


As for "the nice" toolbar, did you guys try changing the appearance setting from within vuze? maybe it is set on classical look. I seem to remember such an option in azureus/vuze.

Personally, I prefer Transmission, the latest version is even nicer, go [www.getdeb.net](www.getdeb.net)
good luck

---

### Post by nayab on 2009-05-23
Thanks for that one cdude but I got to the bottom of it. I am new to Ubuntu as you can guess and I dual-boot with XP. So one day when I am trying to get into my 64 bit Ubuntu, I see a message telling me about the ability to upgrade from 8.04 to 9.10. I say yeah... go ahead.

It wiped out my Java and Flash.

Friend and I sat here and tried installing Vuze from Synaptic and it only allows version 3.x.

Only after updating the Java again did Vuze work. The Funky Vuze HD front end started working fully after Flash for 64 bit got installed.

Hope that helps other newbies out there.

Thank you Ubuntu Community for your patience with a moron like me.:D

---

### Post by jjosotoro on 2009-06-02
ok firts of all in the official ubuntu repositorys the vuze version is the 3.0 and not the last one 4.2.0.2; you can solve your issue this way.

add the getdeb repository to your source list using the terminal

echo "deb [http://getdeb.masio.com.mx/](http://getdeb.masio.com.mx/) jaunty/" | sudo tee -a /etc/apt/sources.list.d/getdeb.list && sudo apt-get update

now if that gives an gpg error like this:

W: GPG error: [http://getdeb.masio.com.mx/](http://getdeb.masio.com.mx/) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY B152F042D246C25D

you must use the following command in the terminal:

gpg --keyserver hkp://subkeys.pgp.net --recv-keys "XXXXXXXXXX"
sudo gpg --export --armor "XXXXXXXXXX" | sudo apt-key add -
sudo apt-get update

replacing the "XXXXXXXXXX" whit the number that appears in the message ex: B152F042D246C25D

$sudo apt-get update

just to check about the gpg error (it shouldnt appear anymore)

$sudo apt-get install vuze

this will install the version of vuze that is on getdeb (4.2.0.2) whit all dependencies, or you can install it using synaptics.
this version has the very nice vuze ui you are asking for and its more configurable.
$sudo chmod -R 777 /usr/share/vuze

this will let vuze to do any upgrade

---

