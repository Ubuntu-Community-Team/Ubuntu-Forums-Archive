---
title: "Ubuntu n00b here - no desktop when booting"
date: 2006-07-11
forum: Desktop Environments
---

### Post by mattyc on 2006-07-11
After much muckin around with windows i decided to give linux a try as an option for my webserver as i had just lost windows due to some great microsoft patches.. 

I install ubuntu as a once cd install and all goes well i think. until i boot it and log in and it takes me to command prompti know a small amount of linux commands, only really ifconfig and listing directory contents. 

Ive had redhat before and it booted straight to Gnome.. Is there something im missing, i have searched the forums but cannot find results that apply to me. please help 

Cheers

---

### Post by mattyc on 2006-07-11
im a goober

found this elsewhere

sudo apt-get install ubuntu-desktop

and it looks like it might be going, its installing all this stuff ansd asked for the cd, now its dling from http so fingers crossed !@!

---

### Post by T700 on 2006-07-11
The default server install does not load a GUI.  Use these commands to load one: ```
sudo aptitude update
``` and ```
sudo aptitude install ubuntu-desktop
``` 

I'd strongly suggest using aptitude instead of apt.  Aptitude is much cleaner if you ever have to uninstall.

Paul

---

### Post by kinematic on 2006-07-11
i wonder to how many n00bs that's happened....

---

### Post by mattyc on 2006-07-11
ok i did the install bit... and whala it boots into x desk i think it is, anyway i have no icons on the desktop and no options available to me, the other thing is in setup it didnt ask me to specify a password for root. .. so im logging in as a non administrative user... im wondering if thats why i have nothing on me desktop
... its all a wee bit tricky really, didnt expect this much hicups as a friend recommended it as a easy version to drive:(

---

### Post by cptnapalm on 2006-07-11
Ubuntu doesn't really have a root user, per se.  What it does is to asign the ability to use "sudo" to execute things as root.  So when it asks for the password, just enter your own.

The regular desktop version is very easy to use, in my opinion.  I have no idea what the server version defaults to.

Anything happen if you right-click on the desktop?

When you log in your user, there should be something that says "Session".  Click that and choose Gnome.  *Probably* the installation of ubuntu-desktop included that.

---

### Post by T700 on 2006-07-11
> **mattyc said:**
> ... its all a wee bit tricky really, didnt expect this much hicups as a friend recommended it as a easy version to drive:(

The server install is for experienced users.  Unlike Windows, Linux servers seldom have a GUI.  Why not blow away this install, download the desktop version, and install that?  Play around for a few weeks and get used to it, while at the same time, reading about Linux servers.

Paul

---

### Post by mattyc on 2006-07-11
all i wanna do with it is host a phpbb forum and coppermine gallery on webserver..aand a mailserver. will desktop version do that ? 

otherwise i might just go to another flavour cause time is very critical, the site has to be moved from where it is andd i gotta move it to my house, i was running it on windows 2k3 server, but as its not a legit version i have issues with updates, and therefore security

---

