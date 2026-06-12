---
title: "can install firefox"
date: 2005-10-08
forum: Desktop Environments
---

### Post by marcelofabiani on 2005-10-08
Hi I'm new to linux, I trying to install firefox and the following error shows:
I've login as user
./firefox-installer
firefox-installer-bin:error while loading shared libraries:libgtk-x11-2-0.so.0:cannot open shared object file:no such file or directory

Please help me and if you can send me a link to a tutorial for installing this:confused:

---

### Post by codejunkie on 2005-10-08
[QUOTE=marcelofabiani]Hi I'm new to linux, I trying to install firefox and the following error shows:
I've login as user
./firefox-installer
firefox-installer-bin:error while loading shared libraries:libgtk-x11-2-0.so.0:cannot open shared object file:no such file or directory

Please help me and if you can send me a link to a tutorial for installing this:confused:[/QUOTE]
the easiest way to install firefox is open a terminal and ```
sudo apt-get update
``` ```
sudo apt-get install firefox
```

---

### Post by marcelofabiani on 2005-10-08
[QUOTE=codejunkie]the easiest way to install firefox is open a terminal and ```
sudo apt-get update
``` ```
sudo apt-get install firefox
```[/QUOTE]

Reading package lists...Done
Building dependency tree....Done
E: Couldn't find package firefox

I also try this changing to the directory where I unzipped
Please help

---

### Post by mlomker on 2005-10-08
> I also try this changing to the directory where I unzipped
Please help

Have you added in all of the repositories?  Follow [this guide]("http://www.ubuntuguide.org/#extrarepositories") but skip the two for 'backports' since they aren't in use anymore.

---

### Post by Gezzer on 2005-10-08
create a folder on the /home partition and name it Firefox
move the firefox-installer folder to this new folder

then open the installer and try the install of firefox ...

---

### Post by bhagabhi on 2005-10-08
That apt-get command line should be:

sudo apt-get install mozilla-firefox

if you want to do it that way. I don't think its enough with "firefox" - it isn't on my system anyway. You might have to add some repositories though, not sure.

---

### Post by mlomker on 2005-10-08
> its enough with "firefox" - it isn't on my system anyway. You might have to add some repositories though, not sure.

There are actually two packages, mozilla-firefox and firefox.  They are in different repositories.  It looks like the mozilla-firefox is newer.

---

