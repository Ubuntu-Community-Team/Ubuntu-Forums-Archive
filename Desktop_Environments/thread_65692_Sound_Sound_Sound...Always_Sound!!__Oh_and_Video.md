---
title: "Sound Sound Sound...Always Sound!!  Oh and Video"
date: 2005-09-14
forum: Desktop Environments
---

### Post by badboyz107 on 2005-09-14
Hey folks here is the problem I have most recently experienced.  

I have this computer set up with Ubuntu for my parents (not a good idea for 60 year olds...BUT free!)

They receive emails from people with .wmv movie attachments that they wish to watch.  Watching works fine but about half of the movies they watch dont have ANY sound.  The other half of them DO have sound.  What is the difference, because if they forward them to me on my XP box it works just peachy keen.  

**I HAVE VERY LIMITED KNOW HOW WITH UBUNTU**....so feel free to talk slowly to me and spell out any suggestions you have....THANKS!!!

 ](*,)

---

### Post by WillCooke on 2005-09-15
The chances are that the correct codecs aren't installed.

There's a howto @ [http://www.ubuntuguide.org/](http://www.ubuntuguide.org/)

---

### Post by juhis on 2005-09-15
Check-out also the xine-documentation:

[http://xinehq.de/index.php/faq](http://xinehq.de/index.php/faq)


juhis

---

### Post by badboyz107 on 2005-09-15
hummmm well I havent been using xine for this...its been defaulting to Totem however any player I use has the same results on the same files....ie if it doesnt have sound in totem neither do any other players....

The wierd part is that some files of the same format work just fine....I have installed the w32 codecs and all that good stuff tried again from the guide and this is what I got

root@ubuntu:/home/carrell # sudo apt-get install w32codecs
Reading package lists... Done
Building dependency tree... Done
w32codecs is already the newest version.
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  mozilla-firefox-gnome-support: Depends: firefox-gnome-support but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
root@ubuntu:/home/carrell #


WHAT does the unmet dependencies mean?????  and if I run it with -f install it gives the same message....however w32 is newest version????

---

